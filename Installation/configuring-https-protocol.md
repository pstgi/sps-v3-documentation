# Configuring HTTPS protocol for SPS v3

This section describes the configuration process for installing an SSL certificate for SPS v3
and setting up the HTTPS protocol to use for accessing the frontend (Web app) and backend (API) of 
the app. Optionally, you will remove the HTTP protocol from the frontend and backend to improve 
security.

## Prerequisites

To configure an SSL certificate for SPS v3, you need:
- an SSL certificate installed on your web server, for the domain name you will use,
- SPS v3 installed and running on your IIS server,
- administrative privileges on the server,
- domain name pointing to your server's IP address,
- text editor such as Notepad.

You can obtain an SSL certificate from a trusted Certificate Authority (CA).

## Configuring both frontend and backend to use HTTPS protocol

You will need to configure both the frontend and backend of SPS v3 to use HTTPS.

### Binding the SSL certificate to the frontend

1. Open the IIS Manager on your server.
1. Select the frontend site (usually named "SPS v3 - Web App") from the list of sites.
1. Click on "Bindings" in the right-hand Actions pane.
1. On the Site Bindings window, click "Add...".
1. On the Add Site Binding window, select "https" as the Type.
1. Verify that the Port is set to 443 (recommended) or to the one you want to use for HTTPS.
1. Enter the Host name (domain name or subdomain) for your SPS v3 frontend.
1. Select the SSL certificate you installed from the "SSL certificate" dropdown.
1. You can click "View..." to verify the certificate is the one you want to use.
1. Click "OK" to add the binding.
1. Optionally, you can remove the HTTP binding by selecting it and clicking "Remove".

With these steps, you have configured the frontend of SPS v3 to use HTTPS protocol.

### Binding the SSL certificate to the backend

Because of the architecture of SPS v3, the backend is typically a separate site in IIS. 
Therefore, the existing installation could have been configured to:

**Option A** - use one domain name for both frontend and backend, and a different port (usually 80 and 44301, respectively), or

**Option B** - use different domain name or subdomain with the same port for both frontend and backend.

In both options, the process of binding the SSL certificate to the backend is similar to the frontend
binding.

1. Open the IIS Manager on your server.
1. Select the backend site (usually named "SPS v3 - API") from the list of sites.
1. Click on "Bindings" in the right-hand Actions pane.
1. On the Site Bindings window, click "Add...".
1. On the Add Site Binding window, select "https" as the Type.
1. Verify that the Port is set to 443 (recommended) or to the one you want to use for HTTPS.
1. Enter the Host name (domain name or subdomain) for your SPS v3 backend.
1. Select the SSL certificate you installed from the "SSL certificate" dropdown.
1. You can click "View..." to verify the certificate is the one you want to use.
1. Click "OK" to add the binding.
1. Optionally, you can remove the HTTP binding by selecting it and clicking "Remove".

> Ensure that the ports used in the new bindings are open in the firewall rules.
Close any ports that are not used by the application or another website or app anymore to improve 
security.

## Modifying the configuration files

After binding the SSL certificate to both frontend and backend, you need to modify the 
configuration files of SPS v3 to ensure that the application uses HTTPS protocol for all requests.

Two files contain references to the domain names and protocols used by the application:
- *./appsettings.json*
- *./wwwroot/dist/assets/appconfig.json*

> When you modify the configuration files, stop the frontend and the backend sites in IIS.
Start them only after you finish modifying the files and copy them to the proper locations.

Also, consider the existing backups of these files, usually located in a folder names 
*App Settings Backup* or *SPS v3 Backup*. You can modify the files there and then copy them to the 
correct location. These copies will have to be modified as well for future updates of the application.

### Modifying the appsettings.json file

1. Create a backup copy of the file before making any changes.
1. Ensure you have write permissions to the location you will edit the file in or copy it to your Desktop.
1. Open the *./wwwroot/dist/assets/appconfig.json* file in a text editor.
1. Modify the values to use the HTTPS protocol and the correct domain name or subdomain, as follows:

- `App > ServerRootAddress` - points at the backend URL
- `App > ClientRootAddress` - points at the frontend URL
- `App > CorsOrigins` - points at the frontend URL
- `IdentityServer > Authority` - points at the backend URL
- `HealthChecks > HealthChecksUI > HealthChecks > Uri` - points at the backend URL, ends with the folder `/health`

5. Save the changes to the file.
1. Copy it over the existing file in the *./appsettings.json* folder of the backend application.

### Modifying the appconfig.json file

The appconfig.json file is located in a subfolder of the frontend application. 

1. Create a backup copy of the file before making any changes.
1. Ensure you have write permissions to the location you will edit the file in or copy it to your Desktop.
1. Open the *./wwwroot/dist/assets/appconfig.json* file in a text editor.
1. Modify the values of `remoteServiceBaseUrl` for the backend and `appBaseUrl` for the frontend
   to use the HTTPS protocol and the correct domain name or subdomain. 
   
For example:
   ```json
   "remoteServiceBaseUrl": "https://your-domain-api.com",
   "appBaseUrl": "https://your-domain.com"
   ```

Or, when using a non-standard port:
   ```json
   "remoteServiceBaseUrl": "https://your-domain-api.com:44301",
   "appBaseUrl": "https://your-domain.com:443"
   ```
5. Save the changes to the file.
1. Copy it over the existing file in the *./wwwroot/dist/assets/* folder of the frontend application.

These should be all the changes you need to make to configure the HTTPS protocol for SPS v3. 
Navigate to the frontend in our browser and verify that the application is accessible via HTTPS.

___

[Home](../README.md)

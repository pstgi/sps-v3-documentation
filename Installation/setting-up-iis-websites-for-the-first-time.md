# Setting up IIS websites for the first time

The following are instructions on how to setup IIS for a new instance of the SPS Plus application on
a new server. Please do not proceed with these steps if you did not complete the previous section,
Preparing the web server of this document. If you already have SPS Plus installed on your server,
you do not need to perform any of these steps.

## Create two websites in IIS

The application has a front-end and a back-end component. Each needs a separate website in IIS.

> These instructions demonstrate the configuration of SPS Plus for using it with the HTTP protocol. 
You can configure the HTTPS protocol during this process, by providing an SSL certificate already 
be installed on the server. You can configure the HTTPS while following these instructions or at a
later time by checking [Configuring HTTPS protocol for SPS Plus](./configuring-https-protocol.md).

### Create an IIS website for API component

> We suggest setting up the website files on the secondary drive of the server. This will allow
you to have more space for the application files and logs, prevent the primary drive from filling up,
and allow easier upgrade of the operating system.

Create a new folder SPS Plus - API under your root IIS folder (usually D:\inetpub\wwwroot\SPS Plus).
This will be the destination root folder of the SPS Plus application.

Open IIS Manager, in the tree on the left, right-click Sites, then choose Add Website. In the modal
popup, enter:
- Site name: *SPS Plus - API*
- Physical path: *browse to the destination root folder you have created*
- Port: *44301* \*
- Start website immediately: *unchecked*

Leave the rest of the fields with their default values and click OK.

If you will be using only a specific URL, set it in the Host name field. This will allow you to
access the API server using a specific URL and change the port as needed.

---
\* Port 44301 is required by the front-end component to connect to the API server application. 
If you need to change it, please contact PSTGI support for assistance on how to setup the proper
connectivity. Alternatively, you can use the same port as the front-end application, but you will
need a different Host name for the API server.

![file](./pictures/installation-web-site-1.jpg "Setup API website")

#### Set application pool parameters (recommended)

In IIS Manager, find the Application Pool with the same name as the API website - usually
SPS Plus - API. It is located in the tree on the left under Application Pools. Right-click on it
and choose Advanced Settings. In the modal popup, change the following settings from their
default values:

- **.NET CLR Version**: *No Managed Code* — optional, but recommended as the app does not rely on
loading the desktop CLR (.NET CLR).
- **Start-up Time Limit (seconds)** (under Process Model): *300* — the back-end application may
need more than the default 90 seconds to initialize, especially on a busy server.
- **Shutdown Time Limit (seconds)** (under Process Model): *300* — gives the application more time
to finish its work in progress when it is stopped or recycled.
- **Regular Time Interval (minutes)** (under Recycling): *0* — disables the default recycle that
occurs every 29 hours at unpredictable times.

> Avoid scheduling recycles under **Specific Times** (Recycling section). A recycle terminates any
long-running background process (data imports, scenario calculations) that happens to be running at
that moment. The application does not need periodic recycling to stay healthy.

![file](./pictures/installation-app-pool-parameters.jpg "App Pool parameters")

With the default IIS behavior, the application is started when the first request arrives and is
stopped again after 20 minutes without visitors. This preserves energy and memory on the server,
but the first user after a server restart or a period of inactivity has to wait for the full
application startup, which may take a long time. If you prefer the application to always respond
immediately, follow the optional instructions in
[Keeping the API application always running](./keeping-the-api-application-always-running.md).

### Create a website for the front-end application

Before you begin, we suggest stopping or removing the Default Web Site from your IIS. This will
allow you to use default port 80 to access the SPS Plus front-end application. If you cannot do that,
we suggest setting port 4200 for the front-end application.

In *IIS Manager*, right-click *Sites*, then choose *Add Website*. In the modal popup, enter:
- Site name: *SPS Plus - Web App*
- Physical path: *{destination_root_folder}\wwwroot\dist*
- Port: *80*
- Start website immediately: *unchecked*

If you will be using only a specific URL, set it in the Host name field. This will allow you to
access the API server using a specific URL.

Leave the rest of the fields with their default values and click OK.

![file](./pictures/installation-web-site-2.jpg "Setup Web App website")
 
At this point, you will have the two websites setup properly.

## Firewall setup

Add inbound exception in the firewall of the server for TCP port 44301, where the API server is
accessed. To do so, open Windows Defender Firewall and Advanced Security from Windows and add an
Inbound Rule. Name it *PSTGI SPS Plus API server* for easy recognition. Allow traffic to the types of
networks you intend to use SPS Plus on.

These are all the steps needed to be configured on the server for SPS Plus to work properly.

___

[Home](../README.md) / Next: [Setting up the network share](./setting-up-network-share.md)

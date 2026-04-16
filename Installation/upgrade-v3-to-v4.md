# Upgrading SPS v3 to v4

When upgrading from SPS v3 to v4, you need to:

- install the latest .NET 9.0 runtimes on the server where SPS is hosted,
- obtain a copy of the distribution package of SPS v4 from the PSTGI team,
- make changes to your appsettings.json file,
- replace the existing SPS v3 files with the new ones from the distribution package of SPS v4,
- copy the App Settings Backup to the website folder.

## Installing .NET 9.0 runtimes

You need to install the latest .NET 9.0.x runtimes on the server where SPS is hosted.

To verify if you already have the required runtimes installed, run the following command in a terminal:
```bash
dotnet --list-runtimes
```
In the list, you need to see a line similar to the following:
```
Microsoft.AspNetCore.App 9.0.xx [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
```

It is safe to download and install the latest runtimes again, even if you already have them installed. 
The installer will detect the existing runtimes and will only install the missing ones, if any.

You can download the runtimes from the official .NET website: https://dotnet.microsoft.com/en-us/download/dotnet/9.0

## Obtain a copy of the distribution package of SPS v4

You need to contact the PSTGI team to obtain a copy of the distribution package of SPS v4. 
You cannot download it from a public website, unless you were instructed to do so by the PSTGI team.

Do not continue with the upgrade process until you have the distribution package of SPS v4.

## Changes to appsettings.json

If you have obtained the distribution package of SPS v4, first do so and then continue with this process.

First, locate the backup copy of the appsettings.json file that you created before starting the upgrade process. 
It is usually in a folder named *App Settings Backup* in the same directory on a harddrive of the web server.

Then, make a copy for backup. Name it appsettings-v3.json and save it in the same folder as the original
appsettings.json file.

> If the upgrade process completes and the app runs, you will not need it and we suggest deleting it from
  any backups you have.

Once you make a backup copy, open the original appsettings.json file in a text editor and make the following changes to it.

### Add `IsCloudHosted` setting

Locate `BackgroundJobs` node under `App` and add `IsCloudHosted` as seen below. 
Set its value to `false` if you are hosting SPS on-premise. Otherwise, set its value to `true` if you are hosting SPS in the cloud.

```json
    "App": {
    ...
        "BackgroundJobs": {
          "DoNotRun": false
        },
        "IsCloudHosted": true
    }
```

> This setting specifies if your server time-zone is set to UTC (use `true`) or local time (use `false`).

**IMPORTANT!**

If you have your database served from a cloud hosting and have set `IsCloudHosted` to `true`, run script 
*SPS v4 - Convert EST to UTC - All Tables.sql* against the database. You can obtain this file from the PSTGI team as part
of the distribution package of SPS v4. Same applies if you are moving your database from on-premise SQL server to the cloud.
Run the script after you restore it to the cloud MS SQL server.

### Replace the following sections

There are a few sections in your existing file that you need to replace by removing the node marked as "Existing"
and adding the one marked as "New" below. Some of the values you already have in your existing file may have very
small differences from the "Existing" ones shown below. You still need to replace them with the "New" ones.

#### Existing

```json
    "Twitter": {
      "IsEnabled": "false",
      "ApiKey": "",
      "ApiKeySecret": ""
    },
```

#### New

```json
    "Twitter": {
      "IsEnabled": "false",
      "ConsumerKey": "",
      "ConsumerSecret": ""
    },
```

Replace the following section of appsettings.json:

#### Existing

```json
  "IdentityServer": {
    "IsEnabled": "false",
    "Authority": "https://xxx.yyy.zzz/",
    "ApiName": "default-api",
    "ApiSecret": "secret",
    "Clients": [
      {
        "ClientId": "client",
        "AllowedGrantTypes": [
          "password"
        ],
        "ClientSecrets": [
          {
            "Value": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
          }
        ],
        "AllowedScopes": [
          "default-api"
        ]
      },
```

#### New

```json
  "OpenIddict": {
    "IsEnabled": "false",
    "Applications": [
      {
        "ClientId": "client",
        "ClientSecret": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
        "DisplayName": "PSTGI_App",
        "ConsentType": "Explicit",
        "RedirectUris": [
          "https://oauthdebugger.com/debug"
        ],
        "PostLogoutRedirectUris": [],
        "Scopes": [
          "default-api",
          "profile"
        ],
        "Permissions": [
          "ept:token",
          "ept:authorization",
          "gt:password",
          "gt:client_credentials",
          "gt:authorization_code",
          "rst:code",
          "rst:code id_token"
        ]
      }
    ]
  },
```

Replace the following section of appsettings.json:

#### Existing

```json
  "EvaluationTimeOnSeconds": 10,
```

#### New

```json
  "EvaluationTimeInSeconds": 10,
```

### Increase the size of the JWT key

In the appsettings.json file, locate the `JwtBearer` node:

```json
    "JwtBearer": {
      "IsEnabled": "true",
      "SecurityKey": "PSTGI_XYZ123XYZ123D55",
      "Issuer": "PSTGI",
      "Audience": "PSTGI"
    }
```

You need to replace the value of `SecurityKey` with a string that is at least 32 characters long.
You can generate it by running the following PowerShell command in a terminal:

```powershell
-join ((48..57)+(65..90) | Get-Random -Count 32 | ForEach-Object {[char]$_})
```

If you need stronger security key, you can increase the number 32 in the command above to 64.

## Upgrading the app

After you have made the necessary changes to the appsettings.json file, you can proceed with upgrading the app files.
To upgrade the app, follow the standard instructions [Updating the SPS Plus application](./updating-the-sps-plus-application.md)
in this documentation.

This concludes the whole process of upgrading from SPS v3 to v4. You do not need to do any changes 
to the hosting server, IIS, or the database, except for the changes to the appsettings.json file described above.

___

[Home](../README.md) / Next: [Updating the SPS Plus application](./updating-the-sps-plus-application.md)

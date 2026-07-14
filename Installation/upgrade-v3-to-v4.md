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

You can download the download the latest release of [ASP.NET Core Runtimes 9 Hosting Bundles] from the official .NET website:
[https://dotnet.microsoft.com/en-us/download/dotnet/9.0](https://dotnet.microsoft.com/en-us/download/dotnet/9.0).

## Obtain a copy of the distribution package of SPS v4

You need to contact the PSTGI team to obtain a copy of the distribution package of SPS v4. 
You cannot download it from a public website, unless you were instructed to do so by the PSTGI team.

> Do not continue with the upgrade process until you have the distribution package of SPS v4.

> You have to update the appsettings.json file before you can upgrade the app files. Use the internal
  "SPS v3 to v4 Settings Upgrader"

## Upgrading the app

After you have made the necessary changes to the appsettings.json file and you ensured your web server prerequisites are met,
you can proceed with upgrading the app files.

To upgrade the app, follow the standard instructions [Updating the SPS Plus application](./updating-the-sps-plus-application.md)
in this documentation.

This concludes the whole process of upgrading from SPS v3 to v4. You do not need to do any changes 
to the hosting server, IIS, or the database, except for the changes to the appsettings.json file described above.

___

[Home](../README.md) / Next: [Updating the SPS Plus application](./updating-the-sps-plus-application.md)

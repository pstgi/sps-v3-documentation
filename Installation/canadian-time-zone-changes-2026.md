# Canadian time zone changes (November 2026)

This page describes what school districts in British Columbia, Alberta and Manitoba need to do so that
SPS+ shows the correct time after the November 2026 time zone change. 

## What changed

On 1 November 2026, British Columbia, Alberta and Manitoba did not set their clocks back one hour.
They now keep the same offset all year. Microsoft added a new Windows time zone for each province:

| Province         | Offset all year | New Windows time zone          | Previous Windows time zone |
|------------------|-----------------|--------------------------------|----------------------------|
| British Columbia | UTC-07:00       | British Columbia Standard Time | Pacific Standard Time      |
| Alberta          | UTC-06:00       | Alberta Standard Time          | Mountain Standard Time     |
| Manitoba         | UTC-05:00       | Manitoba Standard Time         | Central Standard Time      |

The previous time zones keep the old rules: they move back one hour in November and forward one hour
in March. A server or computer that stays on a previous time zone shows a time one hour behind from
November to March.

> If your district is in an area that did not follow the provincial time before the change (for
example, parts of eastern British Columbia), confirm the correct time zone with PSTGI's Customer
Support before you change anything.

## Who needs to act

- **SPS+ installed on your district's servers:** your IT team completes the steps in
  [Steps for SPS+ installed on your servers](#steps-for-sps-installed-on-your-servers).
- **SPS+ hosted by PSTGI:** PSTGI updates the servers and the SPS+ settings for you. Your IT team only
  needs to complete [Users' computers](#users-computers).
- **School districts in other provinces:** no action is needed.

## Before you start

- Plan a short maintenance window. The servers and the SPS+ websites are restarted, and SPS+ is not
  available during the restart.
- You need administrator access to the web server that runs SPS+ and to the SQL Server that holds the
  SPS+ database.
- Request SPS+ version 4.1.12 or newer from PSTGI's Customer Support, if you do not already have it.

## Steps for SPS+ installed on your servers

Complete steps 1 to 3 on both the web server and the SQL Server, unless the step says otherwise.

### Step 1. Install the Windows time zone update

Install the latest Windows updates. If you manage updates centrally (for example, with WSUS), make
sure the update that adds the new Canadian time zones is approved for these servers.

To check that the update is installed, run the following in PowerShell:

```powershell
Get-TimeZone -ListAvailable |
    Where-Object Id -in 'British Columbia Standard Time', 'Alberta Standard Time', 'Manitoba Standard Time' |
    Format-Table Id, DisplayName
```

All three time zones should be listed. If they are not, the update is not installed yet. Do not
continue until it is.

### Step 2. Set the server time zone

SPS+ installed on your servers uses the local time of the servers, so both servers must use the new
time zone for your province. Run the line for your province in PowerShell as an administrator:

```powershell
Set-TimeZone -Id 'British Columbia Standard Time'   # British Columbia
Set-TimeZone -Id 'Alberta Standard Time'            # Alberta
Set-TimeZone -Id 'Manitoba Standard Time'           # Manitoba
```

You can also change it in **Settings > Time & language > Date & time > Time zone**.

To check the result, run:

```powershell
Get-TimeZone | Format-Table Id, DisplayName
[TimeZoneInfo]::Local.GetUtcOffset([datetime]'2027-01-15')
```

The first line should show the new time zone. The second line should show `-07:00:00` in British
Columbia, `-06:00:00` in Alberta and `-05:00:00` in Manitoba.

### Step 3. Install SPS+ version 4.1.12 or newer

On the web server only, install SPS+ version 4.1.12 or newer by following
[Updating the SPS+ application](./updating-the-sps-plus-application.md).

### Step 4. Restart

Restart the SQL Server and then the web server. SPS+ reads the time zone information only when it
starts, so it does not pick up the changes until it is restarted.

If you cannot restart the servers, restart at least the SQL Server service and then the two IIS
websites *SPS Plus - API* and *SPS Plus - Web App*.

### Step 5. Check the result

- The clock on both servers shows the correct local time.
- Open SPS+ and test the functionality you usually use.
- The latest entries in the log files in the *\App_Data\Logs* folder of the SPS+ installation show the
  correct local time.

If something does not look right, contact PSTGI's Customer Support.

## Users' computers

Install the latest operating system updates on the computers your staff use to work with SPS+, and make
sure they use the new time zone for your province. On Windows, check
**Settings > Time & language > Date & time > Time zone**. Computers that are not updated show a time
one hour behind from November to March.

## Times recorded before the change

SPS+ installed on your servers records times in the local time of the servers. Times recorded between
1 November 2026 and the completion of the steps above may be one hour earlier than the actual time,
because the servers were still using the previous time zone. SPS+ does not correct these times. If
this matters for your district, contact PSTGI's Customer Support.

## Troubleshooting

When a school district in British Columbia, Alberta or Manitoba reports times that are one hour off:

1. Confirm the province and whether SPS+ is installed on the district's servers or hosted by PSTGI.
2. **Hosted by PSTGI:** escalate to the PSTGI team, who update the servers and the SPS+ settings.
3. **Installed on the district's servers:** confirm that the district completed steps 1 to 5 and is
   on SPS+ version 4.1.12 or newer. Ask for the output of the PowerShell checks in steps 1 and 2 from
   both servers.

| Symptom                                                     | Likely cause                                        | Fix                  |
|-------------------------------------------------------------|-----------------------------------------------------|----------------------|
| Times are one hour behind since 1 November 2026             | The servers still use the previous time zone        | Steps 1, 2 and 4     |
| The new time zones are not listed by the check in step 1    | The Windows update is not installed or not approved | Step 1               |
| Times are still wrong after the time zone was changed       | The servers or the SPS+ websites were not restarted | Step 4               |
| Times are correct on the server but wrong on a user's computer | The user's computer is not updated               | Users' computers     |

___

[Home](../README.md)

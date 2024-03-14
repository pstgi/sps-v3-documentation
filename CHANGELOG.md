# SPS Plus 3 Change Log

These are the changes to each version that has been released in this project

## ver.3.3.1 (2024-03-14)

- Fix issue with not saving scenario updates because of trigger messages as raised errors.
- Removed password transfer from v3 to v1.
- Fix misaligned panels on Sync page.

## ver.3.3.0 (2024-03-13)

- Added check for validity of a School Locator batch before activating it.
- Resets cache after activating a School Locator batch.
- Added feature to download new addresses from Master repository on the Cloud.
- Added more sortable columns to Scenarios page.
- Export of schools as Shape file.
- UI improvements and cleanup.

## ver.3.2.5 (2024-02-28)

- Added notification for bad Study Area polygons.
- Fixed totals for Progression Factors historic averages.
- Added coordinate system selection for exporting geometry data.

## ver.3.2.4 (2024-02-26)

- Fixed spinner on Sync Database page.

## ver.3.2.3 (2024-02-26)

- Added forced browser refresh when new version is deployed.
- Added filter for schools when program boundaries are filtered.
- Fixed map centering when no program boundaries or study areas.

## ver.3.2.2 (2024-02-21)

- Fixed issue with missing parameters in some API calls.

## ver.3.2.1 (2024-02-21)

- Fixed issue with permissions to write temporary files on some systems.
- Added exporting of GeoJSON and Shape files with different projections.

## ver.3.2.0 (2024-02-21)

- Added School Program boundary map.
- Optimize performance of some pages that contain multiple selectors.
- UI improvemements.

## ver.3.1.0 (2024-02-08)

- Enrolment Projections - main release.
- Many performance optimizations.
- Many bug fixes.

## ver.3.0.16 (2024-01-16)

- Added bulk delete for school Holding.
- Updated schema of tblGisMasterAddressExtended table.
- Added persistence for Program Type and other selection within Enrolment Projections.
- Optimized number of API calls in many pages.
- Added "Select All" to School Configuration Holding grid.
- Fixed dislaying Back button for the same school.
- Fixed chart not reloading when school is changed.
- Fixed many minor bugs.

## ver.3.0.15 (2024-01-02)

- Changed data schema in GisMasterAddressExtended table.

## ver.3.0.14 (2023-12-13)

- Fixed filters for some dropdowns not working properly.
- Removed permission for My SPS page - now accessible to all.
- Expanded Program Type dropdown to display code and name.

## ver.3.0.13 (2023-12-04)

- Fixed batch information panel for some edge cases.
- Added Program Type aliases to syncing to cloud.
- Added ability to copy school assignment overrides from one year to another.

## ver.3.0.12 (2023-11-23)

- Combined all related notes in School Configuration Projections grid.
- Fixed impossible save of deleted note for scenario 0.
- Fixed missing grid when calculating EP > Progression Factors.
- Fixed failure because of unique key constraint in EP > Add holding rules.
- Properly filter school programs for feeder school analysis.
- Continue checking for a running background job even after database timeout.
- Added ability to enter decimal number starting with a dot in grids.
- Added tooltip to Projections chart.
- Allow closing of Yield Template modal with no changes.
- Other UI improvements.

## ver.3.0.11 (2023-11-08)

- Fix filter on schools dropdown in Enrolment Projections.
- Sorted school list in Overrides.
- Added separate symbols for different Study Area meanings.
- Shows all fields on the Update Message modal.
- Added links opening the school locator for the active or latest batch.

## ver.3.0.10 (2023-10-31)
- Added missing fields from School Overrides into the Sync-to-cloud data.
- Removed ability to edit School Overrides for years that are not in the current and next year's scenarios.
- Changed Study Area reference from School Overrides to a single id.
- Allowed adding new School Override from the Notice messages page.
- Added mandatory Notice message to every School Override.
- Extended size of Development Plan Comment and Description fields to 1000 characters.
- Added more information when editing notice messages.

## ver.3.0.9 (2023-10-11)

- Fixed issues with some fields not being synced properly to cloud School Locator database.

## ver.3.0.6 (2023-10-02)

- Add filtering of schools by municipality on Plan Summary tab.
- Fix issues where some pages do not allow navigation away for false pending changes.
- Fix for some drop-downs being cut off from the frame of a popup.
- Show Current and Next Year Scenarios on top of drop-down in School Locator Configuration page.
- Add filtering of schools by municipality on Development Tracking > Plan Summary tab.
- Added link to phasing plan column.
- Detailed warning on school message deletion.
- UI improvements.

## ver.3.0.5 (2023-09-12)

- Removing already selected options from Unit Types dropdown.
- Fixed dropdowns in yield template modal.
- Allowed access to Scenario Data tab from Development Tracking with related permissions.

## ver.3.0.4 (2023-09-05)

- Added setting to disable background jobs for current instance of the app.

## ver.3.0.3 (2023-09-04)

- Fixed issue with Dev Plan phasing defaults breaking when missing a year.

## ver.3.0.2 (2023-08-29)

- UI improvements.

## ver.3.0.1 (2023-08-23)

- Fixed missing Boundary Polys when syncing to the cloud.
- Expanded and format sync-to-cloud logs.
- Fixed the input box for percentage values.

## ver.3.0.0 (2023-08-18)

- Initial release.

# PSTGI's SPS v3 - Change Log

These are the changes to each version that has been released in this project

## ver.3.5.5 (2025-10-28)

- Fixed postal code map not displaying in manual geocoding operations.
- Optimized geocoding API calls to prevent timeouts when looking up postal code address ranges.

## ver.3.5.4 (2025-10-20)

- Increased timeout for Data Mover process to avoid failures on slow SQL servers.
- Fixed assignment job of Study Areas on Maintenance page.
- Fixed missing feedback after assignment job of Study Areas completes.
- Fixed saving of Sub-batch Type records.
- Added protection for invalid Study Area polygons when intersecting with address points.
- Fixed missing students when batch has two or more different aliases.

## ver.3.5.3 (2025-10-07)

- Fixed the date filters in System Logs.
- Adjusted type of some data fields to match database schema.

## ver.3.5.2 (2025-10-02)

- Increased the timeout for Sync-from-Cloud.
- Combined duplicate Long-Running Processes permissions.
- Include Locality field in Legacy address comparison.

## ver.3.5.1 (2025-09-22)

- Fix issue when Sync-to-Cloud fails when ran for a first time.

## ver.3.5.0 (2025-09-22)

- OEN Import/Export feature.
- Student and MPAC import feature.
- Fixed "Round to whole numbers" checkbox not affecting exported values in Projection Summary.
- Fixed Projection Summary export incorrect values.
- Fixed School Facility tab data not sorted by Year.
- Fixed note title length limitation.
- Fixed duplicate records in tblSchoolPrograms when syncing.
- Fixed correct similar addresses functionality for study areas and suggestions.
- Fixed missing Sec column in yield templates table.
- Fixed assignment of Study Area ID and coordinates to legacy records when downloading new cloud ones.
- Fixed failure to save notes without title.
- Added settings for board name and abbreviation.
- Added "Manual Geocoding" button to Edit Master Batch modal for direct navigation to geocoding page.
- Added setting for default legacy Coordinate Reference System for all X/Y fields.
- Added warning when phasing years do not exist in Scenario Tools.
- Rounded Enrolment Projection Summary data on export.
- Sorted facility grid by year - descending.
- Improved grid refresh logic for Census and Progression Factors.
- Added Delete selected functionality to Development Default Connectors.
- Added error logging to several lookup endpoints.
- Removed automatic conversion of SHP_DATA before syncing to the cloud.
- Improved UI component for displaying progress of long-running jobs.

## ver.3.4.16 (2025-03-11)

- Fixed missing program types in School Configuration > Adjustments tab.
- Fixed missing school list from Schools page.
- Warn when outbound email configuration is not set.

## ver.3.4.15 (2025-02-06)

- Added endpoints for additional reports.

## ver.3.4.14 (2025-01-30)

- Fixed determining the last modified on date when Extended table is empty.

## ver.3.4.13 (2025-01-30)

- Added sorting of Progression Rules grid.
- Improved query for syncing address data from the cloud.

## ver.3.4.12 (2025-01-28)

- Fixed missing permission for Feeder Analysis report.
- Implemented deletion of completed long-running process records from Maintenance screen.
- Fix Scenario Data Connectors not retrieving data for the selected year.
- Fix missing columns in Enrolment Projection Details grid.
- Fix for system error when Sub-batch types do not contain comments.
- Update all dropdowns when scenario lock changes after update.
- Disabled ability to change unit type once added in Unit Worksheet.
- Change WKT to GeoJson for address suggestion endpoint.
- Disabled Approved field for newly added Unit Types in Worksheet.
- Allowed scenario selection from Scenario list.
- Fixed lock after sync fails.
- UI improvements.

## ver.3.4.11 (2024-11-28)

- Filters Study Area assignments by Home board.
- Fixed missing development plan data for scenarios other than 0.
- Fixed month shift in scenario details when in different time-zone.
- Added activation marker in Data Mover grid.
- Added progress indicators for more Scenario actions.
- Fixed deleting progression factors with conditions.

## ver.3.4.10 (2024-11-21)

- Refreshes enrolment data after school enrolment calculation completes.
- Added icon that indicate "completed" schools in dropdowns.
- Aligned School Configuration Projections grids.
- Forced scrollbars on School Configuration Projections grids.
- Populates missing values in Projection Summary Enrolment grids.
- Rounded values for Enrolment Projections Summary by Grade.
- Added dialog with results after scenario action completes.

## ver.3.4.9 (2024-10-31)

- Fixed wrong dataset name in Scenarios grid for time-zones past UTC.
- Sync-from-Cloud adds missing addresses to the legacy address table.
- Fixed missing February in Month dropdowns. 😃
- Selects another school if preselected school is not in the newly selected scenario.
- Improvements in progress bars.
- Other UI improvements.

## ver.3.4.8 (2024-10-22)

- Changed grid style to separate editable, selectable, and selected state.
- Fixed calculation when adding progression rule when enrolment equal zero.
- Added ability to compress master batch raw data files.
- Enabled deletion of Development connectors.
- Fixed issue with wrong School/Program values in Default Connectors grid.

## ver.3.4.7 (2024-09-25)

- Preserves Program dropdown selection after navigating to School Configuration > Enrolment tab.
- Sorts all Municipality dropdowns.
- Added sorting of columns in School Configuration > Holding tab.
- Improved performance for deleting multiple holding rules at a time.
- Added refresh of many Enrolment Projection pages after saving changes on others.
- Fixed issue when deleting a large number of Holding Rules.
- Fixed missing actions from the header of some pages.
- Many other UI improvements.

## ver.3.4.6 (2024-09-16)

- Refreshes the Projection tab after school calculation.

## ver.3.4.5 (2024-09-10)

- Added sort and filters to Holding Rules page.

## ver.3.4.4 (2024-09-05)

- Fixed protection for removing Development Plans with units in Registered Plans.
- Fixed calculation with negative values in Unit Worksheet.
- Added filter for Unit Type in Phasing grid.
- Added real-time calculation of total remaining units to be phased.
- Added more information to system error messages in popup.
- Added change guard to Registered Plan, Development Plan, and Master Plan pages.
- Fixed disabled Save button on Building Permits > Permit Details tab.
- Improved performance on Development Plan, Registered Plan, and Master Plan pages.
- Disabled Esc key on all popups.
- Sorts Phasing grid by Year, Plan, and Unit Type.
- Fixed updated of default values for Phasing grid.
- Fixed cell values disappearing after typing in Phasing grid.
- Fixed mismatch of Building Permit date in summary grid.

## ver.3.4.3 (2024-08-28)

- Fixes issue with Unit Worksheet not calculating and saving totals properly.
- Calculates totals and remaining units to be phased in real-time.
- Adds button to test Data Import prerequisites (Administration > SPS Setup > System Configuration).

## ver.3.4.2 (2024-08-22)

- Adds IsPreselected flag for School Locator year.
- Improves Enrolment Projection charts to show clearer capacity data.
- Shows facility capacity instead of OTG in Enrolment Projection charts.

## ver.3.4.1 (2024-08-14)

- Registered Plans are displayed with their code on Development Plan Details.
- Fixes calculation of totals on Unit Worksheet popup.
- Fixes wrongful error message after sync completes successfuly.

## ver.3.4.0 (2024-08-12)

- Adds Boundary Analysis feature.
- Exports all columns for student export to Excel.
- Adds validation error details for bad Study Area polygons.
- Adds less error messages when fetching progress fails.
- Adds ability to open legacy attachments of notes.
- Fixes error when cell has no value in Development Plan Phasing.
- Handles properly empty values for Scenario Years.
- Adds error message when Sync-to-Cloud fails for system errors.
- Loads most recent enrolment year and month in School Enrolment tab.
- Fixes issue when scenarios are not loaded when visiting the School Locator Configuration page.
- Allows editing of existing notes.
- Allows more than one file as attachments to notes.
- Add grade alias record when creating or updating grades, if not exist.
- Remove unnecessary change guard for Building Permit modal.
- Fix issue with years not appearing after adding new connector in tools window.
- Fix swapped lat/long for Development Plans.
- Allows characters different than digits in School Information.
- Add missing schools to scenario before loading its list.

## ver.3.3.11 (2024-06-18)

- Removes start time for long-running process that are running.
- Fixes issue when new schools do not appear in scenario related dropdowns.
- Fixes issue with not being able to update or delete phasing records.

## ver.3.3.10 (2024-06-13)

- Fixes validity check preventing saving of Commulities, Municipality Planning Areas, and Program Types lookups.
- Fixes column order for report exports not being persistent.
- Removes duplicate columns from Projection Summary > Enrolment by School.
- Fixes notes not refreshing when changing Master, Registered, or Development plans.

## ver.3.3.9 (2024-06-06)

- Adds migration of Development Plans Shape Data to Geometry type.
- Expands the field for the body of the note.
- Fixes navigation to Yield Template modal.
- Fixes Auto Phasing grid edit.
- Adds 'Default' as option for Auto Phasing.
- Fixes shifting of columns and totals in Projection Summary Enrolment grid.
- Removes storing time part in DT.
- Fixes Phasing Tools button visibility conditions.
- Hides Auto Phasing button depending on setting.
- Adds conversion of Development Plans SHP_DATA and centroid.
- Other minor bug fixes and UI improvements.

## ver.3.3.8 (2024-05-22)

- Rearranges permission tree for clarity.
- Allows edit of School Custom Attribute list.
- Adds ability to sync French characters to the cloud.
- Adds French character encoding for Sync-to-Cloud.
- Adds sorting columns in Schools grid.
- Fixes Active checkbox in Development Plan Details page working reversed.
- Fixes reload of data after changing Separate Holding in Scenario Tools > Enrolment Projections.
- Fixes missing total and rounding in Projection Enrolment by Grade.
- Adds link to Change Log from the version number.

## ver.3.3.7 (2024-05-08)

- Removes extra column from Feeder Analysis table.
- Fixes error when "Hold From" school is not selected.
- Adds sorting for columns in Holding tab.

## ver.3.3.6 (2024-04-30)

- Decreases loading time of the app and app size.
- Protectes boundary map loading for schools with no data.
- Unifies bar and line colours in charts.
- Fixes link to Development Plan from School Configuration > Development.
- Sorts exported projections by Year.

## ver.3.3.5 (2024-04-24)

- Fixes adding programs for new schools.
- Fixes issue of saving Schoool Info for School Locator.
- Removes posibility to delete master, development, and registered plans.
- Fixes issue of not being able to select year in School Configuration > Enrolment.
- Fixes wrong totals in historic enrolment.
- Fixes exported list of students from Boundary Map.
- Removes unnecesary change notification when phasing or shifting development plans.
- Adds access to validity details using the icon in Scenario Calculation grid.
- Optimizes loading of some pages and added other minor improvements.

## ver.3.3.4 (2024-04-08)

- Adds Sync-Address-from-Cloud progress to AutoProcesses table record.
- Fixes chart failure with some selections.
- Fixes missing colours from Projection Summary charts.
- Fixes the Y-axis in charts to start from zero.
- Adds missing localization strings.
- Adds indicators for currently running calculations of scenarios.
- Fixes issue with missing digits after decimal point.
- Improves capitalization when exporting grids to Excel.
- Unified number of digits after decimal point for percentages in many grids.
- Adds Long-running processes page.
- Adds user format selection to school dropdowns.
- Many other UI improvements and bug fixes.

## ver.3.3.3 (2024-03-21)

- Reloads all data after scenario calculation completes.

## ver.3.3.2 (2024-03-19)

- Refreshes cached scenarios when a new one is created.

## ver.3.3.1 (2024-03-14)

- Fixes issue with not saving scenario updates because of trigger messages as raised errors.
- Removes password transfer from v3 to v1.
- Fixes misaligned panels on Sync page.

## ver.3.3.0 (2024-03-13)

- Adds check for validity of a School Locator batch before activating it.
- Resets cache after activating a School Locator batch.
- Adds feature to download new addresses from Master repository on the Cloud.
- Adds more sortable columns to Scenarios page.
- Added export of schools as Shape file.
- UI improvements and cleanup.

## ver.3.2.5 (2024-02-28)

- Adds notification for bad Study Area polygons.
- Fixes totals for Progression Factors historic averages.
- Adds coordinate system selection for exporting geometry data.

## ver.3.2.4 (2024-02-26)

- Fixes spinner on Sync Database page.

## ver.3.2.3 (2024-02-26)

- Adds forced browser refresh when new version is deployed.
- Adds filter for schools when program boundaries are filtered.
- Fixes map centering when no program boundaries or study areas.

## ver.3.2.2 (2024-02-21)

- Fixes issue with missing parameters in some API calls.

## ver.3.2.1 (2024-02-21)

- Fixes issue with permissions to write temporary files on some systems.
- Adds exporting of GeoJSON and Shape files with different projections.

## ver.3.2.0 (2024-02-21)

- Adds School Program boundary map.
- Optimizes performance of some pages that contain multiple selectors.
- UI improvemements.

## ver.3.1.0 (2024-02-08)

- Enrolment Projections - main release.
- Many performance optimizations.
- Many bug fixes.

## ver.3.0.16 (2024-01-16)

- Adds bulk delete for school Holding.
- Updated schema of tblGisMasterAddressExtended table.
- Adds persistence for Program Type and other selection within Enrolment Projections.
- Optimized number of API calls in many pages.
- Adds "Select All" to School Configuration Holding grid.
- Fixes dislaying Back button for the same school.
- Fixes chart not reloading when school is changed.
- Fixes many minor bugs.

## ver.3.0.15 (2024-01-02)

- Changed data schema in GisMasterAddressExtended table.

## ver.3.0.14 (2023-12-13)

- Fixes filters for some dropdowns not working properly.
- Removes permission for My SPS page - now accessible to all.
- Expands Program Type dropdown to display code and name.

## ver.3.0.13 (2023-12-04)

- Fixes batch information panel for some edge cases.
- Adds Program Type aliases to syncing to cloud.
- Adds ability to copy school assignment overrides from one year to another.

## ver.3.0.12 (2023-11-23)

- Combined all related notes in School Configuration Projections grid.
- Fixes impossible save of deleted note for scenario 0.
- Fixes missing grid when calculating EP > Progression Factors.
- Fixes failure because of unique key constraint in EP > Add holding rules.
- Properly filter school programs for feeder school analysis.
- Continue checking for a running background job even after database timeout.
- Adds ability to enter decimal number starting with a dot in grids.
- Adds tooltip to Projections chart.
- Allows closing of Yield Template modal with no changes.
- Other UI improvements.

## ver.3.0.11 (2023-11-08)

- Fixes filter on schools dropdown in Enrolment Projections.
- Sorted school list in Overrides.
- Adds separate symbols for different Study Area meanings.
- Shows all fields on the Update Message modal.
- Adds links opening the school locator for the active or latest batch.

## ver.3.0.10 (2023-10-31)
- Adds missing fields from School Overrides into the Sync-to-cloud data.
- Removes ability to edit School Overrides for years that are not in the current and next year's scenarios.
- Changed Study Area reference from School Overrides to a single id.
- Allows adding new School Override from the Notice messages page.
- Adds mandatory Notice message to every School Override.
- Extended size of Development Plan Comment and Description fields to 1000 characters.
- Adds more information when editing notice messages.

## ver.3.0.9 (2023-10-11)

- Fixes issues with some fields not being synced properly to cloud School Locator database.

## ver.3.0.6 (2023-10-02)

- Add filtering of schools by municipality on Plan Summary tab.
- Fixes issues where some pages do not allow navigation away for false pending changes.
- Fixes for some drop-downs being cut off from the frame of a popup.
- Show Current and Next Year Scenarios on top of drop-down in School Locator Configuration page.
- Add filtering of schools by municipality on Development Tracking > Plan Summary tab.
- Adds link to phasing plan column.
- Detailed warning on school message deletion.
- UI improvements.

## ver.3.0.5 (2023-09-12)

- Removing already selected options from Unit Types dropdown.
- Fixes dropdowns in yield template modal.
- Allows access to Scenario Data tab from Development Tracking with related permissions.

## ver.3.0.4 (2023-09-05)

- Adds setting to disable background jobs for current instance of the app.

## ver.3.0.3 (2023-09-04)

- Fixes issue with Dev Plan phasing defaults breaking when missing a year.

## ver.3.0.2 (2023-08-29)

- UI improvements.

## ver.3.0.1 (2023-08-23)

- Fixes missing Boundary Polys when syncing to the cloud.
- Expands and format sync-to-cloud logs.
- Fixes the input box for percentage values.

## ver.3.0.0 (2023-08-18)

- Initial release.

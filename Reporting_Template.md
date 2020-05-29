# App Usage Metrics Report
Usage metrics on RedLine applications.
## Data Sources
Data for this report is taken from the data sources listed below.
* [App Usage Metrics Dataset][data-source]
## Definitions
These are the definitions for the terms used in this document.
### <a id="def-activity"></a>Activity
A finite, discrete action that a user can perform within the context of an application.
### <a id="def-grant"></a>Grant
Permissions that allow a user to perform a specific Activity within an application. These permissions, referred to as a Grant, are given by an administrator.
### <a id="def-user"></a>User
A user is an individual with login credentials using one or more RedLine applications.
## Aggregated Usage Histogram
The histogram visualizes aggregated usage every 15 minutes over the last 24 hours. Each point is a sum of all the activities for all applications at a 15 minute period. Hovering over a point will display a summary of the applications.
## Usage Data
The detailed usage data is presented in a tabular format as follows:
### Rows
Each row in the represents an instance where a User attempted to exercise a Grant by using one or more features in a RedLine application.
### Columns
These are the columns in the Usage Data grid.
#### Column: Date/Time (UTC)
The date and time in Coordinated Universal Time (UTC) the User attempted to exercise the Grant.
##### Data Source
Data in this column is taken directly from `some.fully.qualified.field`.
#### Column: Application name
The name of the RedLine application.
##### Data Source
Data in this column is formula-driven as follows:
(`database.schema.table.fizzle_bob` / `month_num`) * 0.424
Where:
* `database.schema.table.fizzle_bob` is...
* `month_num` is the numerical month (e.g., January=1, February=2, etc.)
* 0.424 is a factor taken from the MEVA-AB95 Actuarial Table provided by Risk
Example:
[code cell]
## Revision History
Refer to ASME Y14.35M for how the revision lettering works.
| REV | Date       | Description                                                            |
|-----|------------|------------------------------------------------------------------------|
|  A  | 2020-05-25 | Updated the description for the BoofyWiz column.                       |
[//]: # (These are link are link and image definitions)
[data-source]: https://apps.hawking.dimebox.io/#/data-catalog/grid/app-usage-metrics
[def-activity]: #def-activity
[def-grant]: #def-grant
[def-user]: #def-user
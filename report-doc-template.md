# Overview

_This section asists business users with the functional aspects of this report_

## Title

_name or title of the report_

## Description

_brief description of report_

## Accessing the Report

_what steps are taken to open and view this report_

## Business Objective

_what business problem does this report solve_

## Triggering Activity

_what business process begins the production of this report_

## Impact of Non Availability

_what negative business impacts does the untimely production of this report have_

## Ownership

_key owner(s) that approve changes to this report_

## Support & Help

_which business area can provide functional support and can answer clarifying questions about its measures and dimensions_

# Report Operations & Support

_This section is intermediate level documentation which includes mostly non functional aspects of the report_

## Dataset Source

_the source of truth and providence of this report_

## Source System

_which application(s) or operations provided the data for this report_

## Report Update Timing or Schedule

_how often is this report run_

## Data Sensitivity

_list the data sensitivity classification for this report, if any_

## Data Security

_list the data security requirements (auth/roles) for this report_

# Report Audit & Traceability

_This is an advanced level of documentation setting out fact dimension detail at the most granular level on all components of the report_

## Report Components

_describe the components of the report. i.e a grid, visual, filter, buttons, parameters, etc. These will later be used as categories when describing fact/dimensions._

## Row Level Detail

_define what a row represents on each component_
_Question to be answered is what does a row represent. Observation granularity for dimension or fact. Dollars sales by week, product, and customer for example._

_include and condition, predicate, filter or Where clause of the data soure_

## Column Detail

### Column [_name_]

_describe the column and its calculation or forumla_

- Component Name
- Fully Qualified Column Name e.g. (`database.schema.table.fizzle_bob`)
- Column or Column Formula, e.g. (`database.schema.table.fizzle_bob` / `month_num`) \* 0.424
- Dimension or Measure/Fact
- Aggregation
- Masking Type: _(none, static, or dynamic)_

## Relationships & Dependencies

_List the dependencies of this report if any_

#### Reference Items

[Conforming Dimensions](Master Data)\
Enterprise Data Bus Matrix\
Linked DataSets or Reports\
Errata

## Revision History

_use the same versioning convention used by the source control system of the report_
| REV | Date | Description |
|-----|------------|------------------------------------------------------------------------|
| A | 2020-05-25 | Updated the description for the BoofyWiz column. |

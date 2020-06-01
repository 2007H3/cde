# Overview

## Title

Application Metrics Report

## Description

Usage metrics on RedLine applications.

## Accessing the Report

1. Login to Redline
2. Launch the Data Catalog
3. In Reports, click on the Application Metrics Report

## Business Objective

This report presents a view into Redline micro application usage by user, the application used, and the action a user took on the application.

## Triggering Activity

This report is triggered when an analyis activity against Redline applications is necessary.

## Impact of Non Availability

Without this report, visibility into application usage is not present witin Redline.

## Ownership

_key owner(s) that approve changes to this report_

## Support & Help

_which business area can provide functional support and can answer clarifying questions about its measures and dimensions_

# Report Operations & Support

_This section is intermediate level documentation which includes mostly non functional aspects of the report_

## Dataset Source

The Operational Data Store (ODS)

## Source System

Every Redline micro app is a source for this dataset.

## Report Update Timing or Schedule

Nightly

## Data Sensitivity

Data is classified as sensitive (sensitive, PII, etc..)

## Data Security

_list the data security requirements (auth/roles) for this report_

# Report Audit & Traceability

_This is an advanced level of documentation setting out component, fact and dimension detail at the most granular level on all components of the report_

## Report Components

This report uses a Grid for raw data presentation, a Bar Chart for visualization, a filter for slicing, and a download button to export in csv.

Grid - The detailed usage data is presented in a tabular format and displays the underlying dataest without aggregation. The data is grouped by x,y,z\
Bar Chart - The bar chart visualizes aggregated usage every 15 minutes over the last 24 hours. Each point is a sum of all the activities for all applications at a 15 minute period. Hovering over a point will display a summary of the applications.\
Filter -\
Export Button - Used to downolad dataset in csv format.

## Row Level Detail by Component

Each row in the represents an instance where a User attempted to exercise a Grant by using one or more features in a RedLine application.

## Column Detail

### Activity

- Component: Grid
- Description: A finite, discrete action that a user can perform within the context of an application.
- Column or Column Formula: None
- Dimension or Fact: Fact
- Aggregated: No

### Grant

- Component: Grid
- Description: Permissions that allow a user to perform a specific Activity within an application. These permissions, referred to as a Grant, are given by an administrator.
- Column or Column Formula: None
- Dimension or Fact: Dimension
- Aggregated: No

### User

- Component: Grid
- Description: A user is an individual with login credentials using one or more RedLine applications.
- Column or Column Formula: None
- Dimension or Fact: Dimension
- Aggregated: No

### Date/Time (UTC)

- Component: Barchart
- Description: The date and time in Coordinated Universal Time (UTC) the User attempted to exercise the Grant.
- Column or Column Formula: None
- Dimension or Fact: Dimension
- Aggregated: No

### Data Source

- Component: Barchart
- Description: Data in this column is taken directly from `some.fully.qualified.field`.
- Column or Column Formula: None
- Dimension or Fact: Dimension
- Aggregated: No

### Application name

- Component: Barchart
- Description: The name of the RedLine application.
- Column or Column Formula: None
- Dimension or Fact: Dimension
- Aggregated: No

## Relationships & Dependencies

_List the dependencies of this report if any_

#### Reference Items

The referenced [dataset]("./dataset")

## Revision History

_use the same versioning convention used by the source control system of the report_

| REV | Date       | Description                                      |
| --- | ---------- | ------------------------------------------------ |
| A   | 2020-05-25 | Updated the description for the BoofyWiz column. |

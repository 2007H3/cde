# Solution Assessment & Validation for the Report Documentation Template

Date: 2020-05-27

## Status

Proposed

## Related Documents

[./Reporting Template.md](./Reporting_Template.md)

## Context

This solution assessment & validation document describes and ensures that the conventions used in the Reporting Document Template are aligned with industry and vendor non proprietary report documentation standards, and to ensure that key requirements from the standpoint of the user, auditor, and data manager are met.

An implementation of a reporting documentation template will be used across Redline reporting to serve users, auditors and to a limited extent, software developers. This is an "architectural" information process description - a business analysis artifact.

## Template Goals & Requirements

### Key Requirements

- Provide Contextual Help to End users
- Provide Support to the Audit function
- Reflects Best Practices
- Document Report Components (rows/columns/charts/filters etc) to provide functional and technical traceability to every displayed aspect of the report and it's underlying datasource.

### Key Goals

What should a reporting documentation template include? The general idea was to collect and use available industry and vendor concepts to produce a mix of function, non functional and technical documentation for reporting, and standardize that across the business.

Another goal was to have a document that was accessible programmatically to serve it from a rendering platform or api. Id's should be established in the template for programmatic access, opening up the possibility of serving the document via such an api.

Documentation **could** be rendered via a [Jupyter notebook](http://jupyter.org), although the resulting solution would be both vendor agnostic and rendering technology agnostic using common markdown.

## Existing Guidance

A broad search revealed no definitive, tool, process, taxonomy or technique used to document reporting in the industry. There wasn't a 'grab-n-go' template to simply fill in. The idea here was to create a balance of best practices in the vendor reporting, business process, and data industries and use them in ways that fit our use case.

Therefore, the set of constructs and criteria used here were derived out of best practices from both:

- Report Software Vendors
- Standards Setting Bodies
- Data Management Architectures

Guidance from the following Vendors was incorporated:

1. Microsoft
1. Red-Gate
1. IBM

Guidance from the following Standards setting bodies or associations were incorporated:

1. Kimball Group - Dimensional modeling and ETL Architectures, Enterprise Service Bus
1. PMBOK - Project management body of knowledge (Scope Planning, Scope Definition)
1. BABOK - Business Analysis Body of Knowledge (Business Rules Analysis)
1. CMMI - Capability Maturity Model Integrated (Software quality and assurance)
1. AICPA - Audited Financial Statements (controls, assessment, and attestation)
1. ITIL - Information Technology Infrasturcture Library (Service Provider Management)

## The Audience

Report End Users, Report Auditors, Report & Software Developers are the audience of the reporting documentation. There are fundamental questions to be answered for each group that will be used to satisfy each.

From an end user perspective, the fundamental quesiton to be answered is:

_Does the documentation present a clear path to timely usage of the report?_

From an audit perspective, the fundamental question to be answered is:

_Is there enough guidance and specificity around a measure or dimension (row/column) such that an auditor can attest to its accuracy?_

From a developer perspective, the fundamental question to be answered is:

_Does the documentation present a technical foundation from which to support the software development process_

# The Template Structure

## Graduating Levels of Detail

To aid in usability, the documentation should be organized around increasing levels of detail. Those levels are:

_Foundational_ - Functional, Contextual and descriptive end user facing help

_Intermediate_ - Mostly Non functional specification, i.e Data Connections, Authorization, Data Privacy Classification, etc.

_Advanced_ - Atomic technical detail of individual data points and operations on those data points.

_Reference_ - Reference information and errata.

#### Foundational Level

Report Title \
Instructions\
Business Objective \
Triggering Activity \
Impact of Non Availability\
Ownership\
Support\

#### Intermediate Level

Dataset Source of Truth\
Source System\
Report Update Timing or Schedule \
Data Sensitivity\
Data Security\
Version\
Format\
Link\

#### Advanced Level

Components\
Row Level Detail - Observation granularity for dimension or fact\
Column Level Detail - (Dimension or Fact description)\

- Type ( time, numeric, date/time )
- Primary/Foreign Key
- Fact or Dimension
- Conformed ( master data )
- Operation Description ( caluclated formula )

Relationships & Dependencies\

#### Reference Items

Enterprise Data Bus Matrix\
Linked DataSets or Reports\
Errata

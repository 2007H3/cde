# Solution Assessment & Validation for the Report Documentation Template

Date: 2020-05-27

## Status

Proposed

## Related Documents

[./Reporting Remplate.md](./Reporting_Template.md)

## Context

This solution assessment & validation document describes and ensures that the key decisions, formats and conventions used in the Reporting Document Template are aligned with industry and vendor non proprietary report documentation standards, and to ensure that key requirements from the standpoint of the user, auditor, and data manager are met.

An implemnetation of a reporting documentation template will be used across Redline reporting to serve users, auditors and to a tertiary extent, developers. This is an "architectural" information process description.

## Template Goals & Requirements

### Key Requirements

- Provide Contextual Help to End users
- Provide Support to the Audit function
- Reflects best practices
- Document Report components (rows/columns/charts/filters etc) to provide functional and technical traceability to every displayed aspect of the report.

### Key Goals

What should a reporting documentation template include? The general idea was to have a healthy mix between design specification (for audit) and end user documentation (for contextual help). Ids should be established in the template for programmatic access, giving the possibility of serving the document in sections. Documentation **could** be rendered via a [Jupyter notebook](http://jupyter.org), although the result would be both vendor agnostic and rendering technology agnostic.

## Existing Guidance

A broad search revealed no definitive, tool, process, taxonomy or technique used to document reporting in the industry. There wasn't a 'grab-n-go' template to simply fill in. The idea here was to create a mashup of several definitive best practices around the vendor reporting and business process industries and use them in ways that fit our use case.

Therefore, the set of constructs and criteria used here were derived out of best practices from both:

- Report Software Vendors
- Standards Setting Bodies

Guidance from the following Vendors was incorporated:

1. Microsoft
1. Red-Gate
1. IBM

Guidance from the following Standards setting bodies or associations were incorporated:

1. PMBOK - Project management body of knowledge (Scope Planning, Scope Definition)
1. BABOK - Business Analysis Body of Knowledge (Business Rules Analysis)
1. CMMI - Capability Maturity Model Integrated (Enterprise data architecture, governance and quality)
1. AICPA - Audited Financial Statements (controls, assessment, and attestation)
1. ITIL - Information Technology Infrasturcture Library (Service Provider Management)
1. Kimball Group - Dimensional modeling and ETL Architectures

## The Audience

Report End Users, Auditors, Developers

From an audit perspective, the fundamental question to be answered is:

_Is there enough guidance around a measure or dimension (row/column) such that an auditor can attest to its accuracy?_

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

Database Source\
Source System\
Report Update Timing or Schedule \
Data Sensitivity\
Data Security\
Version\
Format\
Link\

#### Advanced Level

Row (observation granularity for dimension or fact) level Detail\
Column (dimension or fact description) level Detail\
Time Series\
Relationships\

#### Reference Items

Linked reports\
Errata

##### Dataset/Query Detail

### Incorporate

Data source: scs_dev-innovation

Connection string:

Report type: Table

Layout type: Stepped

Style: Slate

Details: irate_book, iplan_id, isurcharge_id, iopt_id, splan, snew_used, icontract_type

Query: SELECT scs_plan_rate_book.\*
FROM scs_plan_rate_book

### Pros

N/A

### Cons

N/A

## Decision

TBD

## Consequences

We can now render Jupyter notebooks.

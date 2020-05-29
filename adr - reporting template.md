# Solution Assessment & Validation for the Report Documentation Template

Date: 2020-05-27

## Status

Proposed

## Related Documents
[./Reporting Remplate.md](.\/Reporting_Template.md)

## Context

This solution assessment & validation document describes and ensures that the key decisions, formats and conventions used in the Reporting Document Template are aligned with industry and vendor report documentation standards, and to ensure that key requirements from the standpoint of user, audit, and data management are met. 

An implemnetation of a reporting documentation template will be used across Redline reporting to serve users, auditors and to a tertiary extent, developers. This is an "architectural" business process description.

## Template Goals & Requirements

### Key Requirements
* Provide Contextual Help to End users
* Provide attestation support to the audit function
* Reflects best practices
* Document Report components (rows/columns/charts/filters etc) to provide functional and technical traceability to every displayed aspect of the report.


### Key Goals
What should a reporting documentation template include? The general idea was to have a healthy mix between design specification (for audit) and end user documentation (for contextual help). And to establish ids in the template that could be queried programmatically for the possibility of serving the document in sections. Documentation would be rendered via a [Jupyter notebook](http://jupyter.org), although the result would be both vendor agnostic and rendering method agnostic.

## Existing Guidance

There wasn't a definitive, tool, process, taxonomy or technique used to document reporting in the industry. There wasn't a 'grab-n-go' template to simply fill in. The idea was to take a mashup of several definitive best practices around the reporting and business process industries and use them.

Therefore, the set of constructs and criteria used here were a mashup of best practices from both:

- Report software Vendors
- Standards Setting Bodies

Guidance from the following Vendors was incorporated:

1. Microsoft
1. Red-Gate
1. IBM

Guidance from the following Standards setting bodies or associations was incorporated:

1. PMBOK - Project management body of knowledge (Scope Planning, Scope Definition)
1. BABOK - Business Analysis Body of Knowledge (Business Rules Analysis)
1. CMMI - Capability Maturity Model Integrated (Enterprise data architecture, governance and quality)
1. AICPA - Audited Financial Statements (control, assessment, and attestation)
1. ITIL - Information Technology Infrasturcture Library (Service Provider Management)

## The Audience

TBD

# The Template Structure

## Graduating Levels of Detail

To aid in usability, the documentation should be organized around increasing levels of detail. Those levels are:

- Foundational - Contextual and descriptive end user facing help
- Intermediate - Functional and non functional specifications
- Advanced - atomic and technical detail around individual data points and operations on those data points.

### Pros

N/A

### Cons

N/A

## Decision

TBD

## Consequences

We can now render Jupyter notebooks.

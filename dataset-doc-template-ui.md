<link href="./style.css" rel="stylesheet"></link>

# Overview

_This section assists business users with the functional aspects of this report_

## Platform

_Service platform, currently RedLine or MyGSFS_

## Update timing or schedule

_how often is this report run_

## Business objective

_what business problem does this report solve_

## Triggering activity

_what business process begins the production of this report_

## Impact of non-availability

_what negative business impacts does the untimely production of this report have_

# Data governance ([`x of 5`] requirements met)

`use either class="complete" or class="incomplete" to note status of governed criteria. Class="data-governance" should remain unmodified`

<ul id="data-governance-list" class="data-governance">
   <li class="complete">
      <b>Ownership</b> <span>is complete</span>
      </br>Key owner(s) that approve changes to this report are: Doc Emmett Brown, Einstein Brown
   </li>

   <li class="complete">
      <b>Dataset source</b> <span>is complete</span>
      <br>ex. This dataset is an originating dataset.  Additional source system information can be found within this document.</br>[Updated m/dd/yyyy]</br>[Audit passed on m/dd/yyyy][Owner name]
   </li>

   <li class="incomplete">
      <b>Documentation</b> <span>is incomplete</span>
      <br>ex. This [report/dataset] is [fully] documented.
   </li>

   <li class="complete">
      <b>Source system</b> <span>is complete</span>
      <br>ex. This dataset uses information captured directly from RedLine’s micro-applicatons.
   </li>

   <li class="complete">
      <b>Report audit & traceability</b> <span>is complete</span>
      <br>This is an advanced level of documentation setting out component, fact and dimension detail at the most granular level on all com-ponents of the report
   </li>
</ul>
 
<a href="" title="" target="">View provenance</a>  
<a href="" title="" target="">Last audit report</a>
 
# Security & sensitivity details

_list the data sensitivity classification for this report, if any_

ex. This [dataset] is classified as: Sensitive

The security requirements for this dataset are:  
[auth/activities for this dataset][activity 1]

# Presentation information

ex. This dataset uses a grid for raw data presentation, column filters for slicing, and a download button to export in csv.

## Export button

Used to download dataset in csv format.

## Grid

ex. The detailed usage data is presented in a tabular format and displays the underlying dataest without aggregation. The data is grouped by x,y,z

<div class="indent-1">Rows

_define what a row represents on each component_
_Question to be answered is what does a row represent. Observation granularity for dimension or fact. Dollars sales by week, product, and customer for example._

</div>

<div class="indent-1">Columns

_describe the column and its calculation or forumla_

Columns Include:  
[column heading ( ∑ )]

- Component Name
- Fully Qualified Column Name e.g. (`database.schema.table.fizzle_bob`)
- Column or Column Formula, e.g. (`database.schema.table.fizzle_bob` / `month_num`) \* 0.424
- Dimension or Measure/Fact
- Aggregation
- Masking Type: _(none, static, or dynamic)_
</div>

# Relationships & dependencies

_List the dependencies of this report if any_

# Revision history

_use the same versioning convention used by the source control system of the report_
| REV | Date | Description |
|-----|------------|------------------------------------------------------------------------|
| A | 2020-05-25 | Updated the description for the BoofyWiz column. |

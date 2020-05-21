# PII Masking

## The Product

Red-Gate Data Masker was used to create maskins instructions known as Rulesets. At the time of this writing, the product was new. 

> **NOTE:** Red-Gate Masking Tool documentation can be found [here](https://documentation.red-gate.com/d

## The Worfklow

#### The following workflow describes the method used to construct Masking Rules that were used to produce masking rules run against Scs innovation database

To simplify the entry of masking rules for large datbases, this workflow was created. This differs from the typical method Red-Gate suggests software usage - which is to build the rules within the software. 

This workflow deviation sped up PII identification and mask rule creation. Once the ruleset was created, the rules were copied to a Redgate Rule Set file. After the basic rulesets were constructed, the rules were further refined within Redgates Data Masking tool. 

> **NOTE:** The tool produces a proprietary file called a Rule Masking Set file. The file is text and xml formatted.

[x] Red-Gate Data Masker ==> [x] Import Sql Server Data Classification Report ==> [x] Export Plan ==> [x] Fine Tune the Plan in an Excel Template ==> [x] Generate a base set of substitution rules for using a macro in the Template ==> [x] Modify the Red-Gate masking set file using the xml produced by the macro.


*Definitions*

Plan: A plan as defined by Red-Gate is an internal representation of the
database schema identifying sensitive columns as candidates for PII.

Excel Template: Data Classification Report.xlsm.

DataSet: A database of substitution terms supplied by Redgate.

Rule.

\#\#\# My Great Heading {\#custom-id}

The HTML looks like this:

\<h3 id="custom-id"\>My Great Heading\</h3\>

The following guides are used in creation of the masking plan.

-   Sensitive columns in the SCS_AUTO_GSFS (SCS) database are evaluated for
    Personally Identifiable Information (PII ) and potentially masked.

-   All foreign and primary keys in SCS are unnatural keys, i.e. don’t contain
    PII.

-   Non Key column names are potentially shared across tables without database
    defined constraints. Those columns must be identified and set up to
    synchronize in the Data Masking tool.

-   Information Sensitivity is defined by SQL Servers 2012 Data Classify feature
    that is run in Sql Server Management Studio

-   The Data Classification report is exported to a Master list of DB Columns
    used for tracking columns with enabled masking rules.

-   Masked columns are reviewed for accuracy by a data owner. Any changes to the
    masking rules are also approved by the data owner.

-   Optional: Backup the scs_auto_group db prior to running the test.

**Master List of SCS DB Columns**

-   **This file is a cleaned version of the Data Classification Report from Sql
    Server Management Studio**

-   **File Name: Data Masking Report.xlsx**

**Masking Software Used:**

1.  Red Gate Data Masker V 7.0.16.5777 – The masking application that stores

2.  SQL Server Management Studio 2010 – The task that produces a data
    classification report used downstream.

**Testing Process:**

1.  Run In SSMS a sql script that that saves a pre-test copy of the data to be
    masked. Export that report and name it “Pre Test Unmasked.csv”

2.  Run the Masking Plan in Red Gate Data Masker.

3.  Wait for the masking to finish.

4.  Run In SSMS a sql script that that saves a post-test copy of the masked
    data. Export that report name it “Post Test Masked.csv”

5.  Difference the files from step 1 and 4.

6.  Visually inspect the difference for results.

# PII Masking

## How to use this document:
1. To undestand how the PII project was implemented from start to finish, continue reading.
1. To modify and/or run an existing masking set, goto to [Appendix A]("./cde#appendix-a").

## The Data Masker Product

Red-Gate Data Masker was used to create masking rules to sanitize personally identifiable information (PII) in the Scs dev Innovation database. Version 7.0.16.5777 was used in a 14 day trial period. This product supports a wide range of data privacy obfuscation use cases for products, internal audits, and regulatory and statutory concerns.

> **NOTE:** Red-Gate Masking Tool (RGMT) documentation can be found [here](https://documentation.red-gate.com/d).  A good reference on PII can be found [here](https://www.identityforce.com/blog/what-is-pii).

## The User Worfklow 

#### The following workflow describes the method used to construct a Masking Set for the Redline PII story.

To simplify the entry of masking rules for large databases like Scs, this workflow was created. This workflow differs from the typical method Red-Gate suggests to use its software - that is to identify mask columns then, build rules all within the software application. The modified worklow builds basic substitution rules outside of the software using Excel to manage masked columns and a macro to build a intermediary xml file that read the Excel masked columns, which are then copied into the masking set file used by Red-Gate. At that point, futher refinements are made within RGMT.

> **NOTE:** To use this workflow, familiarity with Red-Gate's xml masking rules schema, the msxml Active X library, Xpath, Excel and Vba scripting is helpful.  This workflow is not required of any masking project - it only helps simplify the creation of creating a set of "starter" rules in larger projects.

* The RGMT produces a proprietary file called a Rule Masking Set file. The is an xml file that conforms to Red-Gate's proprietary xml data masking schema.
* The Scs database is composed of over 950 tables, and 15K columns. Having to wade through the UI to establish the rules proved to be too time consuming.

Since the underlying file was xml, we were able to construct a macro that built out a base set of substitution rules [see: How to Create Rules]. This workflow deviation sped up PII identification and mask rule creation. Once the ruleset was created, the rules were copied to the proprietary Redgate Rule Set file. After the basic rulesets were constructed, the rules were further refined within Redgates Data Masking tool. 

> **IMPORTANT NOTE:** If a masking project is simple, this workflow can be reduced to the two workflows found in Usage workflow details, the 1) Red-Gate Data Masker and 2) Import Sql Server Data Classification Report. See Below. 

> **Warning:** If the underlying Xml schema is changed by Red-Gate and breaks the macro, this workflow will need to be updated to conform to the new schema. i.e. the macro that produces the intermediary Ruleset file 

### Workflow Sequence
The followin illustrates workflow steps, when executed in sequence pr

[x] Red-Gate Data Masker ==> [x] Import Sql Server Data Classification Report ==> [x] Export Plan ==> [x] Tune the Plan in an Excel Template ==> [x] Generate a base set of substitution rules for using a macro in the Template ==> [x] Modify the Red-Gate masking set file using the xml produced by the macro.

## Usage Workfow Steps
* Red-Gate Data Masker 
1. Fork the Barium.Scs gsfs project and clone it locally.
1. Open up the Red-gate Sofwate and create a new masking set
1. Enter the masking target database Server connection settings
1. Save the file in the /data-masking folder
1. Open the Barium.Scs root folder in vscode
1. Open the masking set created

* Import Sql Server Data Classification Report 
1. Open RGMT, Click the Tables Tab, then Export/Import Plan
1. Select the Import option, and import the Sql Server Data Classification Importer
1. Save the masking set
1. At this point, a recommended set of PII as reported in the Sql Server classification tool is created in the Tables tab of RGMT.
1. For projects that are "simple" i.e. under 20 tables, stop here. You can continue "How To Create Rules" 

* Export Plan 
1. Choosing all options in the Table Tab, click the Import/Export button and export the plan to csv - name the file "export_plan_[project].csv", this will give you a list of all tables and columns with suggested PII.
1. Open the csv file in Excel (data menu/Get Data/Text) and format the data according to the Excel Template.

*  Tune the Plan in an Excel Template 
1. Open the Excel Template (read note below)
1. Remove all data excel the header row from the red colums in the "Template" sheet
1. Copy paste from exported plan data into the Template
1. Now begin to classify the data using the following labels in the "Data Set" column, column E:
    * Phone
    * Email
    * Address
    * City
    * State
    * Zip
    * Title
    * FullName
    * FirstName
    * LastName
    * MiddleName

> **NOTE:** The template can be found at "/data_masking/Data Classification Report.xlsm"

* Generate a base set of substitution rules for using a macro in the Template 
1. Once tuning is complete, 

==> [x] Modify the Red-Gate masking set file using the xml produced by the macro.

## The Macro

The macro will create masking rules from a list. Only substitution rules are supported.

 #### Dependencies: 
1. An empty (no rules) Redgate Data Masker File for the target database.
1. A list of columns to mask. Current list is maintained in this workbook.
1. A substution xml fragment, subst_xml_fragment_template.xml

Input: A list of masking columns, sorted by table, and dataset

Output: An xml_result.xml rules masking file that can be partially copied to a
         Redgate Data Masker File



## Appendix A

### To Modify or Run a Masking Set against the SCS Innovation DB
* Fork the SCS Repo and clone it locally
* Open Red-Get Data Masker
* Open Masking Set file in /data-masker/scs_auto_gsfs.DMSMaskSet
* Either press Ctrl+Enter, or click the Run Menu, then click the Run Masking Set item

> **NOTE:** Masking Rule creation documentation can be found online [here](https://documentation.red-gate.com/dms)

Requirements to Run a Masking Set 
===
* Red Line Data Masker licensed Version 7 or above 


## Definitions

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

## How to Create Rules
* Subsitution rules can be created in several ways. The most common are noted here. 

## How to Run the Masking Set File Locally
* in Barium.Scs, open the scs_auto_gsfs.DMSMaskSet file in Red-Gate Data Masker
* Locate the "Run masking set" item on the ribbon
* Click the Play button.

> **NOTE:** The current Masking Set takes upwards of 10 hours to run on a VPN connection.
Overview of the GSFSGroup Data Exchange
=======================================

Welcome to the GSFSGroup® Data Exchange powered by RedLine, a file transfer
service that allows GSFSGroup business partners to securely and reliably SHAre
their critical data with GSFSGroup. This is a private SFTP service accessible
only to GSFSGroup partners, which uses the latest standards in asymmetric
security to keep your structured data safe and free from compromise while at
rest or in transit.

The file transfer process is always the same: encrypt your data file, create a
manifest file, login to your SFTP server, send the manifest and data file, and
receive a return receipt with the result. Current supported format for data
files is comma separated value. The schema of the data files sent by partners is
always negotiated beforehand with GSFSGroup. Once that schema is in place, the
GSFSGroup Data Exchange is ready to accept your data files.

The remainder of this user guide will assist you with getting up and running
with the GSFSGroup Data Exchange.

Before you begin
================

The following sequence of steps is MUST be completed prior to sending data files
to the GSFSGroup Data Exchange:

1.  Receive your Data Exchange email invite

2.  Install the required software

3.  Create your SSH and PGP key pairs

4.  The Data Exchange email invite will contain the GSFSGroup public PGP key
    which you will import into your PGP tool

5.  Export public keys and email them to GSFSGroup Data Exchange Administrator
    along with your preferred contact phone number for public key verification

6.  A GSFSGroup Data Exchange Administrator will call you to verify the public
    keys you sent

7.  Receive your access confirmation by email

After these steps are successfully completed, you can start sending data files
to GSFSGroup securely.

Invitation to access the GSFSGroup Data Exchange
------------------------------------------------

As a partner, you will receive an email invitation from a GSFSGroup Data
Exchange Administrator. This email will contain important information including:
connection information to your SFTP host, a user account for authentication, and
a GSFSGroup provided public key you’ll use for encrypting data prior to sending
data files to the GSFSGroup Data Exchange.

The GSFSGroup public key must be imported into your encryption program. Details
about this process are provided later in this user guide.

The invite will also contain instructions on how to send *your* public keys back
to GSFSGroup for SFTP SSH authentication and data encryption for files sent by
the GSFSGroup Data Exchange to you. You can connect to the GSFSGroup Data
Exchange once your public keys are received by a GSFSGroup Data Exchange
Administrator and access is granted. You will be notified by email when access
has been granted to you.

Important! Save this invite. You will be referencing it while you get familiar
with the GSFSGroup Data Exchange

Software you will need
----------------------

For Windows users, the software recommended to encrypt, connect, and send files
to the GSFSGroup Data Exchange are:

-   WinSCP – an SFTP client software used for secure file transfer

-   GPG4Win – an encryption client program used for encrypting, signing and
    decrypting files

-   PowerShell – a tool used to generate SHA-256 hash values to ensure file
    integrity

These programs, or the equivalents you choose, are required to be installed on
your computer. Downloads can be found at the following links. Follow the install
instructions on their download pages.

>   WinSCP - <https://winscp.net/eng/download.php>

>   GPG4Win - <https://www.gpg4win.org/get-gpg4win.html>

Note: PowerShell is a program that is already included on Windows computers so
there is no need to download any software.

Partners on Mac or Linux also have a variety of software encryption tools
available to them. The remainder of this document will illustrate using software
running on Windows, but the techniques illustrated generally remain the same for
Linux and Mac environments.

WinSCP installs tools that work in conjunction together. These tools will be
referred to throughout this document. Kleopatra, a certificate store manager,
and PuttyGen, an SSH key generation tool are both installed as companion tools
to WinSCP.

Create an SSH authentication key pair
-------------------------------------

GSFSGroup Data Exchange partners are required to have an RSA based SSH key pair
to authenticate to their GSFSGroup SFTP server. In addition, the public key of
this key pair must be sent back to the GSFSGroup Administrator in order to grant
partner access to the GSFSGroup SFTP server.

Instructions for creating SSH key pairs, can be found in the “[How to create a
key pair for encryption and
authentication](#how-to-create-ssh-and-pgp-key-pairs-for-encryption-and-authentication)”
section below.

Create a PGP key pair
---------------------

GSFSGroup Data Exchange partners are also required to have an RSA based PGP key
pair to decrypt files sent by the GSFSGroup Data Exchange and to sign files sent
to the GSFSGroup Data Exchange.

Instructions for creating PGP key pairs, can be found in the “[How to create a
key pair for encryption and
authentication](#how-to-create-ssh-and-pgp-key-pairs-for-encryption-and-authentication)”
section below.

Important! As of this writing, files sent by the GSFSGroup Data Exchange to a
Partner are not encrypted in the latest version of the GSFSGroup Data Exchange.

Email your public keys to GSFSGroup
-----------------------------------

Once you’ve created the SSH and PGP required key pairs as instructed
[below](#how-to-create-ssh-and-pgp-key-pairs-for-encryption-and-authentication),
you must email the GSFSGroup Data Exchange public keys back to the GSFSGroup
Data Exchange Administrator. Refer to section “[How to export public
keys](#how-to-export-public-keys)” for instructions.

Start sending files securely
----------------------------

Once access to the GSFSGroup Data Exchange has been granted, key pairs are
created, public keys are exchanged, and a partner can begin sending data. The
GSFSGroup Data Exchange is capable of processing csv formatted files delimited
by a value chosen by the partner. A manifest file must always accompany a data
file for each file transfer session.

Sending data files to the GSFSGroup Data Exchange
=================================================

The process for sending data is always the same:

-   Complete setup steps in section “[Before you begin](#before-you-begin)”

-   [Have a data file ready](#have-a-data-file-ready)

-   [Compute a hash value from the data
    file](#compute-hash-value-on-the-data-file)

-   [Encrypt the data file](#encrypt-the-data-file)

-   [Prepare the manifest](#prepare-a-manifest-file)

-   [Connect to the GSFSGroup Data
    Exchange](#connect-to-the-gsfsgroup-data-exchange-sftp-server)

-   [Securely transfer both data file and manifest file to the GSFSGroup Data
    Exchange](#securely-transfer-data-and-manifest-files)

-   Receive email notification after processing and take the appropriate action

Have a data file ready
----------------------

Currently, the GSFSGroup Data Exchange supports processing data files in csv
structured format. The data file header information is negotiated between the
partner and GSFSGroup.

The requirements to successfully send and process a csv file in the GSFSGroup
Data Exchange are as follows:

-   Utf-8 encoded delimited csv file

-   Conform to the csv header negotiated between GSFSGroup and the partner

-   A file hash must be computed on the data file prior to encrypting

-   The data file must be encrypted with the GSFSGroup provided pubic key

Further information on creating a hash can be found in section “[Compute hash
value on the data file”](#compute-hash-value-on-the-data-file)

Further information on encrypting a data file can be found in section “[Encrypt
the data file](#encrypt-the-data-file)”

Alert! Data files must have a .csv extension

Compute hash value on the data file
-----------------------------------

A SHA-256(consistent capitalization) hash must be generated for each data file.
This hash must be performed on an unencrypted data file. There are a variety of
tools that can create SHA-256 hash values. For windows, PowerShell can be
utilized. To create a SHA-256 hash value in PowerShell, perform the following
steps:

1.  Open PowerShell

2.  Change directory to the folder where the data file is

3.  Enter the command Get-Filehash {the name of the data file}

Save this hash value. It will be copied and pasted into the manifest file in the
FileHash column. This hash will be used by the GSFSGroup Data Exchange to verify
the integrity of the data file being sent.

Encrypt the data file
---------------------

Instructions on how to encrypt a file can be found in section “[How to encrypt
and sign a file](#encrypt-the-data-file)”.

Prepare a manifest file
-----------------------

The manifest is used to name the data file being sent, ensure the integrity of
the file, and provide contact information for email notifications. It is created
by the partner for every data file sent to the GSFSGroup Data Exchange. Once
created, this manifest file can be reused, substituting new information when new
data becomes available to send to the GSFSGroup Data Exchange.

The manifest contains a header on the first row and the header values on the
second values row.

**Required header fields in the manifest file are as follows:**

-   CreationTime: The date and time this dataset was generated by the partner,
    formatted as mm/d/yyyy HH:MM.

-   FileName: The file name of the data set being sent by the partner

-   FileHash: A SHA-256 strength encrypted hash value for this data file used
    for integrity checking (refer to section “[Compute hash value on data
    file](#compute-hash-value-on-the-data-file)” for help)

-   RowCount: The number of rows in the data file sent by the partner including
    the header row.

-   Delimiter: The character used to delimit this file’s csv data, if blank, a
    comma delimiter is assumed

-   IdentityCol: The primary key column name of the data file. Leave empty if
    there isn’t an identity column

-   ContactEmail: The partner’s preferred email address that provides data
    support to GSFSGroup

-   ErrorEmails: The partner’s preferred email address for the receiving of
    error messages sent by the GSFSGroup Data Exchange if and when errors occur
    during processing

-   ReceiptEmails: The partner’s preferred email address for the receiving of
    receipt messages sent by the GSFSGroup Data Exchange. Receipt messages
    describe the successful result of processing the file into the GSFSGroup
    Data Exchange. If any errors occurred during processing, the file will
    describe the error and error row.

**Partners can use the following example to create their manifests, substituting
their own information on the values row:**

CreationTime,FileName,FileHash,RowCount,Delimiter,IdentityCol,ContactEmail,ErrorEmails,ReceiptEmails

8/4/2020 16:30, TriPAC_New_Claims_File.csv,
2139afab18a709503fbf7705377cce01427e3ce2829c6c475a3e3f60e056bad9,537,",",Claim_No,contact\@test.com,error\@test.com,receipt\@test.com

 

Important: Manifest file names sent to the GSFSGroup Data Exchange must have a
.manifest extension.

Connect to the GSFSGroup Data Exchange SFTP server
--------------------------------------------------

An SFTP client must be used to securely connect and transfer files to and from
the GSFSGroup Data Exchange. Once an SFTP client is installed, a connection to
the GSFSGroup Data Exchange can be made after the following prerequisites are
complete:

**Prerequisites**

-   A partner must create their SSH key pair for SFTP authentication. To create
    SSH keys for SFTP authentication, review the section ‘[Creating SSH Keys on
    Windows](#create-ssh-keys-on-windows)’.

-   The partner must email the public key of their SSH authentication key pair
    to their GSFSGroup Data Exchange Administrator.

-   A GSFSGroup Data Exchange Administrator emails the partner to confirm access
    has been granted. This confirmation email contains the SFTP host to connect
    to, a public key for encrypting data files, and a GSFSGroup Data Exchange
    user name. A password is not necessary since the partner is connecting using
    their SSH key pair.

**The following example shows how to connect to the GSFSGroup Data Exchange
using Windows WinSCP.**

For the buttons/actions listed below, can we call them out in either italic or
bold? I’ll leave the choice up to you.

1.  Open WinSCP.

2.  You are presented with two panels. The left panel is your local directory,
    the right panel is the remote GSFSGroup Data Exchange directory.

3.  Click on the New Session tab

4.  In the popup Login window, click Advanced

5.  In the popup Advanced Site Settings window, click the Authentication menu
    item under the SSH menu item.

6.  In the Authentication dialog, click the directory button and select the
    private SSH key, click ok

7.  In the Host Name text box, paste the host name given by the GSFSGroup Data
    Exchange Administrator

8.  In the User Name Text box, paste the user name given by the GSFSGroup Data
    Exchange Administrator

9.  Leave the password blank

10. Enter an SSH passphrase if your SSH key contains a passphrase

If successful, the right panel will show the root folder of the GSFSGroup Data
Exchange, ready to accept file transfers.

Securely transfer data and manifest files
-----------------------------------------

**Use the following instruction to send files through Windows WinSCP.**

1.  Open WinSCP

2.  Connect to the GSFSGroup Data Exchange (see the “[Connect to the GSFSGroup
    Data Exchange SFTP
    server](#connect-to-the-gsfsgroup-data-exchange-sftp-server)” section)

3.  Once you are connected to the GSFSGroup Data Exchange SFTP server, you will
    see content of the default remote directory on remote file panel.

4.  On the remote panel you should see no files and a directory labeled outbound

5.  Drag the data file and manifest files from the left panel to the default
    directory shown on the remote panel.

Your files have been sent and are being processed by the GSFSGroup Data
Exchange.

Receiving files from the GSFSGroup Data Exchange
================================================

The GSFSGroup Data Exchange provides feedback after every data file it receives
and processes. This feedback is in the form of a receipt file and possibly an
error file, if an error occurred during processing. These files are deposited
after every data file you send to the GSFSGroup Data Exchange in a folder
labeled ‘outbound’.

You will receive an email notification with the names of the files ready to
retrieve and examine when the GSFSGroup Data Exchange completes processing of
the data file. This email will also notify you of success or failure of
processing. A text editor is sufficient to read these files.

The receipt file
----------------

When the GSFSGroup Data Exchange completes processing a data file, the GSFSGroup
Data Exchange generates a receipt file in a folder named *outbound*. A receipt
file is generated every time data is sent to the GSFSGroup Data Exchange. The
receipt file is a csv file is composed of the following information:

*File Name* - The name of the data file that was processed

*File Hash* – A SHA 256 hash of the data file

*Imported At* – The date and time the data file was successfully imported

*Row Count* – The number of rows processed

*Error Count* – The number of errors encountered, if any

*Error File Name* – The name of the error file deposited in the outbound folder

*Error File Hash* – The SHA-256 hash value of the error file (currently the
GSFSGroup Data Exchange is not encrypting error files)

If an error occurred during the processing of a data file, you’ll want to
download the error file, make corrections to the data file according to the
errors noted and resend the data file following the steps in section “[Sending
Data files to the GSFSGroup Data
Exchange](#sending-data-files-to-the-gsfsgroup-data-exchange)”

The error file
--------------

When the GSFSGroup Data Exchange encounters an error during processing a data
file, the GSFSGroup Data Exchange generates an error file in a folder named
*outbound*. This csv file is composed of the following information:

*Row* – The row that caused the error during data processing

*Column* – The column that caused an error during data processing

*Message* – The error message

Use the messages in this error file to make corrections to the data file and
resubmit.

How to create SSH and PGP key pairs for encryption and authentication
=====================================================================

How to create an SSH key pair for authentication
------------------------------------------------

### Create SSH keys on Windows

On Windows, partners can use WinSCP and its installed companion software
PuttyGen to create an SSH key pair. 2048 bit RSA encryption is the minimum
encryption strength allowed by the GSFSGroup Data Exchange. The keys should
preferably be passphrase protected.

To create an SSH key pair to authenticate to the GSFSGroup Data Exchange, do the
following:

For the buttons/actions listed below, can we call them out in either italic or
bold? I’ll leave the choice up to you.

1.  Open WinSCP using the Windows Start menu

2.  Click the New Session tab

![](media/7658d6b1b905bee9b94ccdf87e519c38.png)

1.  Click on the Tools drop down at the lower left of the Login popup window

    ![](media/afc4045ebf19efcb0a0f981141919671.png)

2.  Click Run PuttyGen

3.  In the Actions section, *click the Generate button*. Continually move the
    mouse to initialize and complete the SSH generation  
    

    ![](media/9f33973ed4419975ec64236cfa717b23.png)

4.  Type in a passphrase and confirm it in the Confirm passphrase text box

    ![](media/ca95f3852f808d43d0fca6c5b3cceaed.png)

5.  Save the private key to your computer by *clicking the ‘Save private key’
    button*

You have now generated an SSH key pair. The key pair is stored in a .ppk file.
The public key of this key pair will be used to authenticate your session to
Data Exchange and must be sent to the GSFSGroup Data Exchange Administrator. To
export the public key see section “[Exporting the SSH Authentication public
key](#exporting-the-ssh-authentication-public-key)”

Alert! Place your private key in a secure location on your computer and never
Share it.

How to create a PGP Key Pair for encryption
-------------------------------------------

PGP key pairs are required so that Partners may communicate securely with the
GSFS Data Exchange. In this system, the Partner has a pair of keys consisting of
a private key and a public key. A Partner’s private key is kept secret; never
revealed. The public key is given to the GSFSGroup.

### Create a PGP key pair on Windows

1.  Ensure that GPG4win is installed on your system

2.  Open Kleopatra using the Windows start menu, which is installed by the
    GPG4Win installation program

3.  *Click File*, then click New Key Pair

4.  *Click Create* Personal OpenPGP key pair

5.  *Enter Name* and Email

6.  *Click Create* to confirm parameters

7.  Enter a passphrase for the key pair

How to export public keys
=========================

Because both the partner and GSFSGroup encrypt and decrypt files, each party
must exchange their public keys with the other party. The public keys should be
sent through email to the GSFSGroup Data Exchange Administrator. Do not send
private keys.

Exporting the SSH Authentication public key
-------------------------------------------

Authenticating to the GSFSGroup Data Exchange requires that you export the SSH
public key you created during creation of your SSH key pair. Once exported, the
file is attached to an email and sent to the GSFSGroup Data Exchange
Administrator. You must have already created your SSH key pair to proceed. To do
this using the WinSCP Windows program, do the following:

For the buttons/actions listed below, can we call them out in either italic or
bold? I’ll leave the choice up to you.

1.  Open the WinSCP tool

2.  Click on the New Session tab

3.  Click on the Tools drop down in the lower left of the Login popup window
    (you are not going to log in)

4.  Click the Run PuttyGen menu item, PuttyGen will launch

5.  Click on the Load button

6.  Find your SSH private key to load it into PuttyGen

7.  Click on Save Public key

8.  Choose a folder to save the public key

9.  Name the file {partner}-ssh-public.key, substitute {partner} with your
    organization’s name

Exporting the PGP public key
----------------------------

So that GSFSGroup can decrypt messages sent by the partner, the partner must
send their PGP public key to the GSFSGroup Data Exchange Administrator. You must
have already created you PGP key pair to proceed. To do this using the GPG4Win
Windows program, do the following:

For the buttons/actions listed below, can we call them out in either italic or
bold? I’ll leave the choice up to you.

1.  Open Kleopatra as installed by the GPG4Win program

2.  Find the partners certificate used to sign and decrypt data files for the
    GSFSGroup Data Exchange and highlight the certificate

3.  Click the Export button on the Ribbon

4.  Export the file to a directory on the local computer

5.  Name the file {partner}-pgp-public.key substitute {partner} with your
    organizations name

Both public key files should be emailed to the GSFSGroup Data Exchange
Administrator

How to import a public key
==========================

So that a partner can encrypt messages sent to the GSFSGroup Data Exchange, they
must import the GSFSGroup PGP public key sent by the GSFSGroup Data Exchange
Administrator. To import the PGP public key using GPG4Win Windows program, do
the following:

Prerequisites: A PGP key pair must be present in Kleopatra’s list of
certificates

1.  If not done so, detach the public key sent by the GSFSGroup Data Exchange
    Administrator to your computer

2.  Open the Kleopatra certificate manager as installed by GPG4Win

3.  Select *Import* from the Ribbon

4.  Select the public key file detached from step 1

5.  Enter a private key passphrase if prompted (do not forget this passphrase)

6.  Continue through the dialogs to certify with your private PGP key

7.  *Click Yes* to begin the verification sequence

8.  In the Certify With drop down, select your certificate (not GSFSGroup
    certificate)

9.  *Click Certify*

Note: In order to mark the imported key as trusted/verified, Kleopatra will
guide you to start process of certification.

You are now ready to encrypt files to send to the GSFSGroup Data Exchange.

How to encrypt and sign a file
==============================

Keys are required to sign and encrypt data files sent to the GSFSGroup Data
Exchange using the PGP encryption protocol. The partner private key is used to
sign files, and the GSFSGroup public key is used to encrypt files sent to the
GSFSGroup Data Exchange.

Partners will perform this encryption with a GSFSGroup provided public key file
to encrypt data files that partners send to the GSFSGroup Data Exchange and sign
public keys provided by GSFS. (This sentence does not read clearly to me,
consider rewording.)

A GSFSGroup Data Exchange Administrator will have emailed a confirmation of
access along with a GSFSGroup public key, which can be used to encrypt files
destined for the GSFSGroup Data Exchange. A partner will have sent both their
public SSH key and PGP key to the GSFSGroup Data Exchange Administrator.

Important! The signature fingerprint on the file sent to the GSFSGroup Data
Exchange must match the fingerprint stored in the PGP public key sent by our
partners to GSFSGroup, or the GSFSGroup Data Exchange will not process the data.

Prerequisites
-------------

-   The GPG4Win client program is installed on your Windows system

-   A public key provided by a GSFSGroup Data Exchange Administrator to encrypt
    files sent to the GSFSGroup Data Exchange

-   A PGP private key to sign a data file

To manually encrypt, sign a data file, and send to the GSFSGroup Data Exchange
perform the following steps:

For the buttons/actions listed below, can we call them out in either italic or
bold? I’ll leave the choice up to you.

1.  Ensure the GPG4Win encryption client is installed on your system

2.  Ensure you have generated a PGP key pair

3.  Open Kleopatra, which is installed by the gpg4win installation program

4.  Find the file to be encrypted in Windows File Explorer, right click it and
    select the Sign and Encrypt menu item.

5.  Click the people icon in the field labeled “Please enter the name or email
    address”

6.  Select The GSFSGroup Data Exchange Admin from the list

7.  Name the file with a .csv extension

The file is now signed and encrypted.

Note: The file name must be labeled with a .csv extension or it won’t be
accepted by GSFSGroup Data Exchange

How to decrypt and validate a file's signature
==============================================

GSFSGroup Data Exchange uses the partner PGP public key to encrypt error files.
Error files are encrypted since they contain partner sensitive data and are
created by GSFSGroup Data Exchange in the unlikely event a signature fails to
validate. GSFSGroup will also sign the error file.

Error files should be decrypted by the partner, using the Kleopatra PGP tool.
Signature verification happens automatically within the tool and will warn you
if a signature cannot be verified.

In the unlikely event a signature is compromised, email your GSFSGroup Data
Exchange Administrator immediately.

Note: As of this writing, error files are not encrypted in the latest version of
GSFSGroup Data Exchange.

Prerequisites

-   A PGP key pair should be created and listed in Kleopatra’s certificate list

-   The GSFSGroup provided public key should be listed in Kleopatra’s
    certificate list

**To decrypt an error file:**

For the buttons/actions listed below, can we call them out in either italic or
bold? I’ll leave the choice up to you.

1.  Open Kleopatra as installed by the GPG4Win program

2.  Click on the Decrypt/Verify Ribbon button

3.  Select the encrypted error file received from GSFSGroup Data Exchange

The decrypted file will be available in the same directory it was selected from.

Frequently Asked Questions 
===========================

Coming Soon

Troubleshooting
===============

Coming Soon

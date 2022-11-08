---
title: "Tracking New Customers"
date: 2022-11-08T08:24:11-07:00
draft: false
---

* Profile - allows you to statically or dynamically define Read statements against a table or stored proceedure output.
* Link Element - an optional field that specifies the common database field in a record group to batch documents, usually the primary key.
* Batch count - defines an interval for the grouping behaviour.
* Max rows - limits the maximum number of frows returned in a single read.

## Salesforce Write Actions
* Create - creates new records in SF object defined in Create operation.  For each document supplied to the operation, an internal 'ID' field is produced automatically.
* Update - updates an existing SF recor in the update operatin.  To edit an existing object record, include the internal 'ID' field in the request.
* Upsert - makes "insert-new-or-update-existing" simple.  Performs an upsert requst and let SF decide whether to insert or update the data.
* Delete - removes a record from the SF object specified in the Delete operation.  To delete existing, you must include the internal 'id' field.

## Configure Salesforce Write Operation
* Request profile - the structure of the SF object being updated.  Created by an import.
* Batch count - specifies the number of documents to send in one SF request.  Use for high-volume processing and system migrations.  By default, AtomSphere batches 200 transactions to commit against the SF API in one write request.
* Return Application Error Responses - returns the xml responses used in later process steps.  This option allows for custom error logging vs directly failing and stopping the document flow.

## Why Use a Connector Call?
* Perform cross-reference lookups
* Obtain supplemental data
* Make a document-level queries on the fly.
* Has a negative performance implication and should be used as last resort.
* If multiple mappings or logic require the same Connector Call, consider using Dynamic Document Properties or Document Caching at the front end of the process.
* Steps:
1. Identify and configure all object query operations before building your full integration solution.
2. Add a Connector Call in logic shapes or map functions to make document-level queries immediately. 
3. You can enable caching, a default option in the Map function, to limit API requests for common input records. This will cache the query result to reuse instead of making many queries for the same information.
4. Finally, if many maps or logic need the same Connector Call, think about using Dynamic Document Properties or Document Caching at the front-end of the Process.

## Mail Connector
When the Mail connector is configured correctly in your process, your Boomi Integration can retrieve files from or send files to virtually any email server.  

### Email Connector Requirements
* A server with the appropriate permissions to access POP/SMTP
* The Atom's static IP address open in the firewall configuration
* An additional port if you are using a Transport Layer Security (TLS) or Secure Sockets Layer (SSL) protocol
* An application password when using two-factor authentication (2FA, or multi-factor authentication) to access your account (for example, Outlook, Gmail, etc.)

### Mail Connnection
* Host - host ip address or domain name of the mail server
* Port - command port on the mail server.  Used for listening for incoming connections from mail clients.  Default port for sending is 25 and receiving is 10
* Use TLS - enables Transport Layer Security protocol.  It encrypts all data exchanged between AtomSphere and the server with digital security certificate.
* Use SSL - uses Secure Sockets Layer to manually import the certificate into the Java Keystore.  encrypts all data exhanged between AtomSphere and the server with a digital security certificate.
* User / Password Authorization - checking means you must supply the login credentials.
* User Name - user name of account on mail server
* Password - password of account on the mail server
* Host - ip address or domain name of the mail server.  Host is where mail application resides and the mail connector receives or send files to the mail server.

### Mail Operation
* From - the input for the from field defaults to the connection user and is usually overwritten.
* To - address of person receiving the email.  No limit to number of email addresses that can be used to send.  Must be separated by ";".
* Subject - contains the email subject and con contain static and dynamic content.
* Disposition - defines if the document should go in the body of the email (inline) or as an attachment.
* Content type - identifies the email file format and selected from thje drop-down.  Valid options are text plain, html or xml, and application biary, edifact, edi-x12 or xml.
* All fields listed in the Mail Operation Options can contain static or dynamic values.  Dynamic values are defined using a Set Properties Shape.

## Understanding the Message Shape
The Message shape generates a free-flow text message from a dynamic or static set of input parameters.

* Uses:
    * Create highly customized emails
    * Send confirmation messages
    * Produce a new document to send through the process
* Varaibles - can insert one or more variables into placeholders defined in the message text.
* Displayu name - user-defined to describe the shape.  If not entered the word Message appears.
* Option - combine documents into a single message.  Check if a document is split during processing.  It will combine the multiple resulting messages into a single message before processing.  Boomi recommends using this option when sending email alerts to reduce the anumb of emails.
* Message - contains the free-flow textd message to be generated.  You can specify variables here by creating placeholders with 1: {<param number>} - for example, {1}

## Program Command Shape
Enables database and system -level commands to be executed as part of the process flow.

* Three command types:
    * SQL statements
    * Stored proceedures
    * System command
* Due to security reasons, you cannot utilize the Program Command shape in processes deployed to the Boomi Atom Cloud.
* Why use program commadn shape:
    * Speed
    * Multiple uses
* Program command Shape for SQL Statements
    * Variables - provide one or more values to insert into a command
    * Display name - optional, user-defined, name to describe the shape.  Appears alongside the label determined by how you set the Type field
    * Type - determines the tpye of program command
        * sql - execute a database sql action
        * stored procedure - execute a database stored procedure that does not return data to the process flow
        * system command - execute command-line programs that require no interaction
    * Run once per execution - if checked, prevents repeated executions of the defined command with multiple documents.  Execute only in scenarios where you do not need to reference inbound document data.
    * Connection - use to choose existing database connection components or create a new one againsta with to execute SQL statements or stored procedures.
    * SQL - SQL statement to execute.  May use placeholders ("?") for variables.
    * Edit SQL - select this opens up a sQL editor
    * The Program Command shape cannot be used with a SQL SELECT statement because you can not return documents to the Process flow using it. 
* Other Types of Program Command Shapes
    * Stored Procedures
    * System Command
* The Program Command shape does not return documents to the Process flow and is used for actions like Write and Send.  After the command is complete, the destination document is passed on. In the event of an error, the process stops and logs an error.
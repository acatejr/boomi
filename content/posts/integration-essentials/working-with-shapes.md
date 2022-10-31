---
title: "Working With Shapes"
date: 2022-10-31T09:07:39-07:00
draft: true
---

Shapes
------
* Steps linked together to form the business logic for a process
* Start shape is automatically added to a new processes
* Start shape cannot be removed
* There are 4 start shape types:
    * Connector - gets data into the process using an application or technology connectors
    * Trading partner - gets data into process for a specific trading partner and handles common EDI doc standarts like X12 or EDIFACT
    * Data passthrough - gets data into process from a parent or another external source
    * No data - process does not receive data from a source, but a single, empty document goes through the process flow
* Display name - if not entered, name of the selected shape appears on the shape

Process Structure and Design  
----------------------------  
* Connector shape get data into or send data out of the process
* Connectors contain all information needed to connect to a data source or applicication.
* connectors have two parts: Connection and Operation
    * Connection - physical connection information
    * Operation - function to call or file(s) to act upon (the how)  
* Connector Types:  
    * Technology connectors - internal systems components that provide codeless connection to and from touchpoint systems using various prototols like Disk V2, Database, Http Client, and SFTP  
* Application Connectors - refer to packaged integration services containing a branded AtomSphere connector built through the Boomi connector
* Custom Connectors - you can develop, deploy, and publish custom connectors.  Custtom connectors take advantage of Boomi Connector API using Connector SDK

Understanding the FTP V2 Connector
----------------------------------
* Use this connector to download or upload files to an FTP-enabled server
* Opens a data connection session with an FTP server
* The connection contains info to log in to the ftp server
* The operation defines how to interact with the ftp server
* FTP V2 Actions:
    * Create - creates files on the ftp server or updates files
    * Query - downloads files from the ftp server
    * Delete - deletes files from an ftp server
    * Get - retrieves a single file from an ftp server
* Disk V2 Actions
    * Create - generates new files if they do not already exist and returns new ID of the inserted object
    * Delete - removes the file from the directory.  The ID specifies the record to delete
    * Get - retrieves objects that match the input filename ID
    * List - retrieves files within a directory
    * Listen - waites for and retrieves files from a given directory on the disk in the underlying file system
    * Query - reads a set of files within a directory based on search criteria
* Set Properites Shape
    * Properties to set are connected to a specific property (e.g., static file name)
    * Parameters define the value of the given property.  Allow you to add multiple parameter values to concatentate a more complex value with dynamic content
 * Choose Property Dialog
    * Property type - contains desired property type.  Valid operations are document property, dynamic document property, dynamic process property, MIME, and process property
    * Source type - contains the source defining the document properties.  You select a specific connector and its associate properties
    * Connectors - contains the connector defining your property
    * Property - the property setting the parameters
    
---
title: "Understanding Different Connector Types"
date: 2022-11-01T09:43:05-07:00
draft: false
---

Connectors are the main component that *contain all the information* needed to connect to a data source or application.

Why Use Connectors?
-------------------
* Simplifies application support:
    * Automatically updates to new versions
    * Protects data access using different authentication types
    * Automatically discovers the recently supported objects in the application API
* Supports advanced options to fine-tune behaviour
    * Highly configurable
    * Allows configuration, based on use case
    * Advanced options allow for additional specification
* Built-in data manipulation
    * Automatically pages through large data sets and retrieves the entire data set from the API
    * Optimizes data transfer and efficiency by splitting large files into smaller chunks
    * Supports batches to improve efficiency and performance
* Real-time support
    * Provides listener support
    * Provides real-time data validation and integration, including communication with trading partners
* Connector Types:
    * Application - targeted at one specific application
    * Technology - implement a specific protocol
    * Event-driving - a hybrid of application and technology used in event or message-driven scenarios
    * Custom - You can develop, deploy, and publish custom connectors by leveraging the Boomi Connector API using the Connector SDK and its companion SDK Javadocs

Configuring a Salesfroce Read Connector
----------------------------------------
The Salesforce read connector retrieves information from a Salesforce account

* Why Use a Salesforce Connector:
    * Provides Connectivity protocols to any native Salesforce application.
    * You can configure it with filters to limit the results returned.
    * Can read related objects (children and/or parent processes) in the same operation
    * Can sort results

* The SF connector is made up of the connection and the operation:
    * The connection is where you provide the information for the SF account you are connecting to
    * The operation is where you provide the information that tells AtomSphere how to retrieve the data from Salesforce

* Process shapes and components use parameters for dynamic configuration. Parameter values can represent data from a document field, current system date/time, static value, result of a connector call or database query,
or a variety of other values

* Why Use Parameters?
    * The provide the ability to dynamicallly pass values into numerouse shapes
    * Cross reference lookup - retrieves value from a cross reference table component given one or more inputs
    * Date/Time - allows you to choose date/time value
    * Dynamic process property - use this param type to retrieve the value of a dynamic process property.  Be sure the name matches th enaove of the property used whent it was created
    * Process property - used to retrieve the value of a process property.  Be sure name matches the name used when setting the property
    * Sequential value - used to create and reference a counter to automatically increment with every execution
    * Static - containts a hard-coded value
    * Unique value - system generated number to guarantee uniqueness

Configuring a Database Write Connector
--------------------------------------
The database write connector *updates and deletes information* in a database table.

* Why use a database connector?
    * Stores database connection details in one location
    * Uses a single interface to connect with an Java Database Connectivity (JDBC) relational database.  A few databases in the Connection tab's Drive Type drop-down have pre-loaded (packaged) JDBC drivers.
    * Allows you to run diverse SQL operations on your database, including select, insert, update, delete and stored procedures
    * Has two kinds of commit options:
        * Commit by number of rows
        * Commit by profile

Configuring Standard and User-Defined Map Functions
---------------------------------------------------
Map functions transform logic applied to individual field values hwen mapping and perform tasks such as converting a character to uppercase or changing the date format in the map.

* Why use a Map Function?
    * Less coding
    * Reduces the number of map components available in the design to apply multiple standard functions to transform a single target value
    *  Provides the ability to apply complex logic using a combination of the standard function to achieve a single data that comply with the target data
* Types of Map Functions
    * Standard - performs single step, like converting value to uppercase or performing mathematical operation
    * User Defined - let's you linke multiple standard functions together.  Example, could get current date in one step, format it in second step. Can reuse these functions.

* Get Document Property is part of Propoerties Map Function

Understanding the Decision Shape
--------------------------------
The Decision shape routes documents based on a True/False comparison of two values.  True documents are processed before False documents.

* Uses of Decisions Shape
    * Check the existence of a record in the destination system to determine what to do next
    * Check the existence of value in a given profile element
    * Check for a specific value
* Try to phrase a question in the shape's display name
* Null values from a profile element or connector call are treated as empty strings (' ') for comparison. To compare against a null value in the inbound data, the Second Value field’s Static Value setting in the Decision shape should be left empty
* Decision shape psrocesses true documents before false

Understanding the Stop Shape
----------------------------
The Stop shape terminates the data flow in a process path. It represents a successful conclusion and does not generate an error message.

* Why use a Stop Shape?
    * It is a Boomi recommended practice
    * It intentionally signifies the end of a processing path

Advanced Testing Techniques in Test Mode
----------------------------------------
When developing new processes, Test Mode is an important debugging tool. It allows you to update and debug your process quickly.


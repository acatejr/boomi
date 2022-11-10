---
title: "Manage and Schedule Processes"
date: 2022-11-09T08:58:36-07:00
draft: false
---

When an AtomSphere process is created, you can run it manually or on a schedule.

## Steps to Run a Process
* Build - design and build using visual ide
* Package - package the component from the Build page or Deploy menu
* Deploy - deploy packaged components to environments from the deploy menu
* Manage - the boomi centralized architecture enables management of all integrations from the platform
## How does Process Deployment work?
build -> pacakge -> deploy -> manage
## Test Mode
* 100 file limit per inbound connector shape
* Maximum total data = 10 MB
* Does not support:
    * Real-time triggering
    * Listener processes
    * Parallel processing in the Flow Control shape
* Does not execute auto-tries in the Try Catch shape
## Deploy
Deployed components support strategic monitoring and unlimited data
* Execution and documents histroy searching
* External Alerting - Email and RSS
* Deployed connections towards account licenses
* Can deploy a pacakaged component to multiple environments
## Environments
An environment is a dedicated deployment are used to support the different phases of the development life cycle.
* Test envrionment used to test a process
* Production environment uses live connections and real-timne data
* Both Environments
    * Managed in Atom Management
    * Unlimited environmewnts
    * An Atom can be assigned to only one environment at a time
    * An environment can contain many atoms
    * A single environment can host multiple deployed processes
## Process Deploy vs Execute
* Process scheduling - like an airplane on a runway.  Ready for take off but waiting for OK.
* 3 ways to execute after process is deplyed:
    * Manual execution
    * Scheduled execution
    * Event Driven execution
## Understanding License Management
AtomSphere tracks the number of production and test connections you've purchased for your account. It also tracks the number of connections deployed in production and test environments.

* Environment Classifications
    * Production
        * Uses production connectors
        * Uses Production license
    * Test
        * Uses Test Connectors
        * Uses Test License
* Deployed connection - connection components built into the deployed processes
* Difference between Production and Test connections?
    * Test connections have (Test) after their connector class name
    * Production connections do not have a designation after their connection class name
* Connector Class
Boomi connects to over 1,500 applications using our catalog of over 100 Boomi-supported connectors. Connection licenses are categorized and provisioned by connector classes: Small Business, Standard, Enterprise, and Trading Partner.

AtomSphere performs an audit during deployment to ensure the allowed connection number is available.  If no licenses are available, an error message will appear stating that your deployment was refused.
Based on the document size and record number constraints, you can still execute the process in the Build tab.

* Connectors without Impact
    * AS2 Shared Server
    * Atom Queue
    * AtomSphere API
    * AtomSphere Partner API
    * Flow Services Server
    * MDM
    * MDM Listener
    * MLLP Server
    * Web Services Server

* How are licenes counted?
Connectxions are managed at the Atom level and double for each process-to-Atom deployment
* Optimum Connection Liscene Usage Recommendations:
    * Reuse existing connections - Instead of creating new connections, reuse existing ones to reduce confusion, simplify maintenance, and reduce connection usage.
    * Organize and consolidate connections in a common folder - Put all connection components in a single folder on the Build page, similar to our #Connections folder, and restrict access to the folder to administrators or super-users. As part of your deployment method, confirm that only connections in the #Connections folder are referenced in your to-be-deployed process.  To ensure no other connections are accidentally introduced, use Compare Deployment to compare the components in the deployed process version to previously deployed versions.
    * Use environment extensions whenever possible - Instead of creating separate connections for each Environment, use Environment extensions.
    * Optional - create separate connections on the build page - We may require different connections on the Build page, which needs to directly configure connections rather than extensions. Create a new connection and replace it with the #Connections folder before deploying. To avoid confusion, use a naming convention such as Database ABC DEV - DO NOT DEPLOY.
* Connections that allow you to change the connection field with Document Properties:
    * Disk
    * FTP
    * HTTP Client

---
title: "Understanding Deployment"
date: 2022-10-31T15:07:24-07:00
draft: true
---
Documents are packaged and deployed using a specific workflow.

Deployment is how you prepare your processes and deployable components to run and operate in a Test or Production Environment
* Build --> Create Packaged Components --> Deploy the Package
* Build - a developer builds a process or deployable component on the process canvas
* Create Packaged Components - A developer or administrator creates a component version by creating a Packaged Component from the Build or Packaged Component page
* Deploy the package - An administrator deploys the packaged component to one or more Environments from the Packaged Component or Deployments page
* Why deploy a process?
    * Control specific versions - Deployment controls specific versions in different runtime Environments as part of the development life cycle (for example, Test vs. Production)
    * Manages versioning - Deployment manages process and other deployable component versioning
    * Isolates the process version - Deployment isolates the version of processes running in runtime Environments from ongoing changes made in the Build tab
    * Complete audit history - Deployment provides a complete audit history for versioning

Defining Packaged Components
----------------------------
When you create a packaged component or process, you take a snapshot of its development on the build tab. You typically do this when you are done building and are ready to deploy to your Environment.

* Why Create a Packaged Component?
    * Ability to assign a single version number - Packaged Components let users assign a single version number to be tracked and referenced throughout various deployments
    * Greater control - Packaged Components provide greater control over the life cycle and distribution of your processes and components. Creating a Packaged Component with a unique version allows you to keep track of where you use each version
* Version Check-In
    * You can specify the version or let AtomSphere do it
    * The version does not change each time you deploy a packaged component
    * Your version stays with the packaged component no matter where you deploy
    * Version names are alpha-numeric
    * You do create a new version number for each packaged component
    * A version is not just numeric, can be alphanumeric

Defining Deployment
-------------------
Deployment is how you prepare your processes and components to run and operate in a Test or Production Environment
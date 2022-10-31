---
title: "Mapping"
date: 2022-10-31T14:52:20-07:00
draft: false
---

Mapping shows how elements in the source profile correspond with those in the destination profile.

Mapping Methods
---------------
* Manual - you click and drag source profile elements to the corresponding destination profile element
* Boomi Suggest Wizard - Boomi makes mapping suggestions based on thousands of mappings loggged by the Boomi community
* Mapping Considerations ![Mapping Considerations](/static/mapping.considerations.png)

Setting a Default Value
-----------------------
* AtomSphere assigns a default value to a dest. profile element when no value exists in source
* Need to create a defualt value if destination profile requires a field value that is not contained in the source profile
* Ways that maps use default values:
    * Source profiles
        * Element is null
        * Elemet is blank
    * Destination profiles
        * Element is null
        * Elemet is blank
* When you map a source element to a destination element with a default value the default value is not used

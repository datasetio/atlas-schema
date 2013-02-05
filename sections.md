---
layout: base
title: Atlas Schema / Sections
---

## Sections

An Atlas Schema is divided into a number of basic sections,  these sections are in place to allow us to capture different information regarding both the model we are building but also meta-data around that model that is useful when a person wants to consume then model.  Lets take a look at the different sections:

### Header

The first part of the schema is a typical header, this is where we define the version of the Atlas schema as well as some top level information regarding this schema.

<pre><code data-language="json">
    {
      "atlasVersion":"#{site.release.atlas_version}",
      "namespace":"com.mycompany",
      "name":"MySchema",
      "documentation":"A description of the purpose of my schema",
      "version":"1.0.0",
      ....
    }
</code></pre>

#### Atlas Version 

This describes the version of Atlas that was used to define this schema

#### Namespace

The namespace is based on the concept of grouping schema together into a logical heirarchy.  The namespace is used to completely reference a schema, for example if your schema is MySchema and the namespace is com.mycompany then your fully qualified schema name is com.mycompany.MySchema.

This can be used when linking to other schema and should always be included, and a namespace can not contain spaces or special characters.

#### Name

The name of your schema,  this should be a simple name with only letters and characters and no spaces or special characters.

#### Documentation

This should provide a definition for the purpose or use of your schema,  for example, "A representation of customers and their related addresses".

#### Version

This is the version for your schema representation,  you should always keep version numbering in place for your data schema to ensure that people are able to track changes.  We strongly recommend looking at [Semantic Versioning](http://semver.org/).

### Organization

<pre><code data-language="json">
    {
      ...
      "organization":{
        "name":"My Company",
        "webSiteUrl":"http://mycompany.com",
        "logoUrl":"http://mycompany.com/awesome-logo.png"
      } 
      ....
    }
</code></pre>

It is important when sharing a schema to tell the world a little about who you are,  the organization allow you to share the details of the company, organization or foundation that is sharing this information.  Typical information he hold here is:

* Name - The name of the organization
* webSiteUrl - The URL of the organization's web presence
* logoUrl - The URL of a logo (this is used when building site documentation)

### Contributors

<pre><code data-language="json">
    {
      ...
      "contributors":[{
          "name":"Philip Dodds",
          "twitter":"philipdodds",
          "webSiteUrl":"http://dataset.io",
          "organization":"Dataset IO"
        },{
          "name":"Garry Wright",
          "webSiteUrl":"http://dataset.io",
          "organization":"Dataset IO"
        }
        ...
      ],
      ....
    }
</code></pre>

Often we want to share information about the people involved in the definition of a schema,  this brings out the ecosystem that is in involved and allows you to see the people behind the work.

We have a set of attributes which can be shared for a contributor:

* Name - The name of the contributor
* Twitter - The twitter handle of the contributor
* webSiteUrl - The URL of the contributor's web presence
* organization - The name of the organization that this contributor represents

### License

<pre><code data-language="json">
    {
      ...
      "license":{
        "name":"Apache Software License v2.0",
        "description":"Apache Software License",
        "copyrightNotice":"(C) Copyright 2012 FiMod (http://fimod.org)",
        "webUrl":"http://www.apache.org/licenses/LICENSE-2.0.html"
      },
      ....
    }
</code></pre>

Since some of the schema's that are used with Atlas are planned to be open source we can also include the license information in the schema definition.  Attributes include:

* Name - The license name
* Description - The short description of the license
* CopyrightNotice - A copyright right notice that should be provided with the schema
* webUrl - A web URL for more information on the schema

### Revision Control System

<pre><code data-language="json">
    {
      ...
      "revisionControlSystem":{
        "system":"github",
        "webUrl":"https://github.com/fimod/lei"
      },
      ....
    }
</code></pre>

This allows the schema to include metadata around where the revision control system that is used for the schema is housed.

* System - Currently we only support github as a revision control system
* webUrl - The website url where you can find the github repository

### Issue Tracker

<pre><code data-language="json">
    {
      ...
      "issueTracker":{
        "system":"github",
        "webUrl":"https://github.com/fimod/lei/issues"
      },  
      ....
    }
</code></pre>

This allows the schema to include metadata around where the issue tracking system that is used for the schema is housed.


* System - Currently we only support github as an issue tracker
* webUrl - The website url where you can find the issue tracker

### Nodes

<pre><code data-language="json">
    {
      ...
      "nodes":[{
        "name":"People",
        "description":"People",
        "documen....
    }
</code></pre>

The heart of the schema is its definition of **nodes**, see [Nodes](nodes.html) for more information on how this is structured.
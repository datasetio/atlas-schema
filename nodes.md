---
layout: base
title: Atlas Schema / Nodes
---

### Nodes

A node is a representation of a point of data,  that can be something like a single value or it can be a group.

For example a node might be **FirstName**, and another node might be **Person**.  In this case a **FirstName** has a relationship to a **Person**.

In Atlas everything is a Node and every node has relationships to other nodes,  this means we aren't structure like a typical database world with tables and columns - though our model can be fairly easily converted to this type of structure.

In the Atlas schema you define a list of nodes at the top level,  lets take a look at one of the node definitions and look at what it has in it.

<pre><code data-language="javascript">
    {
      ...
      {
	    "name":"FirstName",
	    "description":"First Name",
	    "documentation":"The first name of an individual.",
	    "nodeType":{
	      "dataType":"String"
	    },
	    "relationships":[],
	    "sampleValue":"Philip"
	  },
      ....
    }
</code></pre>

The structure of a node is fairly simple,  lets walk through each of the properties:

#### Name

The name of the node,  this is the symbolic name which means that is should be a simple value have no spaces or special characters in it. 

#### Description

This is the description,  typically this is the longer version of the name including spaces and any special characters.

#### Documentation

This is the documentation for the node.  Commonly this is where more information is provided to describe the meaning of the node,  often putting it in some context to allow deeper understanding.

#### Node Type

The node type can be a range of values to describe the node's data.  The available types are:

<table class="table">
  <thead>
    <tr>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>String</td>
      <td>A sequence of characters</td>
    </tr>
    <tr>
      <td>Date</td>
      <td>A date with no time portion</td>
    </tr>
    <tr>
      <td>DateTime</td>
      <td>A date and time with timezone information</td>
    </tr>
    <tr>
      <td>Number</td>
      <td>A number that has no decimal or float component</td>
    </tr>
    <tr>
      <td>Decimal</td>
      <td>A decimal number</td>
    </tr>
    <tr>
      <td>Float</td>
      <td>A floating point number</td>
    </tr>
    <tr>
      <td>Enumeration</td>
      <td>A string that has a domain of values that are valid</td>
    </tr>
    <tr>
      <td>Boolean</td>
      <td>A true or false</td>
    </tr>
    <tr>
      <td>DataGroup</td>
      <td>A data group is where a node is a grouping of other nodes and has not explicit value only relationships to other nodes</td>
    </tr>
  </tbody>
</table>

#### Relationships

A list of the relationships that this node has to other nodes in this schema,  see the [Relationships](relationships.html) guide for more information on how they work.

#### Sample Value

A simple sample value for the field - this allows people to quickly gather context for node by seeing an example of data it might hold. 
   





---
layout: base
title: Atlas Schema / Nodes
---

### Nodes

A node is a representation of a peice of understanding around data,  this can be almost anything and is purposefully abstract.  A node on its only simply represents an item of knowlegde,  for example you might know that you have a person.  Therefore you would create a Person.

<pre><code data-language="javascript">
    {
      ...
      {
        "name":"Person",
        "description":"A Person",
        "documentation":"A human being"
      },
      ....
    }
</code></pre>

Or you might decide that you want to have a Name.

<pre><code data-language="javascript">
    {
      ...
      {
        "name":"Name",
        "description":"A Name",
        "documentation":"A word or collection of words used to identify something"
      },
      ....
    }
</code></pre>

And then you might decide that you want a Person to have a name,  thus you would create a relationship between a person and a name.

<pre><code data-language="javascript">
    {
      ...
      {
        "name":"Person",
        "description":"A Person",
        "documentation":"A human being",
        "relationships" : ["Name"]
      },
      ....
    }
</code></pre>

At this level you are able to build up an abstract representation of the understand you have about the data you want to model.  Typically however you will want to start providing more information on the structure of this data as you do,  often it starts when we try to specify what type a node might be.

In this sense we use the term type to reference if something is a string of characters, a date, a number etc.  We do this so that we are able to understand how to move things out to database technologies,  however in Atlas we do not have a fixed set of base types (sometimes call Primitives), since everything is a Node.   Therefore if you want to specify that Name, for example, is a String type you would use one of the Dataset IO core nodes.

The core nodes are a set of Nodes defined in an internal Schema which is at the heart of Atlas,  you can see the schema here.  We have defined a set of basic Nodes that represent the core types at the heart of most database technologies and you can use them in your Nodes by extending them.


<pre><code data-language="javascript">
    {
      ...
      {
        "name":"Name",
        "description":"A Name",
        "documentation":"A word or collection of words used to identify something",
        "extend" : "io.dataset.atlas.type.String"
      },
      ....
    }
</code></pre>

By including this core type we are able to not see that the Name is a String, since our export technology is aware of these core types you are able to then generate SQL schemas or XML schemas which would port this String representation into the appropriate type.

### Relationship Cardinality

In our earlier example we had a simple relationship between a Person and a Name,  in this case a Person has one name.  The default when we specify a relationship is that there is a single instance of the relationship.  However,  often we might have situations where it isn't a one to one relationship.

Lets add another couple of nodes to our world and see what happens,  First lets create some parts of an Address and then create an Address.

<pre><code data-language="java">
    {
      ...
      {
        "name":"Street",
        "description":"Street Name",
        "documentation":"The name of a street",
        "extends" : "io.dataset.atlas.type.String"
      },
      {
        "name":"ZipCode",
        "description":"Zip Code",
        "documentation":"A US Zip Code",
        "extend" : "io.dataset.atlas.type.String"
      },
      {
        "name":"Address",
        "description":"Address",
        "documentation":"An addresss",
        "relationships" : ["Street","ZipCode"]
      },
      ....
    }
</code></pre>

Above we have created a basic model to represent a Street and a Zipcode (both are extended from our core String node) and then an Address which has one Street and one ZipCode.  Now lets say that we want to show that a Person can have zero or many Addresses.  We would need to add Address to the relationships on Person.

<pre><code data-language="java">
    {
      ...
      {
        "name":"Person",
        "description":"A Person",
        "documentation":"A human being",
        "relationships" : ["Name","Address[0..]"]
      },
      ....
    }
</code></pre>

Note that now on the Address in the relationships we include a classifier which highlights the cardinality of the relationship - in this case [0..].  Atlas uses this Cardinality to represent that there can be 0 to (..) any number of instances of Address related to Person,  this would typically be referred to as a one-to-many relationship.

Cardinality definitions in Atlas can be shown in a few different ways.  For example:

* [1..10] means that must be at least one and there can be a maximum of 10
* [0..] there can be no relationship or any number of relationships
* [0..1] there can be no relationship or there can be only one,  this is the default
* [1..1] there must be at one and only one relationship

### Sample Values

When a node is going to hold a value it is sometimes helpful to provide a sample value, for example:

<pre><code data-language="java">
    {
      ...
      {
      "name":"Name",
      "description":"A Name",
      "documentation":"A word or collection of words used to identify something",
      "extend" : "io.dataset.atlas.type.String"
      "sampleValue" : "Philip"
    },
      ....
    }
</code></pre>




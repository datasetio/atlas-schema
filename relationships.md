---
layout: base
title: Atlas Schema / Relationships
---

### Relationships

In the [Nodes](nodes.html) section we walked through a simple example of how a node can build a relationship and also how a express cardinality on the relationship.

From that brief introduction you have probably started to see that all Nodes are abstract and there is no difference between a node that holds a value and one that does not.  In this section we aim to add more detail to how more complex node structures are set-up to model other types of relationship.

### One-to-One

The simpliest of all relationships is the one-to-one relationship,  you can specify this from any direction and the opposing direction will be implied.  For example

<pre><code data-language="json">
    {
      ...
      {
        "name":"Person",
        "relationships" : ["Name","Address"]
      },
      ....
    }
</code></pre>

In this case we just simply specify the name of the node that we want to use,  we don't care if the node is one that holds a value or another grouping of values,  because nodes are just nodes.

### One-to-Many

A one to many simply includes the [ ] and the range for the cardinality,  therefore we say there can 0 to unbounded instances of the relationship,  therefore is it [0..]

<pre><code data-language="json">
    {
      ...
      {
        "name":"Person",
        "relationships" : ["Name","Address[0..]"]
      },
      ....
    }
</code></pre>

### Many-to-Many

If you have a many to many, for example a person can have a relationship with many organizations and an organization has many people then you can use the cardinality to express that.

<pre><code data-language="json">
    {
      ...
      {
        "name":"Person",
        "relationships" : ["Name","Organization[0..]"]
      },
      {
        "name":"Organization",
        "relationships" : ["Name","Person[0..]"]
      },
      ....
    }
</code></pre>

In an Atlas schema you don't need to create a Node in the middle unless you want to add additional information for the relationship,  for example if you wanted to know the Start and End dates for people in an organization, then you would need to add a new node in the middle and provide a meaningful name.

<pre><code data-language="json">
    {
      ...
      {
        "name":"Person",
        "relationships" : ["Name","Employment[0..]"]
      },
      {
        "name":"Organization",
        "relationships" : ["Name","Employment[0..]"]
      },
      {
        "name":"Employment",
        "relationships" : ["StartDate","EndDate"]
      },
      ....
    }
</code></pre>
 
If you want to describe the relationship a little more fully than organization has a relationship with person you can make use of 2 additional items in the syntax.


<pre><code data-language="json">
    {
      ...
      {
        "name":"Person",
        "relationships" : ["Name","Employers->Organization[0..](A persons' Employers)"]
      },
      {
        "name":"Organization",
        "relationships" : ["Name","Employees->Person[0..](An organization's employees)"]
      },
      ....
    }
</code></pre>

### Multiple Relationships

Another case where you might think you would need to introduce a new node is where one node has more than one relationship with a second node. Again this isn't the case. For example lets say that we have a person who has two Addresses,  the first is a work address and the second is a home address.  You could model this as two relationships between a Person and an Address,  or in order to identify them you could introduce some additional syntax.  For example:
So this:-
<pre><code data-language="json">
    {
      ...
      {
        "name":"Person",
        "relationships" : ["Name","HomeAddress","WorkAddress"]
      },
      {
        "name":"Address",
        "relationships" : ["Street","ZipCode"]
      },
      {
        "name":"HomeAddress",
        "relationships" : ["Address"]
      },
      {
        "name":"WorkAddress",
        "relationships" : ["Address"]
      },
      ....
    }
</code></pre>
can be specified as :-
<pre><code data-language="json">
    {
      ...
      {
        "name":"Person",
        "relationships" : ["Name","HomeAddress->Address","WorkAddress->Address"]
      },
      {
        "name":"Address",
        "relationships" : ["Street","ZipCode"]
      },
      ....
    }
</code></pre>

In the rare cases where there a multiple many to many relationships between the same two nodes and you dont want to specify  those via a new node you need additional information to be held on that relationship so identify the pairs of relationships.
<pre><code data-language="json">
    {
      ...
      {
        "name":"Person",
        "relationships" : ["Name","Employers->Organization[0..](A persons' Employers)","Schools->Organization[0..](A persons' Educational Establishments)"]
      },
      {
        "name":"Organization",
        "relationships" : ["Name","Employees->Person[0..](An organization's employees)"],"Students->Person[0..](An organization's students)"]
      },
      ....
    }
</code></pre>
The above would be ambiguous and would create 4 unrelated relationships. So to complete the picture we require further syntax:-
<pre><code data-language="json">
    {
      ...
      {
        "name":"Person",
        "relationships" : ["Name","Employment->Employer->Organization[0..](A persons' Employers)","Education->School->Organization[0..](A persons' Educational Establishments)"]
      },
      {
        "name":"Organization",
        "relationships" : ["Name","Employment->Employee->Person[0..](An organization's employees)"],"Education->Student->Person[0..](A organization's students)"]
      },
      ....
    }
</code></pre>

The the additional name is the name of the "relationship" that groups the individual relationships together so they can be seen as the reverse of each other. The names of the individual relationships were changed only to be more definitive within that perspective. 



---
layout: base
title: Atlas Schema / Relationships
---

### Relationships

Nodes are simple structures,  they can either be a point of data or a container (in the form of a node type DataGroup),  you can see this in the [Nodes](nodes.html) part of the documentation.

The **relationships** attribute is under a node and has a list of relationship instances,  each of these has a targetNodeName and can have a name and a cardinality.

<pre><code data-language="javascript">
    {
      ...
	  "relationships":[{
	      "targetNodeName":"Address",
	      "cardinality":"1.."
	  	},
      ....
    }
</code></pre>

In order to understand how relationships work it is best to think about the 


#### Target Node Name

This refers to the name of the node in this schema to which this node, the one under which we have the relationships attribute is related.

#### Cardinality

However,  much of the understanding of the structure of a schema is based on the relationships that exist between nodes.  In Atlas we provide a number of relationship types that can exist between to nodes.  Note that all nodes have individual relationships with other nodes,  thus they must always be declared from both directions.

Lets walk through each of the available relationship cardinalities.

#### HasOne

Coming soon....

#### BelongsTo

Coming soon....

#### HasMany






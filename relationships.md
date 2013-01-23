---
layout: base
title: Atlas Schema / Relationships
---

### Relationships

Nodes are simple structures,  they can either be a point of data or a container (in the form of a node type DataGroup),  you can see this in the [Nodes](nodes.html) part of the documentation.

The **relationships** attribute is under a node and has a list of relationship instances,  each of these has a targetNodeName, a name and a cardinality.

<pre><code data-language="javascript">
    {
      ...
	  "relationships":[{
	      "targetNodeName":"Address",
	      "name":"Housed At",
	      "cardinality":"BelongsTo"
	  	},
      ....
    }
</code></pre>

#### Target Node Name

This refers to the name of the node in this schema to which this node, the one under which we have the relationships attribute is related.

#### Name

This is the name of the relationship,  typically this is used to describe the relationships that exists between these nodes from the direction of the current node to the target node.

#### Relationship Cardinalities

However,  much of the understanding of the structure of a schema is based on the relationships that exist between nodes.  In Atlas we provide a number of relationship types that can exist between to nodes.  Note that all nodes have individual relationships with other nodes,  thus they must always be declared from both directions.

Lets walk through each of the available relationship cardinalities.

#### HasOne

Coming soon....

#### BelongsTo

Coming soon....

#### HasMany






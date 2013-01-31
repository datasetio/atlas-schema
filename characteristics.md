---
layout: base
title: Atlas Schema / Characteristics
---

### Characteristics

On a node we also support the setting of characteristics,  this defines certain additional information such a length, max/min values and also enumerations.

Below we can see an example of additional characteristics being applied to a node.

<pre><code data-language="java">
    {
      ...
      {
            "name": "AddressType",
            "documentation": "A collection of characters",
            "extend" : "io.dataset.atlas.type.String"
            "characteristics": {
                "length": "25",
                "enumeration" : [ "Home", "Work" ]
            }
        },
      ....
    }
</code></pre>

The available characteristics are:

* length - the length of the node datum
* pattern - a regular expression that is used to validate the node datum
* enumeration - the domain of values valid for the node datum
* max - a numerical value that is the maximum valid value for the node datum
* min - a numerical value that is the minimum valid value for the node datum
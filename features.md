---
layout: base
title: Atlas Schema / Features
---

### Features

Atlas provides a extensible way to add additional metadata to a node,  this is captures in terms of features.

Basically features are in essence of map of Strings,  therefore you can put anything in a feature.  Tooling has the ability to use these features to control their behaviour.

For example lets take a look at the definition of io.dataset.atlas.type.String

<pre><code data-language="java">
    {
      ...
      {
            "name": "String",
            "documentation": "A collection of characters",
            "datum": true,
            "features": {
                "io.dataset.atlas.xml.xmlType": "xs:string",
                "io.dataset.atlas.java.javaType": "String",
                "io.dataset.atlas.avro.avroType": "String"
            }
        },
      ....
    }
</code></pre>

Here we see some features for the node String, these are used by the Atlas toolchain when we go to build DDL, XSD and also Avro schemas based on our Atlas Schema.

You are able to add more of these features if you are looking for an extension point to the node to capture additional metadata.
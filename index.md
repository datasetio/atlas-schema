---
layout: base
title: Atlas Schema / Introduction
---

### Introduction

In the past modelling data was constrainted by the most obvious technology, and it was RDBMS or Relational Database Management Systems.  While RDBMS are still an excellent way of modelling data now it is no longer the only way to model it,  and commonly it is combined with other forms for other types of storage such as XML for files or technologies from Avro for archival.

At Dataset IO we wanted to provide an open way to model data structures,  one that would allow us to go back to a type of persistence container (such as a database) but also to be able to present the structure in a way that can be modeled in other persistence technologies.   Also we wanted to capture more than the raw structure,  we wanted to provide other helpful information such as example values,  potential sources of the data and features that data might want (such as user audited or time sensitive).  That is why we created **Atlas**.

An Atlas schema is a JSON document that can be used to capture information about the structured or semi-structured data.  In this documentation we will look at some of the core parts.


   





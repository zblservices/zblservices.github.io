---
title:  "doctorbatch.io Prerequisites"
date: 2015-08-17 12:00:00
categories: magicsauce
layout: article
icon-major: fa-circle
icon-minor: fa-flask
---

# Prerequisites
To use **doctorbatch.io**, you'll need to import several dependencies from IBM products into your local Maven repository. The dependencies are as follows:

* The MVS components require IBM Java for z/OS Toolkitfrom your JDK 1.6 or later installation on z/OS, and marshall.jar from your WebSphere Application Server installation (on any platform).
* The ODM components require the JRules RES Execution library from your Operational Decision Manager installation on any platform
* The WebSphere components require the Batch Runtime library from your WebSphere Application Server installation on any platform

Note that *doctorbatch.io-core* and *doctorbatch.io-javabatch* may be built and used without and IBM dependencies.

See the details here: <a href="{{ site.baseurl }}/prerequisites/2015/08/17/Prerequisites.html">**doctorbatch.io** prerequisites</a>

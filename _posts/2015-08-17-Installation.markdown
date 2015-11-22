---
title:  "Building **doctorbatch.io** from Source"
date: 2015-08-17 12:00:00
categories: magicsauce installation
---

# Building **doctorbatch.io** from Source
To build the **doctorbatch.io** from source, you'll need to import several dependencies
from IBM products into your local Maven repository. The dependencies are as follows:

* The MVS components require IBM Java for z/OS Toolkitfrom your JDK 1.6 or later installation on z/OS, and marshall.jar from your WebSphere Application Server installation (on any platform).
* The ODM components require the JRules RES Execution library from your Operational Decision Manager installation on any platform
* The WebSphere components require the Batch Runtime library from your WebSphere Application Server installation on any platform

Note that *doctorbatch.io-core* and *doctorbatch.io-javabatch* may be built and used without and IBM dependencies.

## Locate and import the dependencies
To import a dependency into your local repository, use the following command
{% highlight bash %}
mvn install:install-file -Dfile=<path-to-file> -DgroupId=<group-id> -DartifactId=<artifact-id> -Dversion=<version> -Dpackaging=<packaging>
{% endhighlight %}

The dependencies and their target coordinates are described below.

**IBM Java for z/OS Toolkit** is located in your JDK 1.6 or later for z/OS at
{% highlight bash %}
  $JAVA_HOME/lib/ext/ibmjzos.jar
{% endhighlight %}

*Dependency coordinates*

{% highlight xml  %}
<dependency>
  <groupId>com.ibm</groupId>
  <artifactId>jzos</artifactId>
  <version>2.4</version>
</dependency>
{% endhighlight %}

**marshall.jar** is located in your WebSphere Application Server v8.5.x installation at
{% highlight bash %}
  $WAS_HOME/AppServer/plugins/com.ibm.ws.wsadie/marshall.jar
{% endhighlight %}

*Dependency coordinates*

{% highlight xml  %}
<dependency>
 <groupId>com.ibm</groupId>
 <artifactId>marshall</artifactId>
 <version>1.0.0</version>
</dependency>
{% endhighlight %}

**JRules RES Execution library** is located in your Operational Decision Manager v8.7 (or later) installation at
{% highlight bash %}
  $ODM_HOME/executionserver/lib/jrules-res-session-java.jar
{% endhighlight %}

*Dependency coordinates*

{% highlight xml  %}
<dependency>
   <groupId>com.ibm</groupId>
   <artifactId>jrules-res-session-java</artifactId>
   <version>8.7.0.0</version>
 </dependency>
{% endhighlight %}

**WebSphere Batch Runtime** is located in your WebSphere Application Server v8.5.x (or later) installation at
{% highlight bash %}
  $WAS_HOME/AppServer/plugins/com.ibm.ws.batch.runtime.jar
{% endhighlight %}

*Dependency coordinates*

{% highlight xml  %}
<dependency>
   <groupId>com.ibm</groupId>
   <artifactId>jrules-res-session-java</artifactId>
   <version>8.7.0.0</version>
 </dependency>
{% endhighlight %}

## Building **doctorbatch.io** components

Depending on which products (and therefor dependencies) you have available, you may wish to build only a subset of **doctorbatch.io** modules. A complete build may be obtained by running
{% highlight bash %}
mvn install
{% endhighlight %}

To build any specific submodule, simple switch to the submodule directory, and execute mvn install from there.

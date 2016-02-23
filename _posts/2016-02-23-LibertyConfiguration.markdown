---
title:  "Configuring WebSphere Liberty Profile for Java Batch"
date: 2016-02-23 13:00:00
categories: magicsauce gettingstarted
---
# Configuring WebSphere Liberty Profile
Below is a sample server configuration that will get you started quickly with JSR-352
and the Batch Management capabilities available in WebSphere Liberty Profile.

Be sure you have <a href="https://developer.ibm.com/wasdev/downloads/#asset/runtimes-8.5.5-wlp-javaee7">installed Liberty 8.5.5.x with Java EE 7 Full Platform</a>, as well as the <a href="https://developer.ibm.com/wasdev/downloads/#asset/features-com.ibm.websphere.appserver.batchManagement-1.0">Batch Management feature</a>!

{% highlight xml %}
<server description="batch server">
  <!-- Enable features -->
  <featureManager>
        <feature>javaee-7.0</feature>
        <feature>batchManagement-1.0</feature>
        <feature>localConnector-1.0</feature>
        <feature>appSecurity-2.0</feature>
  </featureManager>

  <!-- SSL KeyStore -->
	<keyStore password="password"/>

  <!-- User registry -->
	<basicRegistry id="basic" realm="ibm/api">
		<user name="demo" password="password"/>
	</basicRegistry>

  <administrator-role>
    <user>demo</user>
  </administrator-role>

  <!-- Define the batch authorization roles -->
	<authorization-roles id="com.ibm.ws.batch">
		<security-role name="batchAdmin">
			<user name="demo"/>
		</security-role>
		<security-role name="batchSubmitted">
			<special-subject type="ALL_AUTHENTICATED_USERS"/>
		</security-role>
		<security-role name="batchMonitor">
			<special-subject type="ALL_AUTHENTICATED_USERS"/>
		</security-role>
	</authorization-roles>

  <!-- To access this server from a remote client add a host attribute to the following element, e.g. host="*" -->
  <httpEndpoint httpPort="9080" httpsPort="9443" id="defaultHttpEndpoint"/>

  <!-- Automatically expand WAR files and EAR files -->
	<applicationManager autoExpand="true"/>

  <applicationMonitor updateTrigger="mbean"/>
</server>
{% endhighlight %}

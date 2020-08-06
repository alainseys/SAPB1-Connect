<h2>SAPB1-Connect</h2>


<p>This libary allows you to connect to SAPBONE , you only need to add this compiled libary to your solution and add some keys in your app.config, after you added you need to call the keys in your solution eg </p>
<pre>
var SAPSERVER = ConfigurationManager.AppSettings["server"];
</pre>

<b>Required Keys:</b>
<add key="server" value="YOURSERVERNAME" <li>
<add key="licenseserver" value="YOURSERVERNAME:30000" />
<add key="dbuser" value="yourdbusername" />
<add key="dbpass" value="yourdbpassword" />
<add key="company" value="yourcompanydb" />
<add key="user" value="SAP_USER" />
<add key="pass" value="SAP_USER_PASSWORD" />




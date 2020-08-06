<h2>SAPB1-Connect</h2>


<p>This libary allows you to connect to SAPBONE , you only need to add this compiled libary to your solution and add some keys in your app.config, after you added you need to call the keys in your solution eg </p>
<pre>
var SAPSERVER = ConfigurationManager.AppSettings["server"];
</pre>

<b>Required Keys:</b>
<ul>
<li><add key="server" value="YOURSERVERNAME" />><li>
<li><add key="licenseserver" value="YOURSERVERNAME:30000" />><li>
<li><add key="dbuser" value="yourdbusername" /><li>
<li><add key="dbpass" value="yourdbpassword" /><li>
<li><add key="company" value="yourcompanydb" /><li>
<li><add key="user" value="SAP_USER" /><li>
<li><add key="pass" value="SAP_USER_PASSWORD" /><li>
</ul>

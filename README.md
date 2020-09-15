<h2>SAPB1-Connect</h2>

<b><p>How to connect</p></b>
<hr />
<p>Create in your C# solution a app.config file with the following params: (see App.config.sample)</p>
<ul>
            <li>add key="server" value="SAPSRV" /></li>
            <li>add key="licenseServer" value="SAPSRV:30000" /></li>
            <li>add key="dbuser" value="sa" /></li>
            <li>add key="dbpass" value="YourDBApassword" /></li>
            <li>add key="companydb" value="ProductionDatabase" /></li>
            <li>add key="user" value="SAPUSER" /></li>
            <li>add key="pass" value="SAPPASSWORD" /></li>
            <li>add key="ClientSettingsProvider.ServiceUri" value="" /></li>
</ul>
<p>Fill out the values that match your enviroment, and add the DLL libary to your references</p>

<p>In your code yo need to setup a connection and execute the write to the sap database bellow some sample code</p>

<b>Example : Write payment date and payment link of MSP to sap ORDR (orders) table </b>
<pre>
try
            {
                ServerConnection connection = new ServerConnection();
                if (connection.Connect() == 0)
                {
                    try
                    {
                       
                        var Data_U_Betaal_link = txt_opmerkingen.Text;

                        var Docentry = Convert.ToInt32(txt_docentry.Text);
                        //sap config variables en parameters
                        int retval = 0;
                        string UDF_VELD_BETAAL_DATUM = "U_U_BETAAL_Datum";
                        string UDF_VELD_BETAAL_LINK = "U_U_BETAAL_LINK";
                        SAPbobsCOM.Documents oOrder;
                        oOrder = connection.GetCompany().GetBusinessObject(SAPbobsCOM.BoObjectTypes.oOrders);
                        if (oOrder.GetByKey(Docentry))
                        {
                            oOrder.UserFields.Fields.Item(UDF_VELD_BETAAL_DATUM).Value = datum_formated;
                            oOrder.UserFields.Fields.Item(UDF_VELD_BETAAL_LINK).Value = Data_U_Betaal_link;
                            retval = oOrder.Update();
                            if (retval == 0)
                            {
                                _log.Info("Document: " + txt_docnum.Text + " is succesvol bijgewerkt");                             
                                MessageBox.Show("Item Bijgewerkt");
                            }
                            else
                            {
                                MessageBox.Show(connection.GetCompany().GetLastErrorCode() + "-" + connection.GetCompany().GetLastErrorDescription());
                                _log.Error(connection.GetCompany().GetLastErrorCode() + "-" + connection.GetCompany().GetLastErrorDescription());
                            }
                            System.Threading.Thread.Sleep(2000);
                            connection.GetCompany().Disconnect();
</pre>

<b>Recomendation:</b>
<p>I recommend before you setup your sap project you implement <a href:"https://www.nuget.org/packages/log4net/">LOG4NET</a> in your solution so you can write some debugging code</p>

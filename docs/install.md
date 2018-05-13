> # *Sense Excel Reporting and Demo Apps Installation Process*

##  *SERVER PREPARATION*

 1.  Confirm Qlik Sense Server version - November 2017 or later

 2.  Confirm .NET Installation. 

Please install the  .NET Core Runtime prior to this installation. Click the link to download the appropriate version from Microsoft. [Download](https:/www.microsoft.com/net/download/Windows/run)
 
 3. Create Target Sub-directories
 
C:\Reporting (advised not to use Qlik share directory)
C:\Reporting\SERReports

## *FILE PREPARATION*

 1. Copy/Download Install Files to Desktop

ser-ext ondemand.zip
serConnector.zip 

 2. Unzip the SerConnnector.zip to the Desktop

 3. Copy/unzip the following files to the C:\Reporting directory

\Apps
\ArchivedLogs
\CustomData
\Reporting
\StaticContent
RunConnector.bat

## *RUN CONNECTOR*

1.  Execute RunConnector.bat as Administrator from the \Reporting directory

Security keys will be created in  %appdata%\Roaming\senseexcel\reporting

Connector Logs will be created in %appdata%\Roaming\senseexcel\ser-con-aai
 
Engine Logs will be created in %appdata%\Roaming\senseexcel\ser-engine

 2. Open Services.msc
 
 3. Restart Qlik Repository Services and all sub-processes.
 

## *INSTALL EXTENSION*

Install the ser-ext-ondemand extension on the Qlik Sense 
server.

QMC> MANAGE RESOURCES > EXTENSIONS +  Import + Choose File

C:\Desktop\ser-ext-ondemand.zip

##  * UPDATE REPORTING CONFIGURATION FILE*

 1. Open the following file using Notepad or other text editor:
C:\Reporting\Connector\config.hjson

 2. Update the serEnginePath parameter:
serEnginePath: C:\Reporting\Engine\SenseExcelReporting.exe

 3. Update bindingHost parmeter:
bindingHost: localhost
  
 4. Update  bindingPort parameter
bindingPort: 50059

 5. Update the default the connectors takes parameters to your local server name:
 https://LOCALSERVERNAME/ser as serverUri

6.  Update the defined HTTP header for the virtual proxy
		 key parameter: X-Qlik-Session-ser
 7. Save and close config.hjson file.

## *ADD CONTENT LIBRARIES*
Add the following content libraries to the Qlik Sense server:
sensexcel
senseexcelreports

QMC > Content Libraries >  +Create New > senseexcel
QMC > Content Libraries >  +Create New > senseexcelreports

## *ADD LICENSE INFO*

### Qlik and Partner Licenses

This step can be ignored.

### Token Licensing 

 1. Open a new text file.  
 2. Copy and paste your LEF information
 3. Delete any spaces at end of each line.
 4. Save file with name license.txt.
 5. Upload the license.txt file to the senseexcel content library.
 
QMC > MANAGE CONTENT > Content Libraries > senseexcel >Upload > license.txt

 6. A required security rule for this content library is defined in the ADD SECURITY RULES section later in this document.

### Named Licensing

 1. Open a new text file.  
 2. Copy and paste your LEF information
 3. Delete any spaces at end of each line.
 4. Append the LEF information with user information as in the example below.  
 5. The  FROM:TO info is optional.  Only include it if you want to put time limits on your named user licenses.

9999999999999999

EXCEL_NAMED;5;;YYYY-MM-DD
AAAA-BBBB-CCCC-DDDD-EEEE
> # *Sense Excel Reporting and Demo Apps Installation Process*

##  *SERVER PREPARATION*

 1.  Confirm Qlik Sense Server version - November 2017 or later

 2.  Confirm .NET Installation. 

Please install the  .NET Core Runtime prior to this installation. Click the link to download the appropriate version from Microsoft. [Download](https:/www.microsoft.com/net/download/Windows/run)
 
 3. Create Target Sub-directories
 
C:\Reporting (advised not to use Qlik share directory)
C:\Reporting\SERReports

## *FILE PREPARATION*

 1. Copy/Download Install Files to Desktop

ser-ext ondemand.zip
serConnector.zip 

 2. Unzip the SerConnnector.zip to the Desktop

 3. Copy/unzip the following files to the C:\Reporting directory

\Apps
\ArchivedLogs
\CustomData
\Reporting
\StaticContent
RunConnector.bat

## *RUN CONNECTOR*

1.  Execute RunConnector.bat as Administrator from the \Reporting directory

Security keys will be created in  %appdata%\Roaming\senseexcel\reporting

Connector Logs will be created in %appdata%\Roaming\senseexcel\ser-con-aai
 
Engine Logs will be created in %appdata%\Roaming\senseexcel\ser-engine

 2. Open Services.msc
 
 3. Restart Qlik Repository Services and all sub-processes.
 

## *INSTALL EXTENSION*

Install the ser-ext-ondemand extension on the Qlik Sense 
server.

QMC> MANAGE RESOURCES > EXTENSIONS +  Import + Choose File

C:\Desktop\ser-ext-ondemand.zip

##  * UPDATE REPORTING CONFIGURATION FILE*

 1. Open the following file using Notepad or other text editor:
C:\Reporting\Connector\config.hjson

 2. Update the serEnginePath parameter:
serEnginePath: C:\Reporting\Engine\SenseExcelReporting.exe

 3. Update bindingHost parmeter:
bindingHost: localhost
  
 4. Update  bindingPort parameter
bindingPort: 50059

 5. Update the default the connectors takes parameters to your local server name:
 https://LOCALSERVERNAME/ser as serverUri

6.  Update the defined HTTP header for the virtual proxy
		 key parameter: X-Qlik-Session-ser
 7. Save and close config.hjson file.

## *ADD CONTENT LIBRARIES*
Add the following content libraries to the Qlik Sense server:
sensexcel
senseexcelreports

QMC > Content Libraries >  +Create New > senseexcel
QMC > Content Libraries >  +Create New > senseexcelreports

## *ADD LICENSE INFO*

### Qlik and Partner Licenses

This step can be ignored.

### Token Licensing 

 1. Open a new text file.  
 2. Copy and paste your LEF information
 3. Delete any spaces at end of each line.
 4. Save file with name license.txt.
 5. Upload the license.txt file to the senseexcel content library.
 
QMC > MANAGE CONTENT > Content Libraries > senseexcel >Upload > license.txt

 6. A required security rule for this content library is defined in the ADD SECURITY RULES section later in this document.

### Named Licensing

 1. Open a new text file.  
 2. Copy and paste your LEF information
 3. Delete any spaces at end of each line.
 4. Append the LEF information with user information as in the example below.  
 5. The  FROM:TO info is optional.  Only include it if you want to put time limits on your named user licenses.
 6. Save file with name license.txt.
 
 7. Upload the license.txt file to the senseexcel content library.

QMC > MANAGE CONTENT > Content Libraries > senseexcel >Upload > license.txt

 8. A required security rule for this content library is defined in the ADD SECURITY RULES section later in this document.


##  *ADD ANALYTIC CONNECTION*
 
Define the name, Host, Port, Reconnect Timeout and Reg Timeout parameters

QMC > MANAGE CONTENT > Analytic Connections > + Create New

|Setting|Value|
------|--------------
|Name | ser
|Host | localhost
|Port | 50059|
|Reconnect Timeout|30
|Request Timeout|30|

##  *ADD VIRTUAL PROXY*
In this section you will define a new Virtual Proxy and then link it to the Main Proxy.  This operation MUST be done in a particular order. 

Create the Virtual Proxy via the QMC’s Virtual Proxy menu first. To ensure that the links will work properly DO NOT utilize the Create New Virtual Proxy technique within the QMC Proxy Menu. 

QMC > CONFIGURE SYSTEM > Virtual proxies > + Create new

Once the new virtual proxy is created, confirm the following Properties are checked in the Dialogue Box on the right side of your screen.

Identification
Authentication
Load Balancing
Advanced

### *IDENTIFICATION SECTION*

|Setting|Value|
|--|--|
|Description  |ser
|Prefix| ser 
Session inactivity timeout | 30
Session cookie header name | X-Qlik-Session-ser|


### *AUTHENTICATION*
|Setting|Value|
|--|--|
|Anonymous access mode | No anonymous user   |
|Authentication method | JWT|
JWT certificate | -----BEGIN CERTIFICATE-----|
|JWT attribute for user ID | UserID|
|JWT attribute value for user directory | UserDirectory


### LOAD BALANCING

Load Balancing nodes > Server node > +Add New Server node > Central

### ADVANCED
Host white list > Add New Value > YOUR SERVER NAME


### LINK PROXIES
This process is done last as earlier mentioned to ensure that the link between the existing Central proxy and newly created Virtual proxy will work properly.

QMC > Proxies > Virual Proxies, Central (Default)  > Associate Items > Virtual Proxies > SER > +Add > Link Existing > ser

## SECURITY RULES CREATION

### Add Shared Content Rule

QMC > MANAGE RESOURCES > Security Rules > + Create new
### IDENTIFICATION
|Setting |Value
------------------|------------------
|Name |_sharedContent* |
|Create Rule from Template | Unspecified|
|Disabled | Leave Unchecked|
|Description ||

### BASIC
|Setting         |Value     |   |
|----------------|----------|---|
|Resource Filter |SharedContent_* |   |
|Actions         |Read, Update, Change Owner     |   |
|User            |name      |=  |
|Value           |YOUR QLIK USER NAME |   |

### ADVANCED

Conditions		((user.name="YOUR QLIK USER NAME"))
Context			Both in hub and QMC			

Validate Rule > Add Rule

### Add SER License rule

QMC > MANAGE RESOURCES > Security Rules > + Create new > SER License

### IDENTIFICATION
|Setting |Value
------------------|------------------
|Name | SER License|
|Create Rule from Template | Unspecified|
|Disabled | Leave Unchecked|
|Description ||

### BASIC
|Setting |Value|
---|---|
|Resource Filter | License_*|
|Actions | Read ||

### ADVANCED
Add the below value manually into the Conditions table:

|Setting |Value
------------------|------------------
|Conditions | !user.IsAnononymous()|
|Context | Both in hub and QMC|

Validate Rule > Add Rule


### Add SER Scheduler Rule

QMC > MANAGE RESOURCES > Security Rules > + Create new > SER Scheduler

### IDENTIFICATION

Setting |Value
------------------|------------------
Disabled | Leave Unchecked |
Name | SER Scheduler|
Create Rule From Template | App Access|
Description ||

### BASIC

Setting |Value
------------------|------------------
Resource Filter | App_*|
Actions | Check Read|
|User |name | =
|Value |ser_scheduler|
| OR|||
|user | userDirectory  = |
|value | INTERNAL|

Conditions field in the ADVANCED section below is automatically populated by the above selections 

### *ADVANCED*
Setting |Value
----------|---------------
|Conditions | ((user.name="ser_scheduler" or user.userDirectory="INTERNAL"))|

Validate Rule > Add Rule

## INSTALL DEMO CONTENT

###  INSTALL DEMO APPS TO APP LIBRARY

From the C:\Reporting\Apps directory install the following files to the QMC App Library.

Executive Dashboard Connector.qvf
Executive Dashboard.qvf

QMC > MANAGE CONTENT > APPS > Import app > Choose FIle >Executive Dashboard Connector.qvf

QMC > MANAGE CONTENT > APPS > Import app > Choose FIle >Executive Dashboard.qvf


###  INSTALL DEMO REPORT TEMPLATE TO CONTENT LIBRARY


 1. Download ExecutiveDashboard.xlsx from the App Contents of the Executive Dashboard App in the QMC.

QMC > MANAGE CONTENT > Apps > Executive Dashboard > App contents (check) > ExecutiveDashboard.xlsx

2. Upload the ExecutiveDashboard.xlsx file to the senseexcelreports content library.

QMC > MANAGE CONTENT > Content libraries > senseexcelreports > Upload > Choose Files >ExecutiveDashboard.xlsx


##  ON DEMAND REPORTS DEMO

1. Open the Executive Dashboard App from the Hub

2. Choose the Accounts Receivable tab

3. Use the Edit Function to choose the parameters of the report you would like to run,

4. Click on the widget with the Generate Report Button

5. Open the Configuration Tab

6. Choose from the Library dropdown list where you would like to run the report from.  Choices are the senseexcelreports content library or InApp which will let you choose from templates that are attached to the app itself.

7. Choose the ExceutiveDashboard.xlsx from the Content dropdown list.

8. Choose the Output Format. Excel or PDF

9. Chose the Selection Mode.  Selection over Shared Session or Selection Over Book Mark. 

Shared session will display the report running in an animated fashion on the screen.  

Selection over Book Mark will perform report processing in the background.

 10.   Choose Direct Download On or Off

Direct Download On will open the report automatically in either your default PDF viewer or in Excel

Direct Download off will require the Download Report button to be pushed.

11. Hit the Done Key.

12. Choose the region you would like to have the report run for in the Region filter pane.  The associated segments will update based on that selection.

13. Hit the Generate Report Button to execute the report.

The demo app is set to generate a Title Page a Summary Page a seperate Detail page for Each Segment Selected.



##  SCHEDULED REPORTS DEMO

 1. Open the Executive Dashboard Connector App from the HUB.

 2. Press open on the This app contains no data dialogue box if it appears.  If it doesn't appear hit the Edit Script button.

 3. Confirm that the Data Connections Attached Files includes the ExecutiveDashboard.xlsx file.  If it doesn't download it from the senseexcelreports or the Executive Dashboard app as described earlier and attach it here.

 4.  Create a new data connection called SERReports.  Make the path C:\Reporting\SERReports.

 5. Open Data Connections section of the QMC.  Choose the SERReports connection and remove the appended user information from the connection name.   

 6. Save the connection.

 7.  Return to the Executive Dashboard Connector App. Press the Save button.  Confirm that the SERReports connection has the appended user information removed.

 8.   Change the following parameters in the script:

 To change the App that the job will run on.

**app:  Executive Dashboard AppID from QMC**  

To Choose the Template that the job will run on.  /// will use the associated content library.  // will use a discreet path.

**input: content:///ExecutiveDashboard.xlsx**

To define report output parameters (optional for Demo app)

output: ='Report_'&only(Region)&'_'&max([Fiscal Year])&'.pdf'
		
	selections:[
	{
		type: static
		objectType: field
		name: Fiscal Year
		values: =[Fiscal Year]=(Year(ToDay())-4)
	}
	{
		type: Dynamic
		name: Region
	}
	]
  }

To set the locations that the reports will be sent when processed:

Below will send the output to the file location referenced in the Data Connection and defined as a target path at the beginning of the install process.

**target: =lib://SERReports'**
	
Define the user for delivery via the Qlik Sense Hub

**Settings for upload in the Qlik hub**

**owner: Domain\User**


10.  Once all parameters are set, hit the Load Data button to execute the script and run the distribution job.
EXCEL_NAME;DOMAIN\USER1

EXCEL_NAME;DOMAIN\USER2;FROM;TO

EXCEL_NAME;DOMAIN\USER3;FROM;TO

EXCEL_NAME;DOMAIN\USER4;FROM;TO

EXCEL_NAME;DOMAIN\USER5;FROM;TO


 6. . Save file with name license.txt.
 
 7.  Upload the license.txt file to the senseexcel content library.

QMC > MANAGE CONTENT > Content Libraries > senseexcel >Upload > license.txt

 8. A required security rule for this content library is defined in the ADD SECURITY RULES section later in this document.


##  *ADD ANALYTIC CONNECTION*
 
Define the name, Host, Port, Reconnect Timeout and Reg Timeout parameters

QMC > MANAGE CONTENT > Analytic Connections > + Create New

|Setting|Value|
------|--------------
|Name | ser
|Host | localhost
|Port | 50059|
|Reconnect Timeout|30
|Request Timeout|30|

##  *ADD VIRTUAL PROXY*
In this section you will define a new Virtual Proxy and then link it to the Main Proxy.  This operation MUST be done in a particular order. 

Create the Virtual Proxy via the QMC’s Virtual Proxy menu first. To ensure that the links will work properly DO NOT utilize the Create New Virtual Proxy technique within the QMC Proxy Menu. 

QMC > CONFIGURE SYSTEM > Virtual proxies > + Create new

Once the new virtual proxy is created, confirm the following Properties are checked in the Dialogue Box on the right side of your screen.

Identification
Authentication
Load Balancing
Advanced

### *IDENTIFICATION SECTION*

|Setting|Value|
|--|--|
|Description  |ser
|Prefix| ser 
Session inactivity timeout | 30
Session cookie header name | X-Qlik-Session-ser|


### *AUTHENTICATION*
|Setting|Value|
|--|--|
|Anonymous access mode | No anonymous user   |
|Authentication method | JWT|
JWT certificate | -----BEGIN CERTIFICATE-----|
|JWT attribute for user ID | UserID|
|JWT attribute value for user directory | UserDirectory


### LOAD BALANCING

Load Balancing nodes > Server node > +Add New Server node > Central

### ADVANCED
Host white list > Add New Value > YOUR SERVER NAME


### LINK PROXIES
This process is done last as earlier mentioned to ensure that the link between the existing Central proxy and newly created Virtual proxy will work properly.

QMC > Proxies > Virual Proxies, Central (Default)  > Associate Items > Virtual Proxies > SER > +Add > Link Existing > ser

## SECURITY RULES CREATION

### Add Shared Content Rule

QMC > MANAGE RESOURCES > Security Rules > + Create new
### IDENTIFICATION
|Setting |Value
------------------|------------------
|Name |_sharedContent* |
|Create Rule from Template | Unspecified|
|Disabled | Leave Unchecked|
|Description ||

### BASIC
|Setting         |Value     |   |
|----------------|----------|---|
|Resource Filter |SharedContent_* |   |
|Actions         |Read, Update, Change Owner     |   |
|User            |name      |=  |
|Value           |YOUR QLIK USER NAME |   |

### ADVANCED

Conditions		((user.name="YOUR QLIK USER NAME"))
Context			Both in hub and QMC			

Validate Rule > Add Rule

### Add SER License rule

QMC > MANAGE RESOURCES > Security Rules > + Create new > SER License

### IDENTIFICATION
|Setting |Value
------------------|------------------
|Name | SER License|
|Create Rule from Template | Unspecified|
|Disabled | Leave Unchecked|
|Description ||

### BASIC
|Setting |Value|
---|---|
|Resource Filter | License_*|
|Actions | Read ||

### ADVANCED
Add the below value manually into the Conditions table:

|Setting |Value
------------------|------------------
|Conditions | !user.IsAnononymous()|
|Context | Both in hub and QMC|

Validate Rule > Add Rule


### Add SER Scheduler Rule

QMC > MANAGE RESOURCES > Security Rules > + Create new > SER Scheduler

### IDENTIFICATION

Setting |Value
------------------|------------------
Disabled | Leave Unchecked |
Name | SER Scheduler|
Create Rule From Template | App Access|
Description ||

### BASIC

Setting |Value
------------------|------------------
Resource Filter | App_*|
Actions | Check Read|
|User |name | =
|Value |ser_scheduler|
| OR|||
|user | userDirectory  = |
|value | INTERNAL|

Conditions field in the ADVANCED section below is automatically populated by the above selections 

### *ADVANCED*
Setting |Value
----------|---------------
|Conditions | ((user.name="ser_scheduler" or user.userDirectory="INTERNAL"))|

Validate Rule > Add Rule

## INSTALL DEMO CONTENT

###  INSTALL DEMO APPS TO APP LIBRARY

From the C:\Reporting\Apps directory install the following files to the QMC App Library.

Executive Dashboard Connector.qvf
Executive Dashboard.qvf

QMC > MANAGE CONTENT > APPS > Import app > Choose FIle >Executive Dashboard Connector.qvf

QMC > MANAGE CONTENT > APPS > Import app > Choose FIle >Executive Dashboard.qvf


###  INSTALL DEMO REPORT TEMPLATE TO CONTENT LIBRARY


 1. Download ExecutiveDashboard.xlsx from the App Contents of the Executive Dashboard App in the QMC.

QMC > MANAGE CONTENT > Apps > Executive Dashboard > App contents (check) > ExecutiveDashboard.xlsx

2. Upload the ExecutiveDashboard.xlsx file to the senseexcelreports content library.

QMC > MANAGE CONTENT > Content libraries > senseexcelreports > Upload > Choose Files >ExecutiveDashboard.xlsx


##  ON DEMAND REPORTS DEMO

1. Open the Executive Dashboard App from the Hub

2. Choose the Accounts Receivable tab

3. Use the Edit Function to choose the parameters of the report you would like to run,

4. Click on the widget with the Generate Report Button

5. Open the Configuration Tab

6. Choose from the Library dropdown list where you would like to run the report from.  Choices are the senseexcelreports content library or InApp which will let you choose from templates that are attached to the app itself.

7. Choose the ExceutiveDashboard.xlsx from the Content dropdown list.

8. Choose the Output Format. Excel or PDF

9. Chose the Selection Mode.  Selection over Shared Session or Selection Over Book Mark. 

Shared session will display the report running in an animated fashion on the screen.  

Selection over Book Mark will perform report processing in the background.

 10.   Choose Direct Download On or Off

Direct Download On will open the report automatically in either your default PDF viewer or in Excel

Direct Download off will require the Download Report button to be pushed.

11. Hit the Done Key.

12. Choose the region you would like to have the report run for in the Region filter pane.  The associated segments will update based on that selection.

13. Hit the Generate Report Button to execute the report.

The demo app is set to generate a Title Page a Summary Page a seperate Detail page for Each Segment Selected.



##  SCHEDULED REPORTS DEMO

 1. Open the Executive Dashboard Connector App from the HUB.

 2. Press open on the This app contains no data dialogue box if it appears.  If it doesn't appear hit the Edit Script button.

 3. Confirm that the Data Connections Attached Files includes the ExecutiveDashboard.xlsx file.  If it doesn't download it from the senseexcelreports or the Executive Dashboard app as described earlier and attach it here.

 4.  Create a new data connection called SERReports.  Make the path C:\Reporting\SERReports.

 5. Open Data Connections section of the QMC.  Choose the SERReports connection and remove the appended user information from the connection name.   

 6. Save the connection.

 7.  Return to the Executive Dashboard Connector App. Press the Save button.  Confirm that the SERReports connection has the appended user information removed.

 8.   Change the following parameters in the script:

 To change the App that the job will run on.

**app:  Executive Dashboard AppID from QMC**  

To Choose the Template that the job will run on.  /// will use the associated content library.  // will use a discreet path.

**input: content:///ExecutiveDashboard.xlsx**

To define report output parameters (optional for Demo app)

output: ='Report_'&only(Region)&'_'&max([Fiscal Year])&'.pdf'
		
	selections:[
	{
		type: static
		objectType: field
		name: Fiscal Year
		values: =[Fiscal Year]=(Year(ToDay())-4)
	}
	{
		type: Dynamic
		name: Region
	}
	]
  }

To set the locations that the reports will be sent when processed:

Below will send the output to the file location referenced in the Data Connection and defined as a target path at the beginning of the install process.

**target: =lib://SERReports'**
	
Define the user for delivery via the Qlik Sense Hub

**Settings for upload in the Qlik hub**

**owner: Domain\User**


10.  Once all parameters are set, hit the Load Data button to execute the script and run the distribution job.

This is complete integration between salesforce and Onedrive.

Azure setup steps-

Login in Microsoft azure portal - https://portal.azure.com/#view/Microsoft_AAD_RegisteredApps/ApplicationsListBlade

Now Go to app registration and create an connected app.

Give these api permissions- 
Files.Read, Files.Read.All, Files.ReadWrite, Files.ReadWrite.All, Files.ReadWrite.All, Files.ReadWrite.AppFolder, Files.ReadWrite.AppFolder, Files.SelectedOperations.Selected, 
offline_access, Sites.FullControl.All, Sites.Read.All, Sites.ReadWrite.All, User.Read

Now Save the following id-
Client ID, Client Credential, tenent id

Now Save the following endpoints-
OAuth 2.0 token endpoint (v2), OAuth 2.0 authorization endpoint (v2)

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Requirement 2-- Now we add one more condition in previous LWC component that it accept Multiple PDF as well upto 10pdf at onces. 
For e.g PDF name- T123456.pdf, Upwork transaction record names e.g - 123456, onedrive folder name e.g - Bank Transfer for 900000.04 INR to xxxx-0938 Dated 15 Nov 24

Single PDF case-
When we are uploading PDF called T123456.pdf, then it checks that 123456 record is present in upwork transaction or not, if present then checks Transaction date field of record with latest 
last onedrive folder name. If the date is lesser then onedrive folder then it uploads pdf in exesting folder and  if the date is greater then it create a new folder and upload the pdf in it.

Onedrive Folder Naming logic- Description field + Dated + Transaction date

Multiple PDF case- If we are uploading 10 pdfs at onces then it checks those 10 records are present or not if present then it exatracts the higest trascation date records from all records then it
then it check this transaction date with onedrive folder date and same previous logic.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

We have to create following things-\

Create a object in salesforce-
Object Name- Access Token(Accesstoken__c)  Field- AccessToken(AccessToken__c)      Data Type-Long Text Area(32768)

Create a Site - 
Go to setup -> search site -> Inside user interface -> go to site -> Create a new site -> 
Add your sandbox url just add /test after .com - in my case I have use this URL- (makediansoftechsolutions--account.sandbox.my.salesforce-sites.com/test)

Create a remote site settings -
Go to setup -> search remote site settings -> open -> create new -> 
Now add this URL(https://login.microsoftonline.com)

Important part-
Now add this URL into the microsoft app which we have create earlier, inside the redirect url.


After these steps go to integration file.

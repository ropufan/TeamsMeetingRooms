# Configuring an HTTPS webhook in Azure

More in-depth technical documentation is available [here](https://learn.microsoft.com/en-us/partner-center/marketplace/partner-center-portal/commercial-marketplace-lead-management-instructions-https)

## Create Resource Group

![Create a Resource Group](./../images/logicapp/1-rg.png "")

## Create a Logic App

![Search for Logic App](./../images/logicapp/2-lgcapp.png "")
![Create a new Logic App](./../images/logicapp/3-lgcappsetup.png "")

## Go to Logic App Designer and configure the trigger

![Go to Logic App Designer & Create a new HTTP request Logic App](./../images/logicapp/4-lgcappnew.png "")
![Use a Sample payload to generate the schema](./../images/logicapp/5-lgcappsample.png "")
![The sample payload should look like this](./../images/logicapp/6-payloadsample.png "")

## Connect to Outlook from Office 365

![Add a new step to the Logic App](./../images/logicapp/7-newstep.png "")
![Select Outlook as a LogicApp Connector](./../images/logicapp/8-outlook.png "")
![Select the correct action - Send Email V2](./../images/logicapp/9-sendemail.png "")
![Log in with the O365 account](./../images/logicapp/10-login.png "")

## Define the Email action

![Configure the email](./../images/logicapp/11-emailbody.png "")

Subject:

```markdown
New Microsoft Lead: @{triggerBody()?['OfferTitle']} /  @{triggerBody()?['UserDetails']?['Company']}
```

Body:

```markdown
Hello!

You just received a new lead from @{triggerBody()?['UserDetails']?['Company']} from @{triggerBody()?['UserDetails']?['Country']}!

You should contact the following person:
First name:@{triggerBody()?['UserDetails']?['FirstName']}
Last name: @{triggerBody()?['UserDetails']?['LastName']}
Job Title@{triggerBody()?['UserDetails']?['Title']}
Email@{triggerBody()?['UserDetails']?['Email']}
Phone Number@{triggerBody()?['UserDetails']?['Phone']}

Thank you,
The Microsoft Commercial Marketplace Automation
```

## Output

![Get the URL for the Webhook](./../images/logicapp/12-url.png "")

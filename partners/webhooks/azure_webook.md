# Configuring an HTTPS Webhook in Azure

This documentation provides a step-by-step guide on how to configure an HTTPS webhook using **Azure Logic Apps**. By following these instructions, you will be able to create a webhook that sends you an email whenever a new lead is received from the Microsoft Commercial Marketplace.

**Azure Logic Apps** has a `Consumption Plan` billing model. This means that you will only pay for the resources that you use, and you will not be charged when the Logic App is not being triggered. At the moment of writing this, each `Consumption Plan` comes with the first 4000 actions for free. The updated pricing details can be checked out [here](https://azure.microsoft.com/en-us/pricing/details/logic-apps/).

## Introduction to Webhooks

Webhooks serve as a communication mechanism between websites and applications, enabling them to automatically send messages to each other when specific events occur. It's similar to having a magical mailbox that notifies you whenever something important happens outside your house. For example, webhooks can be used to receive notifications about new social media messages, online store purchases, and even leads from the Commercial Marketplace. They streamline communication and facilitate seamless interaction between different parts of the internet.

## Prerequisites

Before you proceed with following the guide, make sure you have the following prerequisites:

- An Azure Subscription, with provisioning rights
- An Office 365 account, with email access

## Step-by-step Guide

### Step 1: Create a Resource Group

1. Go to Azure Portal and [create a new Resource Group](https://portal.azure.com/#create/Microsoft.ResourceGroup)
2. Specify the **Azure Subscription**, **Resource Group name**, and the **Region** where the Resource Group will reside

    ![Create a Resource Group](./../images/logicapp/0-rgcrt.png "")

3. Click on **Review + Create** and then **Create** to create the Resource Group

### Step 2: Create a Logic App

1. Inside the Resource Group you have created, you will need to [create a Logic App](https://portal.azure.com/#create/Microsoft.LogicApp)

2. The **Logic App** resource settings that you will need to make, *in the order of setting up*, are:

   - **Plan Type**, which is the model of deployment (recommended: `Consumption`)
   - the `Azure Subscription` that you will use
   - the `Resource Group` in which this `Logic App` will reside
   - the `Name` of the `Logic App` that you will be creating
   - the `Region` in which this `Logic App` will reside
   - if you want to enable `Log Analytics` (optional)

    ![Create a new Logic App](./../images/logicapp/3-lgcappsetup.png "")

3. Click on "Review + Create" and then "Create" to create the Logic App.

### Step 3: Go to Logic App Designer and configure the trigger

1. After creating the Logic App, go to the Logic App Designer
2. Select "When an HTTP request is received" as the trigger for the Logic App

    ![Go to Logic App Designer & Create a new HTTP request Logic App](./../images/logicapp/4-lgcappnew.png "")

3. Select the *Use a sample payload to generate the schema* option

    ![Use a Sample payload to generate the schema](./../images/logicapp/5-lgcappsample.png "")

4. Provide the following example JSON:

    ```json
    {
    "UserDetails": {
        "FirstName": "Some",
        "LastName": "One",
        "Email": "someone@contoso.com",
        "Phone": "16175555555",
        "Country": "USA",
        "Company": "Contoso",
        "Title": "Esquire"
    },
    "LeadSource": "AzureMarketplace",
    "ActionCode": "INS",
    "OfferTitle": "Test Microsoft",
    "Description": "Test run through Logic App"
    }
    ```

    ![The sample payload should look like this](./../images/logicapp/6-payloadsample.png "")

5. Click on "Done" to generate the Request Body JSON Schema
6. Verify that the Body JSON was created and add a new step to the Logic App

    ![Add a new step to the Logic App](./../images/logicapp/7-newstep.png "")

### Step 4: Connect to Outlook from Office 365

1. In the new step, select "Outlook" as the connector

    ![Select Outlook as a LogicApp Connector](./../images/logicapp/8-outlook.png "")

2. Search for and select the action "Send an email V2."

    ![Select the correct action - Send Email V2](./../images/logicapp/9-sendemail.png "")

3. Log in with your Office 365 account, which will be used to send the emails

    ![Log in with the O365 account](./../images/logicapp/10-login.png "")

### Step 5: Define the Email action

1. Define the structure of the email to be sent when the webhook is called with a valid query
2. Customize the "To," "Subject," and "Body" fields according to your preferences. Here's an example:

    Subject:

    ```json
    New Microsoft Lead: @{triggerBody()?['OfferTitle']} /  @{triggerBody()?['UserDetails']?['Company']}
    ```

    Body:

    ```json
    Hello!

    You received a new lead from @{triggerBody()?['UserDetails']?['Company']} from @{triggerBody()?['UserDetails']?['Country']}!

    You should contact the following person:
    First name:@{triggerBody()?['UserDetails']?['FirstName']}
    Last name: @{triggerBody()?['UserDetails']?['LastName']}
    Job Title@{triggerBody()?['UserDetails']?['Title']}
    Email@{triggerBody()?['UserDetails']?['Email']}
    Phone Number@{triggerBody()?['UserDetails']?['Phone']}

    Thank you,
    The Microsoft Commercial Marketplace Automation
    ```

3. If you paste the above values in the fields, you should get something like this:

![Configure the email](./../images/logicapp/11-emailbody.png "")

### Step 6: Save & get the Webhook URL

1. Save the Logic App, which will trigger the creation of the Webhook URL
2. Go to the "When an HTTP request is received" step to find the URL for your configured webhook
3. Copy the Webhook URL and use it in the **Webhook URL**"** field in the Microsoft Commercial Marketplace Automation form

    ![Get the URL for the Webhook](./../images/logicapp/12-url.png "")

These steps will guide you through the process of configuring an HTTPS webhook using **Azure Logic Apps**. By implementing this webhook, you will be able to receive email notifications whenever new leads are received from the Microsoft Commercial Marketplace.

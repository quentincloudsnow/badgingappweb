# RPA Hub Lab

## Introduction

RPA Hub enable end-to-end automation for your organization. With a combination of UI interactions and element-based automations that interact between the various business applications, you can emulate user actions and eliminate mundane and repetitive human activities. Any ServiceNow's RPA Automation can be triggered from any Worlfow on the ServiceNow Platform, this allows to automate things that do not have protocal available such as REST API, SOAP, ssh, powershell etc. 

## Goal 

In this lab, we will automate the task of printing a visitor badge. We will place special emphasis on the recorder capabilities that can capture actions from your desktop or web applications and convert them into an automation flow using the recorder option in the RPA Desktop Design Studio application. When you record an automation, you won't need to create it manually using connectors or components. This is especially useful for new user who have never built an RPA project. Additionally, we will review some administrative aspects of the RPA Hub within the dedicated RPA Hub Workspace, including configuring the Bot process and managing required credentials.

## Use Case

ACME Inc. has a mandate to automate as much as possible within their organization to drive efficiency and reduce costs. They have identified the 'Visitor Access' process as highly repetitive and labor-intensive. As a member of ACME Inc.'s Automation Center of Excellence, you have been contacted to automate the task of a security agent printing a visitor badge.

The requirement is that this automation can be triggered by a ServiceNow workflow. ACME Inc. is using ServiceNow to modernize the experience for their employees and customers and to orchestrate end-to-end automation.

The Badging Application is a web-based application and does not have an API. Agents receive visitor information via email and then access the web interface to populate the Badge Printing form wich result in a lot of manual error, typo and delay for visitor waiting for their badge.


### Reviewing the badgine application

From a web browser, open that [Link](https://automationengine.westus2.cloudapp.azure.com) to access the web-based badging application. Afterward, you should see the authentication screen below.

![Alt text](img/2023-10-02_08-23-29.png)

Type this credentials to authenticate then click Submit:

| Field | type |
   |-------|-------|
   | Username | badgeadmin |
   | Password | badgeadmin |

You should see that page below that Security Agent use to print badge

![Alt text](img/2023-10-02_08-28-54.png)

In our RPA automation project, we will automate all of those steps: opening the web browser, authenticating, performing the data entry, and submitting the form.

### RPA Hub Workspace

In the following step, we will perform some administrative tasks within the RPA Hub Workspace so that you can familiarize yourself with the various available configurations. Please log in to the instance assigned to you using the admin credentials you received when claiming that instance.

Click **All** (1), then type **RPA Hub** in the filter navigator (2) then click **RPA Hub Workspace

![Alt text](img/2023-10-02_08-41-05.png)

RPA Hub workspace is were govern, manage, and supervise your digital workforce all from one place.

In the top left-hand corner, click on the 'hamburger' icon to view the available lists

![Alt text](img/2023-10-02_08-44-35.png)

Click **Bot Process** (1) then **Assign Configuation** (Click the little arrow bext **Create Configuration**)

![Alt text](img/2023-10-02_08-50-15.png)

We are now creating a new **Bot process** from an existing **bot process configuration** and then we will populate the remaining fields required for it

Check the box (1) to select the **Badge printing - Bot process configuration** record then click **submit** (2)

![Alt text](img/2023-10-02_08-52-51.png)

> This Badge Printing Bot process configuration record was preloaded in those lab instances to save time for the lab, allowing us to quickly focus on building the robot!"! Those configuration record are useful for customers that have multiple instances and needs to export the configuration from one instance to another.

This tab should open in the workspace, showing the bot process record, update the **Name** field (1) to rename the Bot Process. remove config then click **Save** (2) 

![Alt text](<img/2023-10-02_08-57-01 (1).png>)

You want the Bot process **name** field to be as shown:

![Alt text](img/2023-10-02_08-59-55.png)

Now that we have this new Badge Pringing bot process record created, lets populate some fields that are important., Click on the **Business Applications** Tab

![Alt text](img/2023-10-02_09-02-47.png)

> Note: This aspect of the configuration is extremely important. In the Business Application tab, we will establish a relationship between the Bot Process and the RPA automation we are creating, connecting it to the specific Business Application we are automating. This configuration is stored in the CMDB (Configuration Management Database), enabling customers to keep their Automation team informed when planning changes to these business applications. Consider a scenario where one team is altering the UI of the Badging Application while another team is automating that UI. 
Another benefit of maintaining this relationship in the CMDB is that when an incident occurs in that application, it can be correlated with potential errors within the automation. Imagine if the business application goes down; the RPA robots may cease to function. Having visibility into potential root causes can be highly valuable."

Click **Add** to  map the existing Business Application (from CMDB) to the Bot Process

![Alt text](img/2023-10-02_09-11-02.png)

Select the **Badge Printing** (1)  Business application then click **Add** (2)

![Alt text](img/2023-10-02_09-12-30.png)

If you don't see the Busuness Application after adding it, clicl that recycle button as shown

![Alt text](img/2023-10-02_09-13-57.png)

then you should see it in the Business Application tab as shown

![Alt text](img/2023-10-02_09-15-03.png)

Lets continue with the configuration of the bot process, click on the **Credentials Set** tab (1), then click **New** (2)

![Alt text](img/2023-10-02_09-17-26.png)

keep that tab open, we need to go grab additional information that we re goin to use in those field.

![Alt text](<img/2023-10-02_09-19-27 (1).png>)

We need to grab the hostname of the Windows Virtual Machnine that was assigned to you, it just happened to be the same machine as the MID Server deployed with your instance

Click **All** (1) then type **mid** (2) in the filter navigator, then mouse over **Servers** then right click **Open Link in a new Tab** (just so we can keep the bot process page open)

![Alt text](img/2023-10-02_09-21-44.png)

From that new tab, copyin your clipboard the value you see in the **Host Name** column as shown

![Alt text](img/2023-10-02_09-25-17.png)

Then return to the Credentials Set tab in the RPA workspace

In the name field, past the previsouly copied value (hostname of mid server), then also in the Windows Username, past the hostname value followed by \Administrator

In the **windows password** field, type the password that was provided to you when you have claimed that lab instance then click **Save**

![Alt text](<img/2023-10-02_09-28-16 (1).png>)

You show see a screen similar to this, allowing you to set the Application Credentials that will be use for that process (this is where we store the credentials for the robot to authenticate to that web badging app interface)

Click on **Application Credentials**

![Alt text](img/2023-10-02_09-31-27.png)

Then clicl k **New**

![Alt text](img/2023-10-02_09-33-12.png)
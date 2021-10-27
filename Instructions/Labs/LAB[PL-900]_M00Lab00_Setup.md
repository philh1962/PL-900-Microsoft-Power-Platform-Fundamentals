---
lab:
    title: 'Lab: Validate lab environment'
    module: 'Module 0: Course introduction'
---

Module 0: Course introduction
=================================

## Lab: Validate lab environment

### Important Notice (Effective November 2020):
Common Data Service has been renamed to Microsoft Dataverse. Most terminology in Microsoft Dataverse has been updated. For example, entity (now **table**), field (now **column**), and record (now **row**) may be out of date. It may help new users to think in terms of "entity tables"  "field columns" and "record rows." Please keep this in mind as you work through the labs. Microsoft content is expected to be fully up to date very soon. 

For more information and for a complete list of affected terms, please visit [What is Microsoft Dataverse?](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/data-platform-intro#terminology-updates)

Scenario
--------

Bellows College is an educational organization with multiple buildings on campus. Campus visitors are currently recorded in paper journals. The information is not captured consistently, and there are no means to collect and analyze data about the visits across the entire campus.

Campus administration would like to modernize their visitor registration system where access to the buildings is controlled by security personnel and all visits are required to be pre-registered and recorded by their hosts.

Throughout this course, you will build applications and perform automation to enable the Bellows College administration and security personnel to manage and control access to the buildings on campus.

In this lab, you set up a Portal that we will use in future labs.  This provisioning can run in the background, but can take up to an hour.

# Exercise \#1: Provision a Power Apps portal

**Objective:** Provisioning a Power Apps portal can take some time. In this exercise, you will create your Power Apps portal in your environment so that the provisioning process can be initiated. You will use this portal in a later lab.

## Task \#1: Create Power Apps portal

1.  Use your tenant credentials username and password to set up a Sales Trial in Dynamics365 in an Incognito or Private browser window.  This create a new environment in your tenancy called **Sales Trial**, containing the various sales apps.  

2.  Sign in to <https://make.powerapps.com>.  This opens the Power Apps maker portal.  

2.  If the **Environment** displayed in the top right is not your **Sales Trial** environment, click to select this environment.

3.  On the Home page, click on the **New app** then **Portal** panel

4.  Provide new portal details

    -   Enter **```Bellows College Visitors```** as the portal **Name**

    -   Provide a unique URL; **something**.powerappsportals.com (if the name has been taken, choose a different one - perhaps using your initials)

    -   Select a base portal **Language**

    - Leave the **Use data from existing website record** checkbox blank.

    -   Click **Create**

    > The Portal provisioning process will run anywhere from 30 to 45 minutes. You do not have to wait, as this will continue while we move on to the next module.

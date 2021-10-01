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

In this Module 0 lab, you will access the Power Platform admin center and create your **Practice** environment that you will do the majority of your lab work in.

## Exercise 1 – Setup

### Task \#1 – Create environment

1.  Access <https://admin.powerplatform.microsoft.com> and log in with your Microsoft 365 credentials if prompted again.

2. Select **Environments** and click **+New.**

    - For **Name**, enter **[My Initials] Practice.** (Example: AJ Practice.)
    
    - For **Type**, select **Trial** (do not select the Trial (subscription-based) option).
    
    - Change the toggle on **Create a database for this environment?** to **Yes.**
    
    - Leave all other selections as default and click **Next.**
    
    - On the next tab, leave all selections to default and click **Save.**

3. Your **Practice** environment should now show in the list of Environments. 

    > Your environment may take a few minutes to provision. Refresh the page if needed.

# Exercise \#2: Provision a Power Apps portal

**Objective:** Provisioning a Power Apps portal can take some time. In this exercise, you will create your Power Apps portal in your environment so that the provisioning process can be initiated. You will use this portal in a later lab.

## Task \#1: Create Power Apps portal

1.  Sign in to <https://make.powerapps.com>

2.  If the **Environment** displayed in the top right is not your Practice environment, click to select your Environment.

3.  On the Home page, click on the **Create** then **Portal from blank** panel

    > If you do not see this option, try zooming out.

4.  Provide new portal details

    -   Enter **```Bellows College Visitors```** as the portal **Name**

    -   Provide a unique URL; **something**.powerappsportals.com (if the name has been taken, choose a different one - perhaps using your initials)

    -   Select a base portal **Language**

    -   Click **Create**

    > The Portal provisioning process will run anywhere from 30 to 45 minutes. You do not have to wait, as this will continue while moving on to the next module.

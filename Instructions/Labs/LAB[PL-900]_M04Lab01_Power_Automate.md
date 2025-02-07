---
lab:
    title: 'Lab 6: How to build an automated solution'
    module: 'Module 4: Get Started with Power Automate'
---

# Module 4: Get Started with Power Automate
## Lab: How to build an automated solution

### Important Notice (Effective November 2020):
Common Data Service has been renamed to Microsoft Dataverse. Some terminology in Microsoft Dataverse has been updated. For example, entity (now **table**), field (now **column**), and record (now **row**) may be out of date. Please keep this in mind as you work through the labs. We expect to have our content fully up to date very soon.

For more information and for a complete list of affected terms, please visit [What is Microsoft Dataverse?](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/data-platform-intro#terminology-updates)

## Scenario

Bellows College is an educational organization with multiple buildings on campus. Campus visitors are currently recorded in paper journals. The information is not captured consistently, and there are no means to collect and analyze data about the visits across the entire campus. 

Campus administration would like to modernize their visitor registration system where access to the buildings is controlled by security personnel and all visits are required to be pre-registered and recorded by their hosts.

Throughout this course, you will build applications and perform automation to enable the Bellows College administration and security personnel to manage and control access to the buildings on campus. 

In this lab, you will create Power Automate flows to automate various parts of the campus management. 

# High-level lab steps

The following have been identified as requirements you must implement to complete the project:

* The unique code assigned to each visitor must be made available to them prior to their visit.
* Security personnel need to receive notifications of visitors overstaying their scheduled timeslots.

## Prerequisites

* Completion of **Module 0 Lab 0 - Validate lab environment**
* Completion of **Module 2 Lab 1 - Introduction to Microsoft Dataverse**
* Campus Staff app created in **Module 3 Lab 2 – How to build a canvas app, part 2** (for testing)
* John Doe contact created with a personal email address in **Module 3 Lab 4 - How to build a model-driven app** (for testing)

## Things to consider before you begin

-   What is the most appropriate distribution mechanism for the visitor codes?
-   How could overstays be measured and strict policies enforced?

# Exercise \#1: Create Visit Notification flow

**Objective:** In this exercise, you will create a Power Automate flow that implements the first requirement. The visitor should be sent an email that includes the unique code assigned to the visit.

## Task \#1: Create flow

1.  Open your Campus Management solution.

    -   Sign in to <https://make.powerapps.com>

    -   Select your **Sales Trial environment.**

    -   Select **Solutions**.

    -   Click to open your **Campus Management** solution.

2.  Click **New** and select **Cloud flow**. This will open the Power Automate flow editor in a new window.  (If you are using the Solution preview option, you will need to select **New > Automation > Cloud flow > Automated**) Give it the flow name of Visit notification, and choose the trigger below).

3. Select for **Microsoft Dataverse**.

4. Select the trigger **When a row is added, modified or deleted**.

   * Select **Added** for **Change type**
   
   * Select **Visits** for **Table name**
   
   * Select **Organization** for **Scope**
   
   * On the trigger step, click the ellipsis (**...**) and click **Rename**. Rename this trigger **"When a visit is created"**. This is good practice, so you and other flow editors can understand the purpose of the step without having to dive into the details.

5. Select **New Step**. This step is required to retrieve visitors information, including email address.

6. Select **Microsoft Dataverse**.

7. Select **Get a row by ID** action. 

   * Select **Contacts** as **Table name**
   
   * In the **Row ID** field, select **Visitor (Value)** from the Dynamic content list.
   
   * On this action, click the ellipsis (**...**) and click **Rename**. Rename this action **"Get the Visitor"**. This is still a good practice, as before.

8. Click **New Step**. This is the step that will create and send email to the visitor.

9. Search for *email*, select **Send an email V2 Office 365 Outlook** connector and **Send an email notification** action 

   * If asked to Accept terms and conditions for using this action, click **Accept**.
   
   * Select **To** field, select **Email** from the Dynamic content list. Notice that it is beneath the **Get the Visitor** header. This means you are selecting the Email that is related to the Visitor that you looked up in the previous step. 

   * Enter **Your scheduled visit to Bellows College** in the **Subject** field.

   * Enter the following text in **Email Body**:  
        
        > Dynamic content needs to be placed where fields are named in brackets. It is recommended to copy & paste all text first and then add dynamic content in the correct places.
   
        ```
        Dear {First Name},

        You are currently scheduled to visit Bellows Campus from {Scheduled Start} until {Scheduled End}.

        Your security code is {Code}, please do not share it. You will be required to produce this code during your visit.

        Best regards,

        Campus Administration
        Bellows College
        ```
   
10.  Select the **Untitled** flow name at the top and rename it to `Visit notification` if necessary.

11. Press **Save**

    Leave this flow tab open for the next task. With all steps expanded, your flow should look approximately like the following:

![image](https://raw.githubusercontent.com/philh1962/PL-900-Microsoft-Power-Platform-Fundamentals/master/Instructions/Labs/media/revisions/flow2.png)

## Task \#2: Validate and test the flow
Here will will add a new visit using the Campus Staff app and test our flow.

1.  Open a new tab in your browser and navigate to <https://make.powerapps.com> in your Sales Trial environment

2.  Click **Apps** and select the **Campus Staff** app you created

3.  Leaving this tab open, navigate back to the previous tab with your flow. 

4.  On the command bar, click **Test**. Select **Manually** and then **Save & Test**.

5.  Leaving the flow tab open, navigate back to the previous tab with the **Campus Staff** app.

6.  Press **+** to add a new Visit record

7.  Enter **John Doe** as **Name** and choose any **Building**

8.  Choose **John Doe** as the **Visitor** (this will ensure the email goes to your address, as we used it in Lab 3).

9.  Choose the **Scheduled Start** and **Scheduled End Dates** to any dates in the future.

10.  Press the **Checkmark** icon to save the new visit

11.  Navigate back to the previous tab with the flow being tested. Watch as the flow is run. If there are any errors, go back and compare your flow to the example above. If the email is sent successfully, you will receive it in your inbox (it may go into your Junk/Spam folder). 

**Where's my email?** You may find that the email does not arrive - this may be due to security settings in Trial accounts preventing outgoing email.  Open a new tab in your browser and go to **portal.office.com** and select the Outlook icon.  Click on **Sent items**.  You may see the outgoing emails have been rejected by the recipient's email provider.  This is a feature of working in trials, but note that the flow was activated when the record was added, and the email was composed and set out, just not received:

![Email sent](https://raw.githubusercontent.com/philh1962/PL-900-Microsoft-Power-Platform-Fundamentals/master/Instructions/Labs/media/revisions/flow8%20(1).png)

Close the outlook tab.

12.  Click the back arrow on the command bar

13.  Your flow will run whenever a new Visit is created, until you turn it off. Any time the flow runs, you will see it added to the **28-day run history** list.

14.  Turn the flow off by clicking **Turn off** on the command bar. You may need to press the ellipses (**...**) to see this option.

15.  Close this window.

# Exercise #2: Create Security Sweep flow

**Objective:** In order to meet the second design requirement, in this exercise you will create a Power Automate flow that performs a security sweep every 15 minutes, and notifies security if any visitors overstay their scheduled time.  
The previous flow was an automated flow - triggered when a new row was added.  This is a scheduled flow, retrieving data based on the current time.

## Task #1: Create flow to retrieve records

1. Open your Campus Management solution.

   -   Sign in to <https://make.powerapps.com>

   -   Select your **Environment.**

   -   Select **Solutions**.

   -   Click to open your **Campus Management** solution.

2. Click **New** and select **Automation>Cloud flow>Scheduled**. Fill in the new **Flow name** as **Security Sweep**.  Set the Flow to run every 15 minutes, and click **Create**.

3. Click **New step**. Select **Microsoft Dataverse** connector. Select **List rows** action.

   * Enter **Visits** as **Table name**
   
   * Click **Show advanced options**

   * Enter the following expression as **Filter rows**

   ```
     statecode eq 0 and bc_actualstart ne null and bc_actualend eq null and Microsoft.Dynamics.CRM.OlderThanXMinutes(PropertyName='bc_scheduledend',PropertyValue=15)
   ```
   
   * To break it down:
       * **statecode eq 0** filters active visits (where Status equals Active)
       * **bc_actualstart ne null** restricts search to visits where Actual Start has a value, i.e. there was a checkin
       * **bc_actualend eq null** restricts search to visits where there was no check out (Actual End has no value) 
       * **Microsoft.Dynamics.CRM.OlderThanXMinutes(PropertyName='bc_scheduledend',PropertyValue=15)** restricts visits where visits meant to complete more than 15 minutes ago.

   * On this action, click the ellipsis (**...**) and click **Rename**. Rename this action **"List active visits that ended more than 15 minutes ago"**. This is a good practice, so you and other flow editors can understand the purpose of the step without having to dive into the details, as before.

6.  Click **New step**. Search for *Apply*, select **Apply to each** action 

7.  Select **value** from dynamics content in the **Select an output from previous steps** field. Notice that it is beneath the **List active visits that ended more than 15 minutes ago** gray header. This means you are selecting the list of visits that you looked up in the previous step. 

8.  Retrieve Building data for related record

    * Click **Add an action** inside the Apply to Each loop.
    
    * Select **Microsoft Dataverse**. 
    
    * Select **Get a row by ID** action.
    
    * Select **Buildings** as **Table name**
    
    * Select **Building (Value)** as **Row ID** from the Dynamic content. (This will specify the building).
    
    * Click **...** beside **Get a row by ID**, select **Rename**. Enter **Get building** as step name
    
9.  Retrieve Visitor data for related record

    * Click **Add an action** inside the Apply to Each loop.
    
    * Select **Microsoft Dataverse**.
    
    * Select **Get a row by ID** action.
    
    * Select **Contacts** as **Table name**
    
    * Select **Visitor (Value)** as **Row ID** from the Dynamic content.  (This will specify the visitor).
    
    * Click **...** beside **Get a row by ID**, select **Rename**. Enter **Get visitor** as step name
    
11.  Send email notification

     * Click **Add an action** inside the Apply to Each loop. Select **Send an email V2 Office 365 Outlook** connector and **Send an email notification** action.

12.  Enter your email address as **To**

13.  Enter the following in the **Subject** field. **Name** is dynamic content from the **Get building** step.

   ```
   There is an overstay in {Name}.
   ```
   
14.  Enter the following in the **Body** field. **Full Name** is dynamic content from **Get visitor** step.

   ```
   {Full Name} overstayed their welcome   
         
   Best,
         
   Campus Security
   ```

17.  Press **Save**

   With all steps expanded, your flow should look approximately like the following:

![Security sweep scheduled flow part 1a](https://github.com/philh1962/PL-900-Microsoft-Power-Platform-Fundamentals/blob/master/Instructions/Labs/media/revisions/flow4.png)
![Security sweep scheduled flow part 1b](https://raw.githubusercontent.com/philh1962/PL-900-Microsoft-Power-Platform-Fundamentals/master/Instructions/Labs/media/revisions/flow5.png)



## Task #2: Validate and test the flow

Your flow will begin sending emails to the email you specified if there are any visits that meet the requirements laid out in the flow.

1. Validate that you have visit records that:

   1. Have active status
   
   2. Scheduled End is in the past (by more than 15 minutes)
   
   3. Actual Start has a value.
   
   > **Note**: To view this data, navigate to make.powerapps.com in a new tab. Click Solutions on the left pane to locate your solution. Select the Visit table, then select the Data tab. Click Active Visits in the top right-hand corner to display the view selector, then select Custom columns.
   
2. Navigate to your **Security Sweep** flow, if not already there.

3. When your flow opens, click **Test**.

4. Select **Manually**.

5. Click **Save & Test** and **Run Flow**.

6. When flow competes, click **Done**. 

7. Expand **Apply to each**, then expand the **Send an email notification** step. Check the **Subject**, **Email Body** values.

8. Select the back arrow to the Security Sweep flow details. Select **Turn off** on the command bar. This is to prevent flow from executing every 15 minutes on the test system.


## Example:

* This is the Active Visits view (therefore all visits shown are active)
* Scott Konersmann's visit has a Scheduled End time more than 15 minutes in the past
* The visit has an Actual Start time

![Security sweep scheduled flow part 2b](https://raw.githubusercontent.com/philh1962/PL-900-Microsoft-Power-Platform-Fundamentals/master/Instructions/Labs/media/revisions/flow10.png)

As all conditions are met, this will trigger emails every 15 minutes (in this case for the top four visits in the view):

![Security sweep scheduled flow part 2a](https://raw.githubusercontent.com/philh1962/PL-900-Microsoft-Power-Platform-Fundamentals/master/Instructions/Labs/media/revisions/flow11.png)

# Challenges

* How could you add Actual Start and Scheduled End to the email body?
* How could you ensure user-friendly date formatting is used in the email body?



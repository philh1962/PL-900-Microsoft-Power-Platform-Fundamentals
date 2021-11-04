---
lab:
    title: 'Lab 4: How to build a model-driven app'
    module: 'Module 3: Get started with Power Apps'
---

# Module 3: Get started with Power Apps
## Lab 3: How to build a model-driven app

# Scenario

Bellows College is an educational organization with multiple buildings on campus. Campus visitors are currently recorded in paper journals. The information is not captured consistently, and there are no means to collect and analyze data about the visits across the entire campus. 

Campus administration would like to modernize their visitor registration system where access to the buildings is controlled by security personnel and all visits are required to be pre-registered and recorded by their hosts.

Throughout this course, you will build applications and perform automation to enable the Bellows College administration and security personnel to manage and control access to the buildings on campus. 

In this lab, you will build a Power Apps model-driven app to allow the backoffice campus staff to manage visit records across the entire campus. Unlike canvas apps, model-driven apps closely resemble existing Dynamics 365 apps and allow for fast deployment and minimal training.

# High-level lab steps

As part of creating the model-driven app, you will complete the following:

-   Create a new model-driven app named Campus Management

-   Edit the app navigation to reference the required tables

-   Customize the forms and views of the required tables for the app

We will work with the following components:

- **Views**: Views allow the user to display the existing data in the form table.

- **Forms**: This is where the user creates/updates new rows in the tables.

Both will be integrated to the model-driven app for a better user-experience.

## Prerequisites

* Completion of **Module 0 Lab 0 - Validate lab environment**
* Completion of **Module 2 Lab 1 - Introduction to Microsoft Dataverse**




# Exercise \#1: Customize Views and Forms

**Objective:** In this exercise, you will customize views and forms of the custom created tables that will be used in the model-driven app.

## Task \#1: Edit Visit Form

1.  Sign in to <https://make.powerapps.com> if you are not already signed in.

2.  Select your Sales Trial environment.

3.  Select **Solutions**.

4.  Click to open your **Campus Management** solution.

5.  Click on the **Visit** entity to open it.

6.  Select the **Forms** tab and click to open the **Main** form type. 

    > By default, the form has two fields: Name (Primary Field) and Owner.
    
7.  Select **+ Form field** and add the following fields below the **Owner** field by dragging columns to the form or simply clicking column names:

    * **Building**
    * **Visitor**
    * **Scheduled Start**
    * **Scheduled End**
    * **Actual Start**
    * **Actual End** 
    
8.  Drag the **Code** column and drop it in the form header. 

    > The header is the top right area of the form. You may need to minimize the Properties panel on the right side of the screen to see the field on the form.

9.  With the **Code** field still selected, check the checkbox for **Read-only** in the Properties panel.

10.  Select **Owner** field. In the Properties panel, change the field's **label** from **Owner** to **Host**

11.  Click **Save** at the top right and wait for the save to complete.

12.  Click **Publish** at the top right and wait for the publishing to complete.

13.  Click **Back** at the top left of the screen. You should now be back to the
     Visit table Forms Tab.

## Task \#2: Edit Visit Views

In this task, we will modify the default Active Visits view and create a new view for today's visits.

1.  Select the **Views** tab and click to open the **Active Visits** view.

2.  Add the following fields to the view by either clicking or dragging and dropping the fields:

    *  **Code**
    *  **Visitor**
    *  **Building**
    *  **Scheduled Start** 
    *  **Scheduled End**
    
3.  Click the **Created On** column and select **Remove**. Field **Created On** will now be removed from the view.

4.  Click the **Name** column and select **Remove**. Column **Name** will now be removed from the view.

5.  In the Properties panel on the right, click **Sort by ...** and select **Scheduled Start**. Click on **Scheduled Start** again to change the order to descending.

6.  Resize the individual column widths to fit the data.

7.  Click **Save** and wait until the changes are saved.

8.  Click **Publish** and wait for the publishing to complete.

Now, we will clone the view to create a new view for today's visits.

9.  Press **Edit filters** link in the Properties panel.

10.  Click **Add**, select **Add row**.

11.  Select **Scheduled Start** as a column, then select **Today** as the condition in the drop-down. (This also removes the specific time condition in the filter).

12.  Click the **...** on the **Status** row and click **Delete**. 

13.  Press **Ok** to save the condition. The view is now filtered to show only records where the Scheduled Start date is today.

14.  Add **Actual Start** and **Actual End** columns to the view. (Since we no longer filter on the view status, we will see all today's visits including completed ones. These fields will help to differentiate completed visits and visits in progress).

15.  Click on the **dropdown arrow** by the Save button (be careful not to press the button itself) and select **Save As**.

16.  Change the name to **Today's Visits** and press **Save**.

17.  Click **Publish** and wait for the publishing to complete.  Close the tab.

# Exercise \#2: Create Model-Driven Application

**Objective:** In this exercise, you will create the model-driven app, customize the sitemap, and test the app.

> You will see several fields not addressed as you build out your application, particularly on the sitemap steps. We have taken some short cuts in the interest of doing the labs. In a real implementation, you would give these items logical names.

## Task \#1: Create Application

**NOTE - At time of writing (27/10/21) there are two app designer interfaces in use - the "Classic" app designer and the "Modern" app designer in preview.  They both do the same function. As the Classic is liable to be deprecated and the Modern liable to change, we have included instructions for both.  You may choose to use either - Task 1a for Classic or 1b for Modern.

## Task 1a:  Create Application in Classic app designer:

1.  -   Sign in to <https://make.powerapps.com>

    -   While in Sales Trial environment, click to open your **Campus Management**
        solution to add the Model-Driven App directly in the solution.
    
2.  Choose to create the Model-Driven Application in Classic app designer.

    -   Click **New** and select **App** and then **Model-driven app**. This will open a new tab.
    
    -   Enter **[Your Last Name] Campus Management** for Name.  

    -   Select **Use existing solution to create the App** checkbox

    -   Select **Next**

    -   Select your **Campus Management** solution from the list.
    
    -   Click **Done**
    
3.  Click the pencil icon next to **Site Map.**

4.  Edit the default titles

    -   Select **New Area**.

    -   Change the Title of the New Area to **Campus** in the properties pane on the right.

    -   Select **New Group**.

    -   Change the Title of the New Group to **Security** in the properties pane on the right.
    
5.  Add the Contact table to the sitemap

    -   Select **New Subarea**.

    -   In the **Properties** pane, select **Entity** from the dropdown
        for **Type**.

    -   Search for **Contact** table from the dropdown for **Entity**.
    
6.  Add the Visit table to the sitemap

    -   Select **Security** group and click **Add**.

    -   Select **Subarea**.

    -   Go to the **Properties** pane.

    -   Select **Entity** from the dropdown for **Type** and search for
        **Visit** table from the dropdown for **Entity**.
    
7.  Add the Building table to the sitemap

    -   Select **Campus** area and click **Add**.
    
    -   Select **Group**.
    
    -   Enter **Settings** for **Title** in the **Properties** pane.
    
    -   With the **Settings** Area still selected, click **Add**.
    
    -   Select **Subarea**.
    
    -   Go to the **Properties** pane.
    
    -   Select **Entity** from the dropdown for **Type** and search for **Building** table from the dropdown for **Entity**.

8.  Click **Save**. This will show the loading screen while the changes are being saved.

9.  Click **Publish** to publish the sitemap and wait for the publishing to complete.

10.  Click **Save and Close** to close the sitemap editor. 

    > You will see the assets for the entities that were added to the sitemap are now in the application.
     
11.  Click **Save** on the App Designer.

12.  Click **Validate** to validate the changes done in the application. 

    This will show some warnings but we can ignore them, since we have not referenced a specific View and Form for the entities and the users will have access to all the Views and Forms for **Visit** and **Building** entities.
     
13. Click **Publish**

14.  Click **Save and Close** to close the app designer.

15.  Click **Done**.

16.  Select **Solutions** and select **Publish all Customizations.**

17.  Select **Apps** and your new application should be listed.  **Now go to task 2.**



## Task 1b:  Create Application in Modern app designer:

1.  -   Sign in to <https://make.powerapps.com>

    -   While in Sales Trial environment, click to open your **Campus Management**
        solution to add the Model-Driven App directly in the solution.
    
2.  Choose to create the Model-Driven Application in Modern app designer (preview).  Be aware this preview interface is liable to minor changes.

    -   Click **Create** to open the designer.
    
    -   Enter **[Your Last Name] Campus Management** for Name and click **Create** .

    -   Select **Add page** 

    -   Choose **Table based view and form**

3.  Select your the tables we want to add to the app.  In this case, tick **Building,  Contact** and **Visit** from the list and select **Add**.
    
4.  You will see a preview of the model-driven app ready for customisation.  All the tables have been added to the same screen group, currently called Group1, which we will customise.  In addition, the tables have carried over all their available views - in the case of the system table contacts, there are several that need to be removed.

5.  We are going to rearrange our tables into two groups - **Security**, containing Contacts and Visits, and **Settings**, containing Buildings.  Select the **Navigation** icon in the left hand pane.

6.  In the Navigation pane, select the Group1 line.  Change the title in the right hand pane to Security.  Press tab twice to change the group name. 

7.  Under the renamed Security group, there is a new Subarea called Subarea1.  Select the elipsis on this line and **Remove Subarea1**.

8.  In the Navigation pane, select the Contacts line.  Select the elipsis on this line and move it up until it is under Security.

9.  In the Navigation pane, select the Buildings line.  Select the elipsis on this line and move it up until it is under Contacts.

10.  To add the new group, in the Navigation pane select **Add** and choose **New Group**.  Change the title in the right hand pane to **Settings**.

11.  In the Navigation pane, select the Buildings line.  Select the elipsis on this line and move it until it is under Settings.

12.  To remove the unwanted views for the Contacts table, select the **Pages** icon in the left hand pane. Expand the Contact line.

13.  Select **Contact view**, and in the pane on the right, choose **Manage views**.  Tick the box for **Active Contacts**, and **Save**.

14.  **Save** and **Publish** the app.



## Task \#2: Test Application

1.  Start the application

    -   Select **Apps** and click on your **Campus Management** app. (If you don't see your app at first, you may need to refresh your browser.)

    -   The application should open in a browser tab.
    
2.  Create new Contact

    -   The app should open to the **Active Contacts** view.  You should also see the Security group with Contacts and Visits tables, and the Settings group with the Buildings table.

    -   Click **New** from the top menu.

    -   Provide **First Name** as `John` and **Last Name** as `Doe`.

    -   Provide your personal email as **Email**. This will be used in a future lab. 
    
    -   Click **Save and Close**.

    -   You should now see the created contact on the **Active Contacts** view.
    
3.  Create new Building

    -   Select **Buildings** from the sitemap.

    -   Click **New**.

    -   Enter the **Name** as `Microsoft Building`
        
    -   Click **Save and Close**. This will show the newly created record on
        the Active Buildings View.
    
4.  Create new Visit

    -   Select **Visits** from the sitemap.
    
    -   Click **New**.
    
    -   Enter the fields as following 
    
        -   **Name**: `New test visit`
        -   **Building**: select Microsoft Building
        -   **Visitor**: select John Doe
        -   **Scheduled Start**: select tomorrow's date and 2:00 PM as start time
        -   **Scheduled End**: select tomorrow's date and 3:30 PM as end time
        
    -   Click **Save and Close**. This will create the Visit and you should be able to see it on the
        Active Visits View.
        
    -   Change view to **Today's Visits**. You should no longer see the new visit in the view, since it is scheduled for tomorrow.
    
5. You may add more test records.

   Your running app should look approximately like the following:

![Sample model driven app](media/3-model-app.png)




# Challenges

* How could you select specific views and forms for Visits and Buildings
* Security personnel typically work in a single building. How would you provide an easy way for them to display visits only for a selected building?
* How do you restrict access to specific entities, e.g. Buildings should be read-only for all staff members except the administrators?


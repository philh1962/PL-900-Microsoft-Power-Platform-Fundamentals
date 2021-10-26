---
lab:
    title: 'Lab 2: How to build a canvas app, Part 1'
    module: 'Module 3: Get started with Power Apps'
---

# Module 3: Get started with Power Apps

## Lab: How to build a canvas app, Part 1



# Scenario

We will continue our implementation of the Bellows College visitor recording system. 

In part 1 this lab, you will design a Power Apps canvas app that college staff can use to manage visits for their guests.

# High-level lab steps

We will follow the below outline to design the canvas app:

-   Create the app from data using the phone form factor template
-   Configure a detail page with visit info
-   Configure an edit page to create visits
-   Configure a gallery control to show the visits
-   Add filtering on the gallery data source to show only future visits

## Prerequisites

* Completion of **Module 0 Lab 0 - Validate lab environment**
* Completion of **Module 2 Lab 1 - Introduction to Microsoft Dataverse**


# Exercise \#1: Create Staff Canvas App

**Objective:** In this exercise, you will create a canvas app from a template and then modify it to include required data.

## Task \#1: Create Canvas App

In this task, you will create a canvas app using the phone layout template based on Microsoft Dataverse. Using Visits as a selected table from Dataverse, the template will generate a Gallery - View - Edit app to manage campus visits.

1.  Start creating an app from data

    -   Sign in to <https://make.powerapps.com>

    -   Select your **Sales Trial** environment at the top right if it is not already set.

    -   Select **+ Create** in the left hand menu.  Note that apps and portals can be started from blank, from data, or from templates.  

    -   Select the **Dataverse** icon within **Start from data** on the Home screen.

2.  Connect to your Visits table
    
    -   Select **+ New connection**

    -   Select **Microsoft Dataverse** and click **Create**

    -   Locate and select your **Visits** table

    -   Select **Connect**.  This will open the Power Apps Studio editor. 

3.  The **Welcome to Power Apps Studio** window may appear. Click **Skip**.  You are now editing a new (as yet unnamed) app built on the data we imported in the last lab.  You can preview the app in this unimproved state by clicking the play button near the top left corner of the screen (small play triangle).

**About the Power Apps Studio** The app editor is not intuitive, especially for beginners.  You can change a selected property in two ways - firstly from the dropdown selector on the left of the function line at the top of the screen. This lists the properties alphabetically. Alternatively, you can use the shortcuts in the Properties tab or Advanced tab with searchbox.  The first allows you to put in values quickly and directly, the second gives you some convenient shortcuts and the ability to select colours from a palette rather than type RGBA values.  They both produce exactly the same results.  In these exercises we will show you both methods and inform you which we are using.

4.  Save application

    -   Click **File \> Save**.

    -   Press **Save** and save to the cloud.   Your new app (called App unless you give it a different name) will now be visible in the Apps section of the Power Apps maker portal, along with the Bellows College Portal and the Portal Management app that is supplied with it.

## Task \#2: Configure Visits Detail Form

In this task, you will configure the Detail form to view information about individual visit records.  The template detail form only shows the name and date/time when the record was created.  We will add fields for scheduled and actual start and end, building and visit code, and remove the created on field. 

1. Select the **Back** arrow at the top left to go back to the app definition.

2. Expand **DetailScreen1** under **Tree view**

3.  Select **DetailForm1**

4.  Select **Edit fields** next to **Fields** in the right-hand panel.

5.  Click **Add field**

6.  Select the following fields in this order:

    * Code
    
    * Building 
    
    * Scheduled Start
    
    * Scheduled End
    
    * Actual Start
    
    * Actual End
    
7.  Click **Add**  You will see that the new fields have been added in the order in which they were selected.  This saves a lot of rearranging in the next step.

8.  Rearrange fields in the **Fields** pane by dragging and dropping field names up or down. Recommended order is:
    * Code, Name, Building, Visitor, Scheduled Start, Scheduled End, Actual Start, Actual End
    >**Tip:** You can collapse each field by clicking the down arrow beside the field name.

9.  Remove the **Created On** field by clicking the ellipses (**...**) beside the field name and selecting **Remove**. 

10.  Close the **Fields** pane.
 
11.  To preserve work in progress, click **File** then click **Save**. Use the back arrow to return to the app.  We will publish it later.

## Task \#3: Configure Visits Edit Form

In this task, you will configure a form to edit information about individual visits.  The template screen only shows the record name and creation date/time, so we will add fields to show the building, visitor and scheduled start and finish.  Scheduled start and finish columns were created as required columns, so users will be required to enter data for them on this form.   

1.  Expand **EditScreen1** under **Tree view**  (The last row) 

2.  Select **EditForm1**

3.  Select **Created On** field and press **Del** key to remove the field

4.  Select **Edit fields** in the properties panel

5.  Click **Add field**

6.  Select the following fields in the following order:

    * Building 
    
    * Visitor
    
    * Scheduled Start
    
    * Scheduled End
    
7.  Click **Add**

8.  You can rearrange fields in the **Fields** pane by dragging and dropping field names up or down, but if you selected them in the order of above they will be ordered correctly.

Recommended order is:  **Name, Building, Visitor, Scheduled Start, Scheduled End**

    >**Tip:** You can collapse each field by clicking the down arrow beside the field name. 

9.  Close the **Fields** pane.

10.  To preserve work in progress, click **File** then click **Save**. Use the back arrow to return to the app.

Your screen should look approximately like the following:

![Canvas edit form](media/2-canvas-edit-form.png)

## Task \#4: Configure Visits gallery

In this task, you will configure the pre-generated gallery to display the title, start date and end date for the visit. 

1.  Expand **BrowseScreen1** under **Tree view**

2.  Select **BrowseGallery1**

3.  Select **TemplateSize** property from in Advanced Properties panel on the right *equally, you could choose TemplateSize from the properties dropdown on the function line at the top*.  

4.  Replace the expression with the following `Min(150, BrowseGallery1.Height - 60)`. (You can cut-and-paste from this screen using Ctl-C and Ctl-V).  You will see the size of each entry change, ensuring sufficient space for additional information.

5.  In the app preview, select the first Date Time field in the gallery.

6.  In the formula bar at the top, change **ThisItem.'Created On'**to `ThisItem.'Scheduled Start'`

7.  Select the field again

8.  Press **CTRL-C** then **CTRL-V** to create a copy of the field, note that all the visits in the gallery are updated.

9.  Using either mouse or keyboard, move the copied control down and align it with the other controls in the gallery, beneath the other Date Time field.

10.  In the formula bar at the top, change **ThisItem.'Scheduled Start'** to `ThisItem.'Scheduled End'`

11.  To preserve work in progress, click **File** then click **Save**. Use the back arrow to return to the app.

## Task #5: Add date filter

Because number of visits continuously grows, users need a feature to filter the visits gallery. For example, the user may want to see only the future visits. In this task, you will add the ability to show visits only after a date selected by the user.

1. Select **BrowseScreen1**

2. Select **Insert** from the menu on the top line.

3. Select **Input** from the next line down and choose select **Date picker**.

4. Using either keyboard or mouse, position the control below the search box.

5. Select **BrowseGallery1** 

6. Resize and move the gallery control so that it is located under the date picker and covers the screen. You can do this by clicking the resize icon at the top center of the gallery control and resizing the control to start after the date picker.

7. With **BrowseGallery1** selected, click the **Advanced** tab of the Properties pane.

8. Locate the **Items** property and click in the text box.

9. In the expression, locate **[@Visits]** and replace it with `Filter(Visits,'Scheduled End' >= DatePicker1.SelectedDate)`. The full expression should look like the following.  (You may find it easier to cut-and-paste the whole expression).
(This is filtering the view by visits with a scheduled end later than the date in the date picker).

   ```
   SortByColumns(
   	Search(
        Filter(
        	Visits,
            'Scheduled End' >= DatePicker1.SelectedDate
           ),
           TextSearchBox1.Text,
       	"bc_code","bc_name"
       ),
     "bc_code",
     If(SortDescending1, Descending, Ascending)
   )
   ```
   
10. To preserve work in progress, click **File** then click **Save**. Use the back arrow to return to the app.

Your screen should look approximately like the following, but with the search date being today's date:

![Canvas filtering gallery](media/2-canvas-browse.png)

# Exercise #2: Complete the App

In this exercise you will test the application and, once successful, you will add it to your solution.

## Task \#1: Test App

1.  Start the application

    -   Select the **BrowseScreen1** and press Function **F5**, or click the **Play** icon at the upper-right corner to preview the app.
    
    -   The application should load and show a list of visits. 
    
    -   Test the filter by selecting different dates in the date picker control
    
    -   Select a visit and verify that display form is working properly by selecting the **>** symbol to view item details.
    
    -   Return to the gallery and press **+** in the top right corner to create a new visit by entering an invented name, building, visitor and scheduled dates and clicking the tick icon. Verify that edit form contains required columns including visitor, building, and scheduled start and end dates.
    
    -   Fill in the information and submit. Verify that the new record appears in the gallery.  You may need to scroll down, search or sort the gallery to see new records.
    
    -   Create and verify at least 2 more visits.
    
    -   Press **ESC** key or click the **X** icon to close preview mode.

2.  Save and publish the application

    -   Click **File** and, if the Save button is displayed, click **Save**.

    -   Click **Publish**.

    -   Click **Publish this Version**.

    -   Click the **Back** arrow to navigate back to the app.

    -   Close the **Designer** tab by clicking the back arrow.

    -   After publishing, when you select your new App in the list in the Power Apps maker portal, the new version will run.  Previously, new versions could only by accessed by selecting edit and previewing. 

## Task #2: Add App to Solution and publish
We have created our app outside the our Campus Management Solution.  Adding the App to the solution and publishing all customizations will allow us to deploy the latest versions of all the necessary components. 

1. Open the Campus Management solution.

   * Sign in to <https://make.powerapps.com>  if you are not already logged in.
   
   * If the Environment displayed in the top right is not your Sales Trial environment, select your **Environment**. 
   
   * Select **Solutions**.
   
   * Click to open your **Campus Management** solution.
   
2. Select **Add existing**, then click **App**, and then click **Canvas app**.

3. Select **Outside Dataverse** tab.

4. Select your **App** app, click **Add**.

5.  The Solution will now have contain three tables (Building, Visit, Contact) and the new App.  Select the new app and click **Settings**, then click the pencil to rename the App.  Rename it **Campus Staff** and Save.  

6.  Select **back to Solutions**  and choose **Publish all customizations**.

# Extension

* You can set a begin and end date range to search by adding another date picker input, and adding to the gallery filter items

SortByColumns(Search(Filter(Visits, 'Scheduled Start' >= DatePicker1.SelectedDate,'Scheduled End' <= DatePicker2.SelectedDate), TextSearchBox1.Text, "bc_code","bc_name"), "bc_code", If(SortDescending1, Descending, Ascending))




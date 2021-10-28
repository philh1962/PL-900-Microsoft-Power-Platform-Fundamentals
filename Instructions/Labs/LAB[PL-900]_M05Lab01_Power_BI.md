---
lab:
    title: 'Lab 7: How to build a simple dashboard'
    module: 'Module 5: Get Started with Power BI'
---

# Module 5: Get Started with Power BI
## Lab: How to build a simple dashboard

# Note - Power BI refers to Columns as Fields throughout.  This is expected to change in future versions.

# Scenario

Bellows College is an educational organization with multiple buildings on campus. Campus visitors are currently recorded in paper journals. The information is not captured consistently, and there is no way to collect and analyze data about the visits across the entire campus. 

Campus administration would like to modernize their visitor registration system where access to the buildings is controlled by security personnel and all visits are required to be pre-registered and recorded by their hosts.  Throughout this course, you have built applications and perform automation to enable the Bellows College administration and security personnel to manage and control access to the buildings on campus. 

In this lab, you will build a Power BI dashboard that visualizes data about campus visits.

# High-level lab steps

We will follow the below steps to design and create the Power BI dashboard:

-   Connect to Dataverse
-   Transform the data to include user-friendly descriptions for the related rows (lookups)
-   Create and publish a report with various visualizations of the campus visits information
-   Utilize a user natural language query to build additional visualizations
-   Build a mobile view of the Power BI dashboard


## Prerequisites

* Completion of **Module 0 Lab 0 - Validate lab environment**
* Completion of **Module 2 Lab 1 - Introduction to Microsoft Dataverse**

## Things to consider before you begin

-   Who is the target audience of the report?
-   How will the audience consume the report? Typical device? Location?
-   Do you have sufficient data to visualize?
-   What are the possible characteristics you can use to analyze data about the visits?

# Exercise \#1: Create Power BI Report

**Objective:** In this exercise, you will create a Power BI report based on data from your Dataverse database.

## Task \#1: Install Power BI Desktop / Prepare Power BI service and connect to your data

1. Follow the below instructions to setup Power BI: 

    - If Power BI Desktop is **already** installed, please skip to [Task \#2](#task-2-prepare-data).
    
    - If you do not have Power BI Desktop installed, complete **Step #2**.
    
    - If you do not have required permissions or encounter issues with running Power BI Desktop, continue to **Step #4**.

2. Navigate to [https://aka.ms/pbidesktopstore](https://aka.ms/pbidesktopstore) to download and install Power BI Desktop.

    > [!IMPORTANT]
    > If you experience issues installing Power BI Desktop using Microsoft Store, try standalone installer that can be downloaded from [https://aka.ms/pbiSingleInstaller](https://aka.ms/pbiSingleInstaller).

3. If you successfully installed Power BI Desktop, you can now skip to [Task \#2](#task-2-prepare-data); otherwise, continue to the next step.

    > If you do not have required permissions to install desktop applications or experience difficulties in running or configuring Power BI Desktop, complete the task steps below to run using local data and the web app.

4. Download [visits.pbix](../../Allfiles/visits.pbix) and save on your computer.

5. Navigate to [https://app.powerbi.com/](https://app.powerbi.com/) and click **Sign in**. 

6. Click **My Workspace**. 

7. If presented with the **Get Data** page, click **Skip**. 

8. Expand **+New** and select **Upload a file**.

    > [!IMPORTANT]
    > If you don't see **+New**, you may need to activate the new look for Power BI. Be sure to toggle the **New look** to **On** at the top of your screen.

9. Select **Dataflow**.

10. Click **add new Tables**.

11. Select **Power Platform** and **Dataflows**.

12. Select  **Common Data Service (Legacy)**. Cut and paste the Server Url of your environment as in Task 2 Step 1 below.

13. Continue from Task 2 Step 6 below.

## Task \#2: Prepare Data

1.  Open Power BI Desktop, sign in with your provided credentials if prompted.

3. Select **Get data from another source**, or select **Get data > more** .

4. Select **Power Platform** on the left, then select **Dataverse**, and press **Connect**.  This will connect you to your data using your tenant credentials.

5. Expand **Sales Trial** node, search for bc and select **bc_Building** and **bc_Visit** entities, click **Load**.

6.  You are given the option of connecting to the data via **Import** or **DirectQuery**.  For the sake of this lab, we will use **Import** as the data access is faster.  The advantages/disadvantages of the two methodologies can be found at https://social.technet.microsoft.com/wiki/contents/articles/53078.power-bi-import-mode-vs-directquery-mode.aspx 

7. Once the data is loaded, there are three icons on the left margin of the screen - hover over to identify - these are **Report** (used to produce visuals), **Data** (used to view and change source imported data), and **Model** (used to set relationships between different tables).
Please also note the **Transform Data** tab at the top of the screen - this useful feature enables large scale data transformations on import and can save much time, although it is outside the scope of this lab.  

8.  Click the **Data** icon on the left vertical toolbar. You can click on a field to see it shown as a column in the dataset. (DirectQuery connections do not have this option).

7. Click **Model** icon on the left vertical toolbar.

8. Power BI has autodetected the relationships between the two tables. A line will appear illustrating the relationship between the two tables.  If you hover over the line it will show the connected columns, as below:

![Power BI relationship diagram](https://raw.githubusercontent.com/philh1962/PL-900-Microsoft-Power-Platform-Fundamentals/master/Instructions/Labs/media/revisions/PBI%202.png)

**This has created a relationship between the two tables that Power BI will be able to use to display related data, in this case connecting visit data to the respective building data.**  The line shows a one to many relationship - one building can have many visits.

Should you need to edit autodetected relationships, you can select **Manage relationships** in the toolbar.  With more complex datasets this may be necessary, but this is outside the scope of this lab.

9.  Select **Report** icon on the left toolbar.

10. Expand the **bc_Building** node in the **Fields** panel.

11. Click **...** beside **bc_name** and select **Rename**.  Rename the Column **Building**. (Power BI will use these names in axes and titles in visuals, so it is good practice to change them to more understandable names).

12. Scroll down and expand the **bc_visit** node.

12. Click **...** next to the **bc_visitid** field and select **Rename**. Enter **Visit** as the field name.

15. Click **...** next to the **bc_scheduledstart** field and select **Rename**. Enter **Start** as the field name.  (You may need to hover over it to identify the field).

16. Save work in progress by pressing **File \| Save** and entering a filename of your choice.

## Task #3: Create Chart and Time Visualizations

1. Press the pie chart icon in the **Visualizations** panel to insert a chart.

2. Drag the **Building** field and drop it into **Legend** box.

3. Drag the **Visit** field and drop it into **Values** target box.

4. Resize the pie chart using corner handles so that all chart components are visible.  The pie chart shows the visits by building.  With the pie chart selected, take the opportunity to try some other visualisations of varying usefulness - Funnel, Donut, Stacked Column, Stacked Bar, Treemap.  Set it back to Pie Chart before continuing.

5. Click on the report outside of the pie chart to deselect it and select **Stacked column chart** in **Visualizations** pane. 

6. Drag **Visit** field and drop it into **Values** target box.

7. Drag **Start** field and drop it into **Axis** target box.

8. Resize the chart as desired using the corner handles.

9. Test the report interactivity:

    * Select various building slices on the pie chart and observe changes on the time report.
    
    * Click on the column chart. Press the down arrow to turn on **Drill down** mode, then press the column to drill down to the next level (months). Another way to do this is to click **Data/Drill \| Expand next level** on the ribbon.
    
    * Drill up and down and select various bars on the time column chart to observe changes on the pie report.

In the example below we have drilled down on the Stacked Bar chart to days in September 2021, and chosen Contoso Suites as the Building:

![Power BI charts example](https://raw.githubusercontent.com/philh1962/PL-900-Microsoft-Power-Platform-Fundamentals/master/Instructions/Labs/media/revisions/pbi%203.png)
    
10. Save the work in progress by pressing **File \| Save**.

# Exercise #2: Create Power BI Dashboard

## Task #1: Publish Power BI Report

1. Press **Publish** button on the Home tab of the ribbon.

2. Select **My workspace** as the destination, then press **Select**.

3. Wait until publishing is complete and click **Open \<name of your report\>.pbix in Power BI**.  You may need to log in to see it.

## Task #2: Create Power BI Dashboard

1. You should have the report open from the previous task.

2. Select **Pin to a dashboard** on the menu. You may need to press **...** to show additional menu items.

3. Select **New dashboard** on **Pin to dashboard** prompt.

4. Enter **[Your Last Name] Campus Management** as a **Dashboard name**, press **Pin live**.

5. Select **My workspace** at the top, select **[Your Last Name] Campus Management** dashboard.

6. Test interactivity of the pie and bar charts displayed - you will see the interactivity has been retained in the published report.

## Task #3: Add Visualizations Using Natural Language

1. Within your **Campus Management** dashboard, select **Ask a question about your data** bar at the top.

2. Enter **buildings by number of visits** in Q&A area. The data will be displayed as a bar chart.

3. Select **Pin visual**.

4. Select **Existing dashboard**, select your **[Your Last Name] Campus Management** dashboard, press **Pin**.

5. Click **Exit Q&A**.

Your **[Your Last Name] Campus Management** dashboard should be displayed. You may have to scroll down to see the new Q&A visual. 

Your dashboard should look similar to the following:

![Power BI Dashboard](media/5-powerbi-result.png)

## Task #4: Build Mobile Phone View and Share a Report with a QR Code

1. In the Dashboard, select **Edit \| Mobile Layout**.

2. Rearrange tiles as desired.

3. Click **Mobile layout** at the top right and change the View to **Web layout**.

4. Select **My Workspace** at the top, and select your **Report**.

5. Select **Edit** and then select **... \| Generate QR Code**.

6. *Optional:* If you have a mobile device, scan the code using a QR scanner app available on both iOS and Android platforms, or the camera app if your phone supports it. Log in to your account if prompted. Navigate and explore the report on a mobile device.



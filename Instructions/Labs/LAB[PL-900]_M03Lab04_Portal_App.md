
---
# Module 3: Get started with Power Apps

## Lab 4: How to build a Power Apps portal

# Scenario

Bellows College is an educational organization with multiple buildings on campus. Campus visits are currently recorded in paper journals. The information is not captured consistently, and there are no means to collect and analyze data about the visits across the entire campus.

Campus administration would like to provide the visitors with the information about the buildings on campus. The visitors will be able to view the buildings list on a website, which will be built using a Power Apps portal.  Portals are usually used for external users.

In this lab, you will provision a Power Apps portal and create a portals webpage that will show a listing of the buildings on campus.

# High-level lab steps

You will follow the below outline to design the Power Apps portal:

* Provision a Power Apps portal in the Dataverse environment
* Create and configure a webpage to show a list of the buildings
* Create a new theme and apply it to the portal

## Prerequisites

* Completion of **Module 0 Lab 0 - Validate lab environment**
* Completion of **Module 2 Lab 1 - Introduction to Microsoft Dataverse**

## Things to consider before you begin

* Power Apps portals apps are always started from a template instead of a blank application. Your portal should have been created in Module 0 Lab 0. Once you provision a portal, it will already have pages, menus and a default theme. 

# Exercise \#1: Create a Portal Webpage

**Objective:** In this exercise, you will create a new webpage that will display some static content as well as a list of buildings from Dataverse.  We will use the Portals editor, which is similar to other website editors such as WordPress.

## Task \#1: Navigate to Portal

1.  Navigate to <https://make.powerapps.com>.

2.  Verify that you are in your Sales Trial Environment. If you are not, change the environment at the top right.

3.  Click on **Apps**

4.  Locate your **Bellows College Visitors** app that has the **Type** of **Portal**

5.  Click on the app name to open the portal

    > You should be redirected to your portal website landing page with a welcome message. Navigate your portal to see what was created by default when you provisioned your portal. You will have two Services pages, an About us page and a search function.  

## Task \#2: Create a Webpage

1.  Open Power Apps portals Studio

    -   Sign in to <https://make.powerapps.com> (you may still have this open in your tabs)

    -   Select **Apps**
    
    -   Locate the app that has the **Type** of **Portal**

    -   Click on the ellipses (**...**) to the right of the portals app name and choose **Edit**

    > You are now in the Power Apps portals Studio. This is where you can modify and create portal content.

2.  Create a new page

    -   From the command bar on the left, select **New page**

    -   Mouse over **Fixed layouts** and choose **Page**

3.  In the properties pane, under **Display** change the **Name** from **New page (1)** to `Building Directory` (it may take a moment to appear)

4.  In the **Partial URL** change the value to `building-directory`, press the Tab key (to initiate auto-save)

    > The title of the page should now read **Building Directory**
    
## Task \#3: Add Static Content
In this exercise we are adding some static text and an image to the new page.

1.  Add a section to the webpage

    -   On the canvas (area showing webpage), select the **Page Copy** section. This is the large box around the 2 sentences of text in the middle of your page.

    -   On the toolbelt (left side), select the **Components** icon

    -   Choose **Two columns section** from the **Section layout** area

2.  Add Static Text

    -   On the canvas (area showing webpage), select the left column

    -   On the toolbelt (left side), select the **Components** icon

    -   Choose **Text** from the **Portal components** area

    -   In the new text area, enter the following text:
          ```
          This is our building directory:
          ```
    -   Select the text box above the one you just edited, and click **Delete** on the command bar to remove the default text.

3. Add an Image

    -   On the canvas (area showing webpage), select the right column

    -   On the toolbelt (left side), select the **Components** icon

    -   Choose **Image** from the **Portal components** area

    -   In the properties pane, click **Select an image**. Locate and choose any **searchhero.png**
    
    -   In the properties pane, click the **Formatting** section drop-down and change the **Width** to 70% (be sure to type the %). You can play around with the sizing of the image until it is as desired.

4.  Click **Browse website** to view the page so far.  

    > You may need to configure your browser to allow pop-ups.

## Task \#4: Add a List Component
In this exercise we are adding a dynamic list of content from the Dataverse table, using the Portals security tools.

1.  Navigate to the previous tab and continue to step #2. If not available, follow the below steps to return to this location.

    -   Sign in to <https://make.powerapps.com> (you may still have this open in your tabs)

    -   Locate the app that has the **Type** of **Portal**

    -   Click on the ellipses (**...**) and choose **Edit**
    
    -   On the toolbelt (left hand side), choose the **Pages** option 

    -   Locate and select the **Building Directory** page you created earlier
    
2.  Add a list component to the Building Directory page

    -   Select the section with two columns.

    -   On the toolbelt (left side), select the **Components** icon

    -   Choose **One column section** from the **Section layout** area (a section will appear below the image and text on the webpage)

    -   Select the new column section on the canvas

    -   On the toolbelt (left side), select the **Components** icon

    -   Choose **List** from the **Portal Components** area (a list component will appear in the new section)
    
3.  Configure the list component

    -   Select the list component on the canvas

    -   In the properties pane (right side), enter in `Buildings List` in the **Name** field

    -   In the **Table** field, choose **Building (bc_building)** from the drop-down list

    -   In the **Views**, choose **Active Buildings**

    -   Leave the remaining default settings
    
4.  Click **Browse website** to view the page. 

    > You will see an error message that you do not have the permissions to view these records.  Since portals are designed to allow external users to access Dataverse data, we need to set permissions for access.  Return to the portal editor, select the list component and go to **Manage table permissions**.  Choose **New permisson**,  give the permission a name (e.g. Building List),  select the **Building (bc_building)** table and choose **Global Access** as the Access type.  Set the Privileges to Read, and after clicking **+ Add roles**, select **Anonymous Users**. Click **Browse website** to view the page again, and the building list will now be visible in your new page.  This will give you an idea of the granularity of the security setup in portals.

5.  Note that because the Active Buildings view contains the Created On column, these dates are visible on the portal page.

# Exercise \#2: Change the Portal Theme

In this exercise, you will create a new theme that will alter the color scheme of your portal. 

## Task #1: Apply and Edit a Theme

1.  Navigate to the previous tab and continue to step #2. If not available, follow the below steps to return to this location.

    -   Sign in to <https://make.powerapps.com> (you may still have this open in your tabs)

    -   Locate the app that has the **Type** of **Portal**

    -   Click on the ellipses (**...**) and choose **Edit**
    
2.  Apply and customize a basic theme

    -   On the toolbelt (left side), select the **Themes** icon
    
    -   Click the toggle for **Enable basic theme** to turn this feature on.
    
    -   On one of presets, click the ellipses (**...**) and choose **Customize**  The Dark yellow Preset is particularly lurid.
    
    -   A copy of the basic theme has been created. 
    
    -   On the properties pane, play around with changing the colors and exploring the impact of these changes to your portal.
    
    -   Rename your theme
    
3.  On the command bar, click **Sync configuration** and then **Browse website** to appreciate the new colour scheme.  Note that the theme is applied to all the pages of the site.

Your app layout should look similar to the following structure:

![Example portal](media/9-portallabresult.jpg)

# Challenge
Explore the **Portal Management** app.

Up to now we have only made minor changes to a template portal, but there are many more capabilities and settings in the Portal Management app that is automatically deployed into your environment when you provision a portal.  You can access this by click **Settings > View more settings** in the your Portal editor, or by selecting it listed under Apps in the make.powerapps.com screen.

---
title: Add a new Permission in the UI
labels:
    - howto
    - permission
    - content-review-6-0
confluence:
    ajs-parent-page-id: '12911810'
    ajs-parent-page-title: Roles & Permissions Section
    ajs-space-key: Studio
    ajs-space-name: Nuxeo Online Services
    canonical: Add+a+new+Permission+in+the+UI
    canonical_source: 'https://doc.nuxeo.com/display/Studio/Add+a+new+Permission+in+the+UI'
    page_id: '7536711'
    shortlink: RwBz
    shortlink_source: 'https://doc.nuxeo.com/x/RwBz'
    source_link: /display/Studio/Add+a+new+Permission+in+the+UI
history:
    - 
        author: Solen Guitter
        date: '2016-09-01 15:28'
        message: ''
        version: '10'
    - 
        author: Manon Lumeau
        date: '2015-11-25 17:36'
        message: replace "access rights" by "permissions"
        version: '9'
    - 
        author: Bertrand Chauvin
        date: '2015-05-13 13:58'
        message: Replaced mention of DM
        version: '8'
    - 
        author: Solen Guitter
        date: '2014-03-11 18:34'
        message: ''
        version: '7'
    - 
        author: Solen Guitter
        date: '2013-08-30 10:19'
        message: Fixed broken picture
        version: '6'
    - 
        author: Solen Guitter
        date: '2011-09-06 15:36'
        message: Migrated to Confluence 4.0
        version: '5'
    - 
        author: Solen Guitter
        date: '2011-09-06 15:36'
        message: Added related tutorials
        version: '4'
    - 
        author: Solen Guitter
        date: '2011-09-06 14:30'
        message: ''
        version: '3'
    - 
        author: Arthur Gallouin
        date: '2011-06-01 16:19'
        message: ''
        version: '2'
    - 
        author: Arthur Gallouin
        date: '2011-06-01 16:08'
        message: ''
        version: '1'

---
This howto gives you the steps to add a new permission in the permissions list of Nuxeo applications. For instance, in the Permissions tab in Nuxeo Platform.
You can then leverage this permission in the [definition of new user actions]({{page space='nxdoc' page='how-to-add-a-button-in-the-web-ui'}}) to filter who should see the new button, link or icon or in [automation chains]({{page space='nxdoc' page='how-to-create-an-automation-chain'}}).

To create a new permission in Nuxeo:

1.  Unfold the **Roles and Permissions** menu entry and click on **Permissions**.
2.  Click on the **New** button.
3.  On the window that pops up give your new permission an ID and click on the **Next** button.
4.  Select where the permission should be displayed in the drop down menu and click on **Add**.
    ![]({{file name='screenshot_2011-06-01_16.02.36.png'}} ?w=650,border=true)
5.  When you have chosen all the places where the permission should be displayed, click **Save** to save your modifications.

{{#> callout type='tip' }}

Don't forget to translate the permission label [using an I18N translation file]({{page space='nxdoc' page='how-to-upload-labels-translations-in-nuxeo-studio-i18n'}}).

{{/callout}} {{#> callout type='info' }}

After you updated your Nuxeo application with Studio customizations, you must restart your server so the new permission is displayed.

{{/callout}}
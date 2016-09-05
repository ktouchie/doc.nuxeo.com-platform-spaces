---
title: Documents
labels:
    - document-type
    - content-review-6-0
toc: true
confluence:
    ajs-parent-page-id: '12911801'
    ajs-parent-page-title: Content Model
    ajs-space-key: Studio
    ajs-space-name: Nuxeo Online Services
    canonical: Documents
    canonical_source: 'https://doc.nuxeo.com/display/Studio/Documents'
    page_id: '12911979'
    shortlink: awXF
    shortlink_source: 'https://doc.nuxeo.com/x/awXF'
    source_link: /display/Studio/Documents
history:
    - 
        author: Manon Lumeau
        date: '2016-04-28 13:44'
        message: 'ix Studio menu label     '
        version: '31'
    - 
        author: Solen Guitter
        date: '2016-02-09 16:13'
        message: Add screenshot for schema and layouts tabs
        version: '30'
    - 
        author: Solen Guitter
        date: '2016-02-09 10:53'
        message: 'NXDOC-769: update Schema tab description'
        version: '29'
    - 
        author: Solen Guitter
        date: '2015-09-07 09:17'
        message: Fix format and update related how-to's.
        version: '28'
    - 
        author: Solen Guitter
        date: '2015-01-26 16:09'
        message: ''
        version: '27'
    - 
        author: Solen Guitter
        date: '2015-01-26 16:05'
        message: ''
        version: '26'
    - 
        author: Solen Guitter
        date: '2015-01-26 15:30'
        message: ''
        version: '25'
    - 
        author: Solen Guitter
        date: '2014-11-05 23:01'
        message: ''
        version: '24'
    - 
        author: Solen Guitter
        date: '2014-09-17 14:49'
        message: ''
        version: '23'
    - 
        author: Solen Guitter
        date: '2014-09-12 16:37'
        message: ''
        version: '22'
    - 
        author: Manon Lumeau
        date: '2014-08-14 11:05'
        message: ''
        version: '21'
    - 
        author: Manon Lumeau
        date: '2014-07-10 16:20'
        message: ''
        version: '20'
    - 
        author: Manon Lumeau
        date: '2014-07-02 15:29'
        message: ''
        version: '19'
    - 
        author: Manon Lumeau
        date: '2014-07-02 11:59'
        message: ''
        version: '18'
    - 
        author: Manon Lumeau
        date: '2014-07-02 11:55'
        message: ''
        version: '17'
    - 
        author: Manon Lumeau
        date: '2014-07-01 12:39'
        message: ''
        version: '16'
    - 
        author: Manon Lumeau
        date: '2014-07-01 10:35'
        message: ''
        version: '15'
    - 
        author: Manon Lumeau
        date: '2014-06-30 18:00'
        message: ''
        version: '14'
    - 
        author: Benjamin Jalon
        date: '2013-07-05 01:40'
        message: ''
        version: '13'
    - 
        author: Solen Guitter
        date: '2013-07-04 12:05'
        message: 'Added links, fixed typos and resized screenshots'
        version: '12'
    - 
        author: Alain Escaffre
        date: '2013-01-03 11:06'
        message: ''
        version: '11'
    - 
        author: Alain Escaffre
        date: '2013-01-03 05:13'
        message: ''
        version: '10'
    - 
        author: Alain Escaffre
        date: '2013-01-03 05:09'
        message: ''
        version: '9'
    - 
        author: Alain Escaffre
        date: '2013-01-03 01:01'
        message: ''
        version: '8'
    - 
        author: Alain Escaffre
        date: '2013-01-03 00:59'
        message: ''
        version: '7'
    - 
        author: Alain Escaffre
        date: '2013-01-02 01:18'
        message: ''
        version: '6'
    - 
        author: Alain Escaffre
        date: '2013-01-02 01:12'
        message: ''
        version: '5'
    - 
        author: Alain Escaffre
        date: '2013-01-02 01:09'
        message: ''
        version: '4'
    - 
        author: Alain Escaffre
        date: '2013-01-02 00:52'
        message: ''
        version: '3'
    - 
        author: Alain Escaffre
        date: '2013-01-02 00:18'
        message: ''
        version: '2'
    - 
        author: Benjamin Jalon
        date: '2012-12-04 08:41'
        message: ''
        version: '1'

---
## Concept

Read more about documents, properties and schemas in the [Essential Nuxeo Platform Terminology]({{page space='nxdoc' page='essential-nuxeo-platform-terminology'}}).

## Creating a Document Type

To create a document type, click on button "**New**".&nbsp;

&nbsp;&nbsp;![]({{file name='doc_type_creation.png' space='nxdoc' page='how-to-define-a-document-type'}} ?w=350,h=269,border=true)

*   **Feature ID**: The id of the document type. Will be used as the technical id at generation. Convention is to use a capital for the first letter.
*   **Extend**: The document type that the type being created will extend. Local types are the ones created in your Studio project. Default types are the ones part of the Nuxeo distribution you use (Nuxeo DM 5.6, ...)

{{#> callout type='info' heading='Adding a custom type'}}

if you don't find the default type you are looking for, you can add it [using the custom type registry]({{page page='registries'}}).

{{/callout}}

*   **Label**: You can put here&nbsp; a label or an i18n key.
*   **Description:**&nbsp;The description of the document type. This description is here for information purposes.

## Definition Tab

![]({{file name='doc_definition_tab.png' space='nxdoc' page='how-to-define-a-document-type'}} ?w=650,border=true)

*   **Extends**: See the&nbsp;[undefined](#creating-a-document-type)&nbsp;section of this page.
*   **Label:&nbsp;**See the&nbsp;[undefined](#creating-a-document-type)&nbsp;section of this page.
*   **Category**: The category defines in which column the document type appears on the "new Document" pop up in Nuxeo DM. If you don't want to use the default categories, you can add a new one&nbsp;[using the custom document category registry]({{page page='registries'}}).
    ![]({{file name='available-documents-workspace.png' space='userdoc' page='creating-content'}} ?w=500,h=216,border=true)
*   **Icon**: The icon that will be displayed in the default list view. Note that you can upload new icons on the&nbsp;[resources]({{page page='resources'}})&nbsp;section.
*   **Large Icon**: The icon that will be displayed in the "Available document types" pop-up and the&nbsp;[Icon view]({{page space='userdoc58' page='changing-workspace-content-presentation'}}) (view available up to Nuxeo Platform 5.8). Note that you can upload new icons on the&nbsp;[resources]({{page page='resources'}})&nbsp;section.
*   **Default view**: The default JSF view. This is a technical attribute that you probably don't want to change (will be moved in an advanced section in the future).
*   **Lifecycle**: the life cycle the document will follow. You can use a life cycle that&nbsp;[you defined]({{page page='life-cycle'}})&nbsp;in Studio.
*   **Container types:&nbsp;**The document types selected here are the ones from which it will be possible to create the document type being designed.
*   **Accepted children types**: The document types selected here will be creatable just under the document type being designed. This attribute only appears for document types that have the "folderish" facet.
*   **Document**&nbsp;**Facets**: Read the page [Available Facets]({{page space='nxdoc' page='available-facets'}})&nbsp;for better understanding of what facets are and which ones are available. If you don't find the facet you are looking for, you can add it&nbsp;[using the custom facet registry]({{page page='registries'}}).
*   **Deployment mode**: This is particularly useful when you declare a document type that already exists in the default product from Studio, for instance "Folder", or "File". When the contribution generated by Studio is deployed on Nuxeo DM (for instance when you click on "Update" from Admin Center), either you want to delete the previous definition, and use only what was defined from Studio (_override_), or you just want to "complete" the definition from what you configured in Studio (_merge_). A concrete example is: by default, an icon is defined for the Folder document type. If you redefine the folder document type from Studio and don't configure the Icon and Big Icon attributes, then if you select "override" for Deployment mode, your folders won't have any icon, while if you select "merge", they will keep the icon that was originally defined.

## Schema Tab

This is where you can define a schema for your document type. It shows:

*   The inherited schemas, i.e. schemas from the document type you are extending
*   The **Add extra schema to this document type** form: Select schemas from other document types to be available for your custom document type.
*   The **Add a custom schema** form: Define your own schema.
    This is equivalent to defining the schema from the [Schema]({{page page='schemas'}})&nbsp;feature and assign it from the **Add extra schema** form. Read the [Schema]({{page page='schemas'}}) page for more information on how to define your schema.

![]({{file name='doc_type_schema_tab.png' space='nxdoc' page='how-to-define-a-document-type'}} ?w=600,h=413,border=true)

## Creation, Edition, View and Header Layout Tabs

On those tabs, you can respectively configure the creation, edition, view and header layouts of the document type you are designing. They work like the&nbsp;[form layouts]({{page page='form-layouts'}})&nbsp;feature, thus you can follow the same instructions.

However there are a few differences/additional features:&nbsp;

*   The&nbsp;**Header layout**, which is not on the form layout feature is the part that is displayed on top of the tabs when viewing a document. By default, it displays the title and the description.
*   You don't have to reference the layout anywhere, they will be bound automatically to the document type you are configuring.
*   **External Layouts**: it is possible to "compose" the creation/edition/view/header layouts as being the aggregation of multiple layouts that are created from the&nbsp;[form layouts]({{page page='form-layouts'}})&nbsp;feature.

![]({{file name='creation_layout_form.png' space='nxdoc' page='how-to-define-a-document-type'}} ?w=600,border=true)

## Tabs - Default Tabs Filtering

![]({{file name='doc_type_tabs_tab.png' space='nxdoc' page='how-to-define-a-document-type'}} ?w=650,border=true)

Documents in DM are displayed with a series of tabs to display all the actions that can be done on documents. By default, a new document type will hold all the tabs. From this view in Studio, you can disable some of them, for the document type you are configuring. This is a binary activation/inactivation. If you want to refine the tabs display rules, you can&nbsp;[contribute XML extensions to the action service](http://explorer.nuxeo.org/nuxeo/site/distribution/current/viewExtensionPoint/org.nuxeo.ecm.platform.actions.ActionService--actions), so as to override existing contributions (for advanced users).

## {{> anchor 'tabs-content-views'}}Tabs - Content Views

![]({{file name='doc_type_content_view.png'}} ?w=650,border=true)

Content view tabs are tabs that display a list of documents in a table, that is the result of an&nbsp;[NXQL]({{page space='nxdoc' page='nxql'}})&nbsp;query (a content view). You configure the content view with the&nbsp;[content view feature]({{page page='content-views'}})&nbsp;and just reference it here.

*   **Main content**: you can choose which content view is used for the document you are configuring. This appears only for document types that are folderish.
*   **Trash content**&nbsp;**:&nbsp;**you can choose which content view is used for the document that are displayed in the trash. This appears only for document types that are folderish.
*   **Additional tabs configuration**:

    *   **Label**: The name displayed for this new tab. Can be a translated key.
    *   **Content views:**&nbsp;You can reference several content views that will be displayed one after the other.
    *   **Order**: The place of the tab on the document . You can put numbers like 0, 5, 10, 40, 150, ...
    *   **Tab Activation**: (TODO: a specific page for this screen that appears in many places on Studio).

{{#> callout type='info' heading='Using the Tabs feature'}}

Adding a tab that displays a content view using this feature is easy and straightforward, but you can also use the [Tabs feature]({{page page='tabs'}}) that provides more refinements like the ability to add buttons, other information, wrappers, etc...

{{/callout}}

* * *
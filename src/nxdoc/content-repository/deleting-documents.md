---
title: Deleting Documents
labels:
    - delete
    - life-cycle
    - last-review-20150123
toc: true
confluence:
    ajs-parent-page-id: '22380905'
    ajs-parent-page-title: Content Repository
    ajs-space-key: NXDOC60
    ajs-space-name: Nuxeo Platform Developer Documentation — 6.0
    canonical: Deleting+Documents
    canonical_source: 'https://doc.nuxeo.com/display/NXDOC60/Deleting+Documents'
    page_id: '22380733'
    shortlink: vYBVAQ
    shortlink_source: 'https://doc.nuxeo.com/x/vYBVAQ'
    source_link: /display/NXDOC60/Deleting+Documents
history:
    - 
        author: Solen Guitter
        date: '2015-01-23 14:04'
        message: ''
        version: '6'
    - 
        author: Alain Escaffre
        date: '2014-09-19 16:15'
        message: ''
        version: '5'
    - 
        author: Florent Guillaume
        date: '2014-04-25 12:30'
        message: soft-delete details
        version: '4'
    - 
        author: Solen Guitter
        date: '2014-04-11 10:55'
        message: ''
        version: '3'
    - 
        author: Florent Guillaume
        date: '2014-04-10 15:14'
        message: ''
        version: '2'
    - 
        author: Florent Guillaume
        date: '2014-04-10 15:00'
        message: ''
        version: '1'

---
{{! excerpt}}

Deleting a document involves several steps before the full document is actually deleted from the database and disk. These steps are described below.

{{! /excerpt}}

## Putting the Document in the Trash

For most standard document types in the Nuxeo Platform, the user interface action of deleting a document (**Delete**&nbsp;button) just puts it in the trash (visible in the&nbsp;**Manage**&nbsp;>&nbsp;**Trash**&nbsp;tab). Once in the trash, the document may be either undeleted (**Restore**&nbsp;button), or removed (**Permanent delete**&nbsp;button).

Putting a document in the trash is done by changing is life cycle state to&nbsp;**deleted**, by following the&nbsp;**delete** transition of the document's life cycle. If no such life cycle exists for the document, then it won't be put in the trash at all but will be immediately permanently deleted using the steps below.

When the trash is purged, all its documents are permanently deleted.

Besides the standard user interface, a document is put in the trash when using WebDAV, Nuxeo Drive, or using the [TrashService.trashDocuments](http://community.nuxeo.com/api/nuxeo/release-5.8/javadoc/org/nuxeo/ecm/core/trash/TrashService.html#trashDocuments(java.util.List)) API.

## Permanently Deleting the Document

A permanent delete is done by most Nuxeo APIs, typically [CoreSession.removeDocument](http://community.nuxeo.com/api/nuxeo/release-5.8/javadoc/org/nuxeo/ecm/core/api/CoreSession.html#removeDocument%28org.nuxeo.ecm.core.api.DocumentRef%29)&nbsp;or the higher-level APIs that use it like the CMIS bindings or the Automation [Document.Delete](http://explorer.nuxeo.org/nuxeo/site/distribution/Nuxeo%20Platform-6.0/viewOperation/Document.Delete) operation.

### Soft-Delete

If soft-delete is enabled (this is not the case by default), then the document is marked as deleted in the database (using a simple boolean flag) but no rows are actually removed. A search will not be able to find any document marked deleted in this way. From the application's point of view, the document is already fully deleted.

A scheduled periodic process will then hard-delete the documents marked as deleted at a later time, for asynchronous cleanup in fixed-sized batches.

{{#> callout type='info' heading='Using Soft-Delete'}}

Soft-delete can be enabled to relieve the database of expected heavy loads if many documents are deleted at the same time.

When Nuxeo has to hard-delete lots of documents, many rows in many tables, themselves related by foreign key constraints, have to be removed. On some databases this can use many resources (like undo segments for Oracle) and take a lot of time, so soft-delete is designed to spread these costly operations over time.

To activate soft-delete, you should change the repository configuration to add `<softDelete enabled="true" />`. See [Configuration Templates]({{page space='admindoc60' page='configuration-templates'}}) for more about updating the `default-repository-config.xml.nxftl` file.

Please consult [NXP-11335](https://jira.nuxeo.com/browse/NXP-11335) for more details about soft-delete and the configuration of the periodic cleanup.

{{/callout}}

### Hard-Delete

If soft-delete is not enabled, or when the periodic cleanup process for soft-delete happens, the document's data is actually physically deleted from the database by using `DELETE` statements (hard-delete).

&nbsp;

* * *

<div class="row" data-equalizer data-equalize-on="medium"><div class="column medium-6">{{#> panel heading='Related How-Tos'}}

*   [How to Enable the Trash Feature]({{page page='how-to-enable-the-trash-feature'}})&nbsp;
*   [How-To Index]({{page page='how-to-index'}})

{{/panel}}</div><div class="column medium-6">{{#> panel heading='Other Related Documentation'}}

*   [Deleting Content]({{page space='userdoc60' page='deleting-content'}}) (User documentation)
*   [Managing Deleted Documents]({{page space='userdoc60' page='managing-deleted-documents'}}) (User documentation)
*   [Garbage-Collecting Orphaned Binaries]({{page space='admindoc60' page='garbage-collecting-orphaned-binaries'}}) (Admin documentation)

{{/panel}}</div></div>
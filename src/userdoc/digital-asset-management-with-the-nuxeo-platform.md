---
title: Digital Asset Management with the Nuxeo Platform
review:
    comment: ''
    date: '2015-12-01'
    status: ok
labels:
    - multiexcerpt
    - multiexcerpt-include
toc: true
confluence:
    ajs-parent-page-id: '11043048'
    ajs-parent-page-title: Nuxeo Platform User Documentation
    ajs-space-key: USERDOC
    ajs-space-name: Nuxeo Platform User Documentation
    canonical: Digital+Asset+Management+with+the+Nuxeo+Platform
    canonical_source: >-
        https://doc.nuxeo.com/display/USERDOC/Digital+Asset+Management+with+the+Nuxeo+Platform
    page_id: '26312925'
    shortlink: 3YCRAQ
    shortlink_source: 'https://doc.nuxeo.com/x/3YCRAQ'
    source_link: /display/USERDOC/Digital+Asset+Management+with+the+Nuxeo+Platform
tree_item_index: 1800
history:
    -
        author: Solen Guitter
        date: '2016-04-20 08:00'
        message: ''
        version: '6'
    -
        author: Manon Lumeau
        date: '2016-04-19 15:36'
        message: ''
        version: '5'
    -
        author: Solen Guitter
        date: '2016-04-18 17:49'
        message: Add note about annotations removed from 8.2
        version: '4'
    -
        author: Solen Guitter
        date: '2015-08-27 12:48'
        message: ''
        version: '3'
    -
        author: Solen Guitter
        date: '2015-07-10 09:30'
        message: ''
        version: '2'
    -
        author: Solen Guitter
        date: '2015-07-10 09:30'
        message: ''
        version: '1'

---
{{! multiexcerpt name='Functional_overview'}}

The Nuxeo DAM document types are fully integrated in the Nuxeo Platform and are available alongside the other document types. They can be created the same ways as the platform default document types, they get the same metadata, the same workflows, etc.

### Pictures

Pictures are specific files. To take into account the specificities of pictures, their Summary tab shows additional pieces of information, such as:

*   Rotate actions
*   The picture's EXIF metadata
*   Additional picture views

Pictures can be [created]({{page page='creating-content'}}) and [edited]({{page page='editing-content'}}) in workspaces and folders like any other document type. You can also classify and organize them in [collections]({{page space='nxdoc' page='collections'}}).

When pictures are created, the EXIF metadata of the pictures are automatically extracted and displayed on the **Summary** tab. They cannot be modified. The IPTC legend, copyright and source are used to automatically fill in the description, rights and source metadata. See the page [Binary Metadata]({{page space='nxdoc' page='binary-metadata'}}) for more information.

![]({{file name='picsMetadata.png' space='nxdoc' page='digital-asset-management-dam'}} ?w=450,border=true)

You can report to the page [Supported File Formats]({{page space='nxdoc' page='supported-file-formats'}}) to see which file formats are supported as pictures.

#### Browsing Pictures

Nuxeo DAM add the possibility to view pictures in a slideshow mode from the thumbnail mode of a workspace or search results. To view the pictures in a slideshow mode, click on the icon ![]({{file name='slideshow_enabled.png' page='icons-index'}}) from the thumbnail mode. You can then switch from one picture to the next or the previous using the right and left keys of you keyboard. You automatically go the next page picture when you're at the last picture of the current page.

If no picture is available on the current page, it shows the icon ![]({{file name='slideshow_disabled.png' page='icons-index'}}).

{{! multiexcerpt name='annotating-pictures'}}

#### Annotating Pictures

{{! multiexcerpt name='picture-annotation-definition'}}

Annotations are post-it notes that users can add on the picture to comment it or to comment a specific part of the picture.

{{! /multiexcerpt}} {{#> callout type='note' }}

{{{multiexcerpt 'upgrade-8.2-remove-annotations' page='NXDOC:Upgrade from LTS 2015 following Fast Tracks'}}}

{{/callout}}

**To add an annotation on a picture:**

1.  To access to the image view, click on the icon&nbsp;![]({{file name='preview.png' page='icons-index'}})&nbsp;in the&nbsp;**More**&nbsp;menu.
    A pop up opens.
2.  Draw a frame on the part of the picture you want to annotate.
3.  Type your annotation and click on&nbsp;**Submit**.
    ![]({{file name='DAM-annotation.png' space='nxdoc' page='digital-asset-management-dam'}} ?w=600,border=true)
    You can see your annotation when the mouse is over the zone you selected, and, in the margin, the list of annotations, and for each, the author, date and time of annotation and the text.
    ![]({{file name='DAM-annotation-rollover.png' space='nxdoc' page='digital-asset-management-dam'}} ?w=600,border=true)

{{! /multiexcerpt}}

#### Picture Views

When you import a&nbsp;document having the `Picture` facet on your platform, additional formats are available on it.&nbsp;The default ones are:

*   Thumbnail: the picture is converted to JPG and resized to 100px height or width.
*   Small: the picture is converted to JPG and resized to&nbsp;280 px&nbsp;height or width.&nbsp;
*   Medium: the picture is converted to JPG and resized to 550 px height or width.
*   OriginalJpeg: the picture is converted to JPG but the original size is kept. This export is done even if the original picture was a JPG file.

{{#> callout type='tip' }}

The original and medium pictures can be the same size when you download them if the original is smaller or equal to medium size.

{{/callout}}

To download the picture view that you want, click on&nbsp;![]({{file name='download.png' space='userdoc58' page='icons-index'}})&nbsp;in front of it.

![]({{file name='Additionnal Picture Views Download.png' space='nxdoc' page='digital-asset-management-dam'}} ?w=600,border=true)

{{#> callout type='info' }}

To contribute new picture views, follow this [how-to]({{page space='nxdoc' page='how-to-contribute-picture-conversions'}}).

{{/callout}}

A user interface is added in the Admin tab so that it is possible to re-compute picture conversions (Picture views). This is particularly useful when you add new conversions and want to compute them over existing images, or if you change the definition of some of the existing conversions.

![]({{file name='Admin Picture Conversions.png' space='nxdoc' page='digital-asset-management-dam'}} ?w=650,border=true)

### Video

Video is a document types dedicated to the management of videos files. It provides the following specific features: A player to view the video from the application, a storyboard to navigate in the video and alternative video formats.

Video documents can be [created]({{page page='creating-content'}}) and [edited]({{page page='editing-content'}}) like any other document type. See the page&nbsp;[Supported File Formats]({{page space='nxdoc' page='supported-file-formats'}})&nbsp;for supported video files.

![]({{file name='video_document_type.png' space='nxdoc' page='digital-asset-management-dam'}} ?w=600,border=true)

#### Viewing Videos

Video documents can be viewed from their **Summary** tab where a video player is available. You can also navigate in the video using the Storyboard that is generated at import time.

#### Converting Videos

It is possible to convert the video to various formats from the user interface:

*   Ogg
*   WebM
*   MP4

To convert the video, from the **Summary** tab click on the **Convert** button corresponding to the format you want.

#### Exporting Videos

When your export a video asset, you get a folder with several files available:

*   The original video file
*   One WEBM conversion
*   One MP4 conversion
*   One JPEG picture by storyboard chapter
*   One JPG picture prefixed with "StaticPlayerView_video-screenshot-", which is the picture extracted from the video that is used for the player picture
*   One JPG picture prefixed with "Thumbnail_video-screenshot-", which is the thumbnail used in folders proposing a thumbnail view (typically in the DAM view)

A video is exported like any other document. See the page [Exporting Documents]({{page page='exporting-documents'}}).

### Audio

Audio is a document types dedicated to audio files management. It provides a player from the document **Summary** tab to listen to it from the application.

Audio documents can be [created]({{page page='creating-content'}}) and [edited]({{page page='editing-content'}}) like any other document type. They don't have any specific tab or action available.

See the page [Supported File Formats]({{page space='nxdoc' page='supported-file-formats'}}) for supported audio files.

![]({{file name='audio_document_type.png' space='nxdoc' page='digital-asset-management-dam'}} ?w=600,border=true)

{{! /multiexcerpt}}

{{! Don't put anything here. }}

* * *

<div class="row" data-equalizer data-equalize-on="medium"><div class="column medium-6">{{#> panel heading='Related User Documentation'}}

- [Creating Content]({{page page='creating-content'}})
- [Editing Content]({{page page='editing-content'}})
- [Collections]({{page page='collections'}})

{{/panel}}

&nbsp;

&nbsp;

</div><div class="column medium-6">{{#> panel heading='Other Related Documentation '}}

- [DAM developer documentation]({{page space='nxdoc' page='digital-asset-management-dam'}})
- [How to Contribute a New Video Conversion]({{page space='nxdoc' page='how-to-contribute-a-new-video-conversion'}})
- [How to Contribute Picture Conversions]({{page space='nxdoc' page='how-to-contribute-picture-conversions'}})

{{/panel}}</div></div>

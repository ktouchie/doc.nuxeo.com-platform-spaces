---
title: How to Impact Another JSF Component from a Command or Select
details:
    howto:
        excerpt: Learn how to impact another JSF component from a Command or Select.
        level: Advanced
        tool: Nuxeo IDE
        topics: 'Layout, JSF'
labels:
    - howto
toc: true
confluence:
    ajs-parent-page-id: '22380748'
    ajs-parent-page-title: JSF and Ajax Tips and How-To Index
    ajs-space-key: NXDOC60
    ajs-space-name: Nuxeo Platform Developer Documentation — 6.0
    canonical: How+to+Impact+Another+JSF+Component+from+a+Command+or+Select
    canonical_source: >-
        https://doc.nuxeo.com/display/NXDOC60/How+to+Impact+Another+JSF+Component+from+a+Command+or+Select
    page_id: '22380672'
    shortlink: gIBVAQ
    shortlink_source: 'https://doc.nuxeo.com/x/gIBVAQ'
    source_link: >-
        /display/NXDOC60/How+to+Impact+Another+JSF+Component+from+a+Command+or+Select
history:
    - 
        author: Anahide Tchertchian
        date: '2015-08-18 09:35'
        message: 'XDOC-649: fix first example, ajaxifying i'
        version: '6'
    - 
        author: Solen Guitter
        date: '2014-12-09 17:05'
        message: Fix typos
        version: '5'
    - 
        author: Anahide Tchertchian
        date: '2014-12-09 16:59'
        message: ''
        version: '4'
    - 
        author: Anahide Tchertchian
        date: '2014-12-09 16:27'
        message: 'NXDOC-363 : add howtos about selectionActions helpers'
        version: '3'
    - 
        author: Anahide Tchertchian
        date: '2014-12-01 14:52'
        message: ''
        version: '2'
    - 
        author: Anahide Tchertchian
        date: '2014-12-01 14:52'
        message: ''
        version: '1'

---
{{! excerpt}}

When designing a screen or form, you may want to render a part of the page when clicking on a link or when choosing an element in a select. This page explains how this can be done in a XHTML template.

{{! /excerpt}}

&nbsp;

This page describes how to do so without having to define a Seam component, keeping the contextual information. This is better for reuse of templates (like in widgets) within the same page, as you do not have to define a new Seam component for every context variable on the page.

The context variable is kept by a [nxu:valueHolder](http://community.nuxeo.com/api/nuxeo/release-6.0/tlddoc/nxu/valueHolder.html) tag, which also exposes the corresponding value in the context.

Two examples are given:

*   impact a given component with a static value
*   impact a given component with a value taken on another component

## Impacting with a Static Value

### Use Case

When i click on a button, another element should be hidden (or shown).

### Available Helper

The Seam Component [selectionActions](http://explorer.nuxeo.org/nuxeo/site/distribution/Nuxeo%20Platform-6.0/viewSeamComponent/seam:selectionActions) has a method named `setStaticValue` that will retrieve attributes named `selectedValue` and `targetComponentId` from its originating tag. It will lookup the corresponding component in the tree and set the value given by the `selectedValue` attribute (which can also be an EL expression).

### Sample Template Excerpt

```xml
<ui:fragment
  xmlns="http://www.w3.org/1999/xhtml"
  xmlns:ui="http://java.sun.com/jsf/facelets"
  xmlns:h="http://java.sun.com/jsf/html"
  xmlns:c="http://java.sun.com/jstl/core"
  xmlns:f="http://java.sun.com/jsf/core"
  xmlns:a4j="http://richfaces.org/a4j"
  xmlns:nxu="http://nuxeo.org/nxweb/util">

<h:form>

  [...]

 <a4j:outputPanel id="showContentHolderPanel">
    <nxu:valueHolder id="showContentHolder"
      defaultValue="false"
      var="showContent">

      <h:commandButton rendered="#{not showContent}" value="Show">
        <f:attribute name="selectedValue" value="true" />
        <f:attribute name="targetComponentId" value="showContentHolder" />
        <nxu:actionListenerMethod value="#{selectionActions.setStaticValue}"/>
        <f:ajax execute="@this" render="showContentHolderPanel" />
      </h:commandButton>
      <h:commandButton rendered="#{showContent}" value="Hide">
        <f:attribute name="selectedValue" value="false" />
        <f:attribute name="targetComponentId" value="showContentHolder" />
        <nxu:actionListenerMethod value="#{selectionActions.setStaticValue}"/>
        <f:ajax execute="@this" render="showContentHolderPanel" />
      </h:commandButton>

      <c:if test="#{showContent}">
        My content
      </c:if>

    </nxu:valueHolder>
  </a4j:outputPanel>

  [...]

</h:form>

</ui:fragment>
```

&nbsp;

## Impacting with a Value Taken on Another Component

### Use Case

When i select an element in a drop down list, another element should be displayed depending on the selected value.

### Available Helper

The Seam Component [selectionActions](http://explorer.nuxeo.org/nuxeo/site/distribution/Nuxeo%20Platform-6.0/viewSeamComponent/seam:selectionActions) has a method named `setValueFromComponent` that will retrieve attributes named `sourceComponentId` and `targetComponentId` from its originating tag. It will lookup the corresponding source component in the tree, retrieve its current value, and set this value to the corresponding target component.

### Sample Template Excerpt

This is an excerpt of the [widget template displaying additional information about a selected flavor](https://github.com/nuxeo/nuxeo-features/blob/release-6.0/localconf/nuxeo-localconf-web/src/main/resources/web/nuxeo.war/widgets/select_flavor_widget_template.xhtml) in local configuration:

```xml
<h:panelGroup>
  <nxu:set var="flavors"
    value="#{themeConfigurationActions.getAvailableFlavors(themeActions.defaultTheme)}"
    cache="true">
    <h:selectOneListbox id="#{widget.id}" value="#{field}">
      <nxu:selectItems
        var="flavor" value="#{flavors}"
        itemValue="#{flavor.name}" itemLabel="#{messages[flavor.label]}" />
      <f:attribute name="sourceComponentId" value="#{widget.id}" />
      <f:attribute name="targetComponentId" value="#{widget.id}_valueHolder" />
      <f:ajax execute="@this" render="#{widget.id}_preview"
        listener="#{selectionActions.setValueFromComponent}"
        id="#{widget.id}_ajax_select" />
    </h:selectOneListbox>
  </nxu:set>
  <h:message for="#{widget.id}" id="#{widget.id}_message"
    styleClass="errorMessage" />
</h:panelGroup>

<nxu:valueHolder id="#{widget.id}_valueHolder"
  var="selectedFlavorName"
  defaultValue="#{origSelectedFlavorName}"
  submitChanges="false">
  <a4j:outputPanel id="#{widget.id}_preview" layout="block">
    <nxu:set var="selectedFlavor"
      value="#{themeActions.getFlavor(selectedFlavorName)}"
      cache="true">
      <c:choose>
        <c:when test="#{! empty selectedFlavor.logo.previewPath}">
          <h:graphicImage value="#{selectedFlavor.logo.previewPath}" class="palettePreviewLogo" />
        </c:when>
        <c:otherwise>
          <c:choose>
            <c:when test="#{! empty selectedFlavor.logo.path}">
              <h:graphicImage value="#{selectedFlavor.logo.path}" class="palettePreviewLogo" />
            </c:when>
            <c:otherwise>
              #{messages['label.local.configuration.theme.flavorSelection.noPreviewAvailable']}
            </c:otherwise>
          </c:choose>
        </c:otherwise>
      </c:choose>
    </nxu:set>
  </a4j:outputPanel>
</nxu:valueHolder>
```
---
title: Incremental Layouts and Actions
labels:
    - lts2015-ok
    - layout-widgets-component
    - incremental-layout
    - summary-layout
confluence:
    ajs-parent-page-id: '28475523'
    ajs-parent-page-title: 'Actions (Links, Buttons, Icons, Tabs and More)'
    ajs-space-key: NXDOC710
    ajs-space-name: Nuxeo Platform Developer Documentation — LTS 2015
    canonical: Incremental+Layouts+and+Actions
    canonical_source: 'https://doc.nuxeo.com/display/NXDOC710/Incremental+Layouts+and+Actions'
    page_id: '28475812'
    shortlink: pIGyAQ
    shortlink_source: 'https://doc.nuxeo.com/x/pIGyAQ'
    source_link: /display/NXDOC710/Incremental+Layouts+and+Actions
history:
    - 
        author: Solen Guitter
        date: '2014-03-10 18:42'
        message: ''
        version: '6'
    - 
        author: Solen Guitter
        date: '2014-01-20 15:59'
        message: Added related topics
        version: '5'
    - 
        author: Solen Guitter
        date: '2014-01-13 09:48'
        message: ''
        version: '4'
    - 
        author: Anahide Tchertchian
        date: '2014-01-10 13:55'
        message: 'NXDOC-227: explain how to configure incremental layouts'
        version: '3'
    - 
        author: Anahide Tchertchian
        date: '2013-12-20 15:38'
        message: better title to avoid special chars
        version: '2'
    - 
        author: Anahide Tchertchian
        date: '2013-12-12 18:14'
        message: ''
        version: '1'

---
{{! excerpt}}

Actions are leveraged by the layout framework to include widgets inside layouts dynamically, benefiting from sorting and filtering features of actions within layouts.

{{! /excerpt}}

Configuration is a bit overkill for now; this could be simplified in the future, but the main principle is to:

1.  Define a layout including action widgets.
2.  Define action widgets referencing an [action category]({{page page='actions-display'}}) (depending on the use case).
3.  Define actions with type&nbsp;`widget` within this category, referencing a widget name.
4.  Define widgets with corresponding names.

Here is a complete example, taken from the default Nuxeo Summary layout, and showing how some widgets are shown conditionally on the page.

{{#> panel type='code' heading='Summary Layout Definition'}}

```xml
<extension target="org.nuxeo.ecm.platform.forms.layout.WebLayoutManager"
  point="layouts">
  <layout name="grid_summary_layout">
    <templates>
      <template mode="any">
        /layouts/layout_grid_template.xhtml
      </template>
    </templates>
    <rows>
      <row>
        <properties mode="any">
          <property name="nxl_gridStyleClass_0">gridStyle12</property>
        </properties>
        <widget>summary_panel_top</widget>
      </row>
      <row>
        <properties mode="any">
          <property name="nxl_gridStyleClass_0">gridStyle7</property>
          <property name="nxl_gridStyleClass_1">gridStyle5</property>
        </properties>
        <widget>summary_panel_left</widget>
        <widget>summary_panel_right</widget>
      </row>
      <row>
        <properties mode="any">
          <property name="nxl_gridStyleClass_0">gridStyle12</property>
        </properties>
        <widget>summary_panel_bottom</widget>
      </row>
    </rows>
  </layout>
</extension>
```

{{/panel}}

This layout is using a [grid]({{page page='layout-definitions#gridlayoutdefinition'}}), so that widgets are piled up within grid slots and stacked up correctly when some widgets are not displayed.

Let's look at the `summary_panel_left` widget configuration:

{{#> panel type='code' heading='Action Widget Definition'}}

```xml
<extension target="org.nuxeo.ecm.platform.forms.layout.WebLayoutManager"
  point="widgets">
  <widget name="summary_panel_left" type="documentActions">
    <handlingLabels>true</handlingLabels>
    <labels>
      <label mode="any"></label>
    </labels>
    <properties widgetMode="any">
      <property name="category">SUMMARY_PANEL_LEFT</property>
      <property name="subStyleClass">summaryActions</property>
    </properties>
  </widget>
</extension>
```

{{/panel}}

Actions can be displayed by this widget when using the category&nbsp;`SUMMARY_PANEL_LEFT`. Here is a sample action configuration:

```xml
<extension target="org.nuxeo.ecm.platform.actions.ActionService"
  point="actions">
  <action id="summary_note_text" type="widget" order="100">
    <category>SUMMARY_PANEL_LEFT</category>
    <properties>
      <property name="widgetName">summary_note_text</property>
    </properties>
    <filter-id>hasNote</filter-id>
  </action>
</extension>
```

This action is using the type `widget`, referencing the widget named&nbsp;`summary_note_text`. Note that it's also using a filter that makes sure the widget will be shown only when the document has a schema named `note`:

```xml
<extension target="org.nuxeo.ecm.platform.actions.ActionService"
  point="filters">
  <filter id="hasNote">
    <rule grant="true">
      <schema>note</schema>
    </rule>
  </filter>
</extension>
```

Finally, here is the widget configuration:

```xml
<extension target="org.nuxeo.ecm.platform.forms.layout.WebLayoutManager"
  point="widgets">
  <widget name="summary_note_text" type="richtext_with_mimetype">
    <fields>
      <field>note:note</field>
      <field>note:mime_type</field>
    </fields>
    <properties mode="view">
      <property name="translatedHtml">
        #{noteActions.translateImageLinks(field_0)}
      </property>
      <property name="cssClass">note_content_block</property>
    </properties>
    <controls mode="any">
      <control name="requireSurroundingForm">true</control>
    </controls>
  </widget>
</extension>
```

Note that the widget holds a control to make sure a form is added around it: the summary layout is not surrounded by a form since version 5.8 to allow defining fine-grained forms inside it.

&nbsp;

* * *

<div class="row" data-equalizer data-equalize-on="medium"><div class="column medium-6">{{#> panel heading='Related pages in current documentation'}}

**About actions:**

**About Summary layout:**

{{/panel}}</div><div class="column medium-6">{{#> panel heading='Related pages in Studio documentation'}}

**About actions:**

{{/panel}}</div></div>
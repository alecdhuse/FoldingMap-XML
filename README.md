# FoldingMap-XML

  This is the documentation for Folding Map's xml file format.  It includes style information.

## Outline Style
  OutlineStyle is used to detail how the outlines of Polygons and LineStrings are drawn.

### Tag Descriptions:
<pre>
    <borderCondition>
      The condition on when to use this OutlineStyle.  For Polygons the condition is the Class or Feature Type of the bordering Polygon sharing a vertex.  For LineStrings this tag is ignored.

    <color> 
      The color used to draw this outline.

    <selectedColor>
      The color used to draw this outline when the styled object is selected.

    <strokeStyle>
      The stroke style of the outline.  Current supported options are:

        - Solid
        - Solid-Dashed
        - Dashed
        - Dotted
        - Dash-Dotted

    <width>
      A float value indicating the width to draw the outline.
</pre>

####  Example:

<code>
  <outlineStyle>
    <borderCondition>Any</borderCondition>
	  <color>ffddbfa5</color>
	  <selectedColor>fff33e3e</selectedColor>
	  <strokeStyle>Solid</strokeStyle>
	  <width>1</width>
  </outlineStyle>
</code>

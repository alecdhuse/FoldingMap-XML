# FoldingMap-XML

  This is the documentation for Folding Map's xml file format.  It includes style information.

## \<Node\>
	Node are a single geospatial point.  A Node can be multidimensional, using at minimum, a Latitude and Longitude; 
	but also may including altitude and a timestamp.  
	
	- Altitude is mesured in meters above mean sea level.  
	- Latitude is mesured in decimal degrees (-90 to 90).
	- Longitude is measured in decimal degrees (-180 to 180).
	- Timestamp is in year-mm-ddThh:mm:ssZ format.  Example: 2012-09-06T22:41:24Z
	
	Each node has a refference id so map objects can use it as a componet.
	
	Nodes are defined at the begining of the FmXML file and are inclosed in the parent \<Nodes\> tag.
	
### Syntax:
	
	<node id="1">-3.025556,58.64749</node>
	<node id="2">-3.03,58.60027,3</node>
	<node id="3">-122.66198,45.52524,4,2012-09-06T22:41:24Z</node>

## \<OutlineStyle\>
  OutlineStyle is used to detail how the outlines of Polygons and LineStrings are drawn.

### Tag Descriptions:

    <borderCondition>
      The condition on when to use this OutlineStyle.  For Polygons the condition is the Class or Feature Type 
      of the bordering Polygon sharing a vertex.  For LineStrings this tag is ignored.

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

###  Example:

  	<outlineStyle>
   		<borderCondition>Any</borderCondition>
	  	<color>ffddbfa5</color>
	  	<selectedColor>fff33e3e</selectedColor>
	  	<strokeStyle>Solid</strokeStyle>
	 	<width>1</width>
  	</outlineStyle>

# FoldingMap-XML

  This is the documentation for Folding Map's xml file format (FmXml).  
  This format is based off of KML and OpenStreetMap.org with some furthur customization.
  
  FmXml includess style information as well as geospatial objects.
  
  General note about units: when using a unit within an FmXml file it should be in metric.

## \<Data\>
	The Data tag is used by Map Objects to store Key/Value Data.  Each object can only contain one of each key.
	If an object had multiple entries for a single key only the last entry is used, the others are discarded.

### Syntax:
	<data>
		<pair key="highway">residential</pair>
		<pair key="speed">80</pair>
	</data>

## \<Font\>

## \<GroundOverlay\>

## \<Heatmap\>
	Used to indicate a heatmap layer, these layers are dynamically generated.

## \<IconStyle\>
	Specifies how Points are drawn, usually by drawing an Icon, otherwise by a circle.
	
## \<LabelStyle\>
	Specified how Labels are to be drawn.
	
### Tag Descriptions:

	<Color>
		The main color of the label text.
		
	<OutlineColor>
		The outline color of the label text.
		
	<Font>
		Information on which font and size should be used for the label text.  
		See the Font Tag for more Information.
	
### Example:

	<labelStyle>
		<color>ffffffff</color>
		<outlineColor>ff3c444b</outlineColor>
		<font>
			<family>SansSerif</family>
			<style>Plain</style>
			<size>10</size>
		</font>
	</labelStyle>

## \<LatLonAltBox\>

## \<LinearRing\>

## \<LineStyle\>

## \<LineString\>

## \<Lod\>

## \<MultiGeometry\>

## \<Node\>
	Node are a single geospatial point.  A Node can be multidimensional, using at minimum, a Latitude and Longitude; 
	but also may including altitude and a timestamp.  
	
	- Altitude is mesured in meters above mean sea level.  
	- Latitude is mesured in decimal degrees (-90 to 90).
	- Longitude is measured in decimal degrees (-180 to 180).
	- Timestamp is in year-mm-ddThh:mm:ssZ format.  Example: 2012-09-06T22:41:24Z

	Each node has a refference id so map objects can use it as a componet.  This value is a long integer, and when 
	importing from OpenStreetMaps.org the ID will be the same as the OSM ID.  When importing from other sources, 
	ID will start at 1 and increment from there.
	
	Nodes are defined at the begining of the FmXML file and are inclosed in the parent <Nodes> tag.
	
### Syntax:
	
	<nodes>
		<node id="1">-3.025556,58.64749</node>
		<node id="2">-3.03,58.60027,3</node>
		<node id="3">-122.66198,45.52524,4,2012-09-06T22:41:24Z</node>
	</nodes>

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

## \<Point\>

## \<Polygon\>

## \<PolyStyle\>

## \<Region\>

## \<VectorLayer\>

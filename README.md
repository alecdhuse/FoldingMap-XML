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

	A three dimentional bounding box.
	
### Tag Descriptions:

	<north>
		The north bound of this bounding box.
		
	<south>
		The south bound of this bounding box.
		
	<east>
		The east bound of this bounding box.
	
	<west>
		The west bound of this bounding box.
		
	<minAltitude>
		The lower altitude bounds of this bounding box.
	
	<maxAltitude>
		The upper altitude bounds of this bounding box.
	
	<altitudeMode>
		Possible values are clampToGround, relativeToGround, and absolute.
		
### Example:

	<LatLonAltBox>
		<north>5.156742572784424</north>
		<south>5.222579479217529</south>
		<east>10.593417167663574</east>
		<west>10.464646339416504</west>
		<minAltitude>0.0</minAltitude>
		<maxAltitude>5000.0</maxAltitude>
		<altitudeMode>absolute</altitudeMode>
	</LatLonAltBox>

## \<LinearRing\>

## \<LineStyle\>

## \<LineString\>

## \<Lod\>

	Lod is an acronym for Level of Detail.  This tag describes the size of an area on the screen needed 
	for that area to be displayed.  

### Tag Descriptions:

	<minLodPixels>
		The minimum number pixels needed for this area to be displayed.  
		A value of -1 indicates this field is to be ignored.
		
	<maxLodPixels>
		The maximum number of pixels that can be displayed for this area.
		A value of -1 indicates this field is to be ignored.
		
	<minFadeExtent>
		Distance over which the map objects associated with this LOD fade, from fully opaque to 
		fully transparent.
	
	<maxFadeExtent>
		Distance over which the map objects associated with this LOD fade, from fully transparent to 
		fully opaque.
		
### Example:

	<Lod>
		<minLodPixels>633.0</minLodPixels>
		<maxLodPixels>100000.0</maxLodPixels>
		<minFadeExtent>0.0</minFadeExtent>
		<maxFadeExtent>0.0</maxFadeExtent>
	</Lod>
		
## \<MultiGeometry\>
	A containor for zero or more vector map objects.  Valid objects are:  Point, LineString, LinearRing, Polygon and 
	MultiGeometry.  
	
### Tag Descriptions:

	<description>
		The description for this object.
		
	<elements>
		Contains the elements that make up this MultiGeometry.
		
	<name>
		The name for this object.
		
	<ref>
		The reference ID for this object.
	
### Example:

	<multiGeometry id="id">
		<ref>2</ref>
		<name>Burnside Bridge</name>
		<description>Burnside Bridge MultiGeometry</description>
		<elements>
			<LineString id="Road - City Primary">
				<name>Burnside Bridge</name>
				<Ref>8004</Ref>
				<coordinates>40723784 1634664284 1328062041</coordinates>
			</LineString>
			<LineString id="Road - City Primary">
				<name>Burnside Bridge</name>
				<Ref>8001</Ref>
				<coordinates>1328062041 1634664269 333451694 1328062042</coordinates>
			</LineString>
		</elements>
	</multiGeometry>

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

## \<PhotoPoint\>
- Extends Point

  A GeoTagged photo displayed as a point on a map.

## \<Point\>

  A simple geographical object consisting of a single coordinate.
	
### Syntax:

	<Point id="Bar">
		<name>Yes and No</name>
		<Ref>4066</Ref>
		<coordinates>1234800640</coordinates>
	</Point>
	
## \<Polygon\>

	
## \<PolyStyle\>

## \<Region\>

## \<ScreenOverlay\>

## \<Style\>

	Defines a style that can be applied to vector objects within a given map.  A style is referenced by an id.
	The id is defined as an attribute of the style tag, see below.
	
### Syntax:

	<Style id="ID">

		<IconStyle>...</IconStyle>
  		<LabelStyle>...</LabelStyle>
  		<LineStyle>...</LineStyle>
  		<PolyStyle>...</PolyStyle>
	</Style>	
	
## \<TileSource\>

	Describes the soure for tiles used in a TileLayer.  The source can be a diectory structure, file, or a server address.
	
	The directory structure must be in the form: path/Zoom/X/Y.png  Where Zoom, X and Y are integers.
	File must be a .MbTile file.
	Server address must follow the Zoom/X/Y.png or Y.jpg format.
	
### Syntax:	
	
	<TileSource>
		<href>...</href> 
	</TileSource>
	
## \<VectorLayer\>

### Syntax:

	<VectorLayer>
		<name>New Layer</name>
		<objects>
			...
		</objects>
	</VectorLayer>

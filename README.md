# lcRhino
![Image](https://locivir.com/images/lcRhino.png) 

This document was last updated: *21 January 2023*

lcRhino is a Rhinoceros® plugin that started to implement idea's of use as a jewelry designer. 
With time more is has become an important tool for me and the designers I've had the pleasure working with.
I keep developing it as a hobby and progress will depend on available time. If you have suggestions or comments
please send an email to [ernst@locivir.com](mailto:ernst@locivir.com?subject=lcRhino).


## Getting started

Please install lcRhino with the Rhino PackageManager and accept the EULA.  
The plugin will enable four panels (all prefixed with *'lc'**) and below are the commands and their options listed.  

### Prerequisites

lcRhino needs to be running on the latest version of Rhino 7 on Windows, it will not work on a Mac. 

lcRhino is using .NET version 4.8.0, please make sure you have it installed. You can download it [here](https://dotnet.microsoft.com/download/dotnet-framework/thank-you/net48-offline-installer). Further information about .Net version 4.8.0 is on the [Microsoft website](https://support.microsoft.com/en-us/topic/microsoft-net-framework-4-8-offline-installer-for-windows-9d23f658-3b97-68ab-d013-aa3c3e7495e0).

Legacy versions for older versions of Rhino are still available for download as-is. These versions are not maintained anymore. 
Download here for: [Rhino 5](https://locivir.com/lcRhino/lcRhino_rh5-2020.11.21.22.rhi) or [Rhino 6](https://locivir.com/lcRhino/lcRhino_rh6-2020.11.21.22.rhi).
Please note that these versions use the Rhino Installer Engine. The easiest way to install is drag and drop the file into Rhino.

## Commands
The following commands are available in lcRhino (all commands start with the *"lc"* prefix to prevent command name collision) :

* ~~lcRegistration~~ - **lcRhino is free for use on an as-is basis, please read the EULA (see below).**
* lcLayerPanel - Alternative layer panel for layer management in Rhino.
* lcFingerSize - Insert a layer with a circle of the requested finger size.
* lcMultiOrient - Place object(s) on a (poly)surface with history in-command undo/redo.
* lcStones - Insert stones and cutters, see the stone size on the stones in your viewports, create summaries and more.
* lcFlowCrvSrf - Place objects along a curve on a (poly)surface with equal spacing between objects (not the same as equal spacing along the curve).
* lcCrvSelfIntersect - Enables display points on self-intersecting curve continuously without the need of running a separate command.
* lcScreenshot - Save multi-view images of the model without the need of creating layouts.
* lcSprue - Helps creating sprue's for casting 

### lcLayerPanel

***Documentation is Work-In-Progress***

Layer panel with easy selection of objects on layers, moving object across layers, copying object to layers and deleting object on layers. Faster access to toggle visibility and locked states of the layers.

* Show - Show the layer panel
* Hide - Hide the layer panel
* Toggle - Toggle the visibility of the layer panel
* Settings
	+ DisplayColor - Default color for new layers
	+ Tooltip - Show or hide the tooltips on the layer panel 

### lcFingerSize

*Options are available when running scripted (use the prefix "-" prefix when running the command, eg. -lcFingerSize)*

Sizes can be entered in different formats that are more human friendly, eg. 5, 5+, 5½, 5½-, 5 1/2, 5.5

* Offset - Offset (towards the inside of the finger) for production to allow the jeweller to finish the ring and still end up with the proper finger size. This will create a second circle if the offset is larger then 0.
* Color - Color of the finger size layer
* Standard - Select the finger size standard to use: US, British, French, German, Japan, Diameter (mm or inch), Circumference (mm or inch). A user-defined finger size list can also be used.
* DefaultStandard - Set the default finger size standard to use.
* Measure - Measure the diameter and get the (closest) finger sizes in all standards.
* Dialog - Show the dialog to select finger size.

### lcMultiOrient

[![lcMultiOrient presentation](https://img.youtube.com/vi/de1XB5hlafY/0.jpg)](https://youtu.be/de1XB5hlafY)

* *(while selecting source object)* PreviousSelection - Use last selected source object and plane.
* *(while selecting source plane)* 3Point - Assign custom source plane by selecting the center, x-axis and y-axis.
* *(while selecting target object)* PreviousSelection - Use last selected target object.
* Scale - Enter the scale (relative to the size of the source object) of the placed object. The scale can also be directly entered in the command prompt.
* Rotation - Enter the rotation (relative to the source xy-plane) of the placed object.
	+ Custom - Specify the rotation for each object
* Profile - Show the profile curve (including offset) while placing objects. The profile curve is created from the intersection of the source object with the source plane.
* Offset - Offset of the profile curve for easy spacing.

### lcStones

***Documentation is Work-In-Progress***

* Insert - Insert specified stone to the default insertion plane (world or current cplane)
* PlaceCutters - Place cutters for the selected stones (it will use the first available cutter for each different stone definition)
	+ Scale - Set a relative scale for the cutter proportional to the stone itself
* Summary
* Display
	+ DisplayStyle
		- Offset - Show the size of the stone and the profile curve (with specified offset)
		- OffsetOnly - Show the profile curve (with specified offset)
		- Shaded - Show the size of the stone 
		- Print - Hide the stone and show the size of the stone and the profile curve (no offset)  
	+ Show - Toggle showing or hiding the stone size or profile curve altogether
	+ Offset - Set the offset for the profile curve (0 means the profile curve itself)
	+ DisplayColor - Set the color of the text and profile curve
* lcStonePanel - Set the visibility of the stone panel
* Manage *(Any changes will be only available for current instance of Rhino unless saved.)*
	+ List -  Output a list of all stone definitions.
	+ Groups -  Maintain groups and the definitions inside the groups.  
	*(see "Edit stone groups submenu")*
	+ Save - Save current stone groups and definitions permanently. 
	+ Reload - Reload the groups and the definitions from the saved settings.   
	This cancels any edits of the stone groups and definitions.
  
		*The following commands are hidden unless in debug mode*
	+ Update - Load additional groups or definitions from the supplied file.  
	Current groups and definitions will not be affected.  
	+ Replace - Delete all stone groups and definitions and replace them with groups and definitions from the supplied file.
	+ Reset - Delete all stone groups and definitions and replace them with the default groups and definitions of the plugin.
	+ Export - Save all stone groups and definitions to the specified file.
	+ RegenerateCurves - Rebuild the profile curve for all stone definitions.

* *Edit stone groups sub-menu*
 	- List -  Output a list of all stone groups.
	- Add -  Add a new stone group  
	(all groups must have an unique name).
	- Edit -  Edit an exisiting stone group
		* Name - Adjust stone group name
		* Dimensions - How many dimensions to show on the stone and in the compact stone summary
		* Abbreviation - Stone group abbreviation. *(e.g. Rd for round)*
		* Image - Load a new image for the panel
		* Definitions - Sub-menu to edit the stone definitions within this group  
		*(see "Edit stone definitions submenu")*
		* Cutters - Sub-menu to edit the stone cutters within this group  
		*(see "Edit stone cutters submenu")*
		* Default - Set the default definition for this stone group when inserting a new stone into a document stone  
		(only available is more than one enabled definition is linked to the stone group)		
	- Remove - Remove a stone group.  
	**WARNING:** this will also delete any definitions within this group.
	- EditForm - Open the visual interface to edit the stone groups and definitions
  
* *Edit stone definitions sub-menu*  
	- List -  Output a list of all definitions within the group.
	- Add -  Add a new stone definition to the group  
	(all definitions must have an unique name within the group)
	- Edit -  Edit an exisiting stone definition
		* Name - Adjust stone definition name
		* Profile - Replace the automatically created profile with a custom profile curve
			+ Generate - Re-generate the profile curve
		* Description - Adjust the stone description
		* Replace - Replace the stone with a new object
	- Remove - Remove a stone definition.  
	
* *Edit stone cutters sub-menu*  
	***Documentation is Work-In-Progress***
	
### lcFlowCrvSrf

***Documentation is Work-In-Progress***


### lcCrvSelfIntersect

***Documentation is Work-In-Progress***

### lcScreenshot

***Documentation is Work-In-Progress***

### lcSprue

***Documentation is Work-In-Progress***

### The four different panels avaialble 
*lcStonePanel - user interface for the lcStones command*  
![Image](https://locivir.com/images/stonepanel.png)  
*lcLayerPanel - alternative user interface for layer usage*  
![Image](https://locivir.com/images/layerpanel-1.png)  
*lcSpruePanel - user interface to easily place casting sprue's on objects*  
![Image](https://locivir.com/images/spruepanel.png)  
*lcFlowCrvSrf - user interface place objects along a curve on  
 complex objects like (poly)surfaces, subD objects or meshes.*  
![Image](https://locivir.com/images/flowpanel.png)  

## Author

Ernst Plaatsman - [Locivir](http://locivir.com/)


## End-User License Agreement

Use of lcRhino is protected and governed by the EULA - see the [EULA](https://locivir.com/lcRhino/EULA.pdf) file for details

## Acknowledgments

Many thanks to *Vladimir Starkov*, *Caroline Royer* and *Manoueil Bairamian* for patience 
shown using lcRhino with all the bugs in it's early development.

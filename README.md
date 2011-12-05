License
=======

Copyright (C) 2011 Scott Harwell

This program is free software; you can redistribute it and/or
modify it under the terms of the GNU General Public License
as published by the Free Software Foundation; either version 2
of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.

INSTRUCTIONS
============

This is an attempt to create a plugin for Ajaxplorer that will allow you to create a form button to find a file on your server. The purpose of this plugin is to create something similar to CKFinder's "popup" functionality with Ajaxplorer.

How to Use
----------

Instructions assume use of jQuery on the host site.

1. Place the hook.popupchooser folder in your ajaxsplorer plugin directory.
2. In your javascript (either inline or the file you are using to define your functions) create a callback function.
	- The function should be named 'ajaxplorerPopupCallback'
	- The body of the function should do what you want with the image path (such as set an input value)

	function ajaxplorerPopupCallback(filePath){
		$('.imagepath').val(filePath);
	}
	
3. Create a function to popup the window:
	- (Required) The external_selector_type options must be set to popup.
	- (Required) The relative_path parameter must be set and it must point to the Ajaxplorer folder that stores your files.
	- (Optional) The filetypes array can be set if you want to limit the file extensions that can be returned. For instance, if you want to limit the files that can be returned to common image types, then use the format &filetypes[0]=jpg&filetypes[1]=gif&filetypes[2]=png&filetypes[3]=jpeg. Omitting the filetypes in the URL will allow any file type to be returned to your callback function.
	
	function chooseFile(){
		var fbWindow = window.open(
		"/ajaxplorer/?external_selector_type=popup&relative_path=/files/&filetypes[0]=jpg&filetypes[1]=gif&filetypes[2]=png&filetypes[3]=jpeg",
		"ajaxplorer",
		width=600,
		height=500
	);


CHANGE LOG
==========

##12/4/2011 - Ver .2###

- Added the ability to limit filetypes that can be returned through the `filetypes` array passed through the URL. 

Open to feature suggestions through GitHub Wiki.

##12/2/2011 - Ver .1###

Plugin created with simple abilities to select a file from a popup window and have the file path sent back to a callback function.
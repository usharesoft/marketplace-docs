.. Copyright (c) 2007-2016 UShareSoft, All rights reserved

.. _rebrand-welcome:

Customizing the Welcome Page
----------------------------

UForge Marketplace allows you to customize the welcome page text and color.

.. image:: /images/welcome-page.jpg

The following elements of the config.xml file allow you to customize the welcome page:

	* welcomeTitle : string displaying welcome message
	* welcomeLink : string of an external URL if the user clicks on the text
	* welcomeBackgroundColor : the color code in Hexa or RGB (#RRGGBB or rgba(red[0..255],green[0..255],blue[0..255],alpha[0.0..1.0]))
	* welcomeBackgroundImage :  a relative path to the image to display as a background
	* welcomeMessageLoggedInDisplay 

To do this, open the config.xml file and change the corresponding attributes in the client section. Run the marketplace_ui_update.sh script to enforce the changes.

.. code-block:: shell

	# vi /var/opt/UShareSoft/uforge-client/gwt/uforge/templates/config.xml

	<c:client>

	    <c:welcomeTitle>Welcome !</c:welcomeTitle>
	    <c:welcomeMessage>UForge Marketplace Platform</c:welcomeMessage>
	    <c:welcomeLink></c:welcomeLink>
	    <c:welcomeLinkText></c:welcomeLinkText>
	    <c:welcomeBackgroundColor></c:welcomeBackgroundColor>
	    <c:welcomeBackgroundImage></c:welcomeBackgroundImage>
	    <c:welcomeMessageLoggedInDisplay>true</c:welcomeMessageLoggedInDisplay>

	</c:client>

	# /opt/UShareSoft/uforge-client/bin/marketplace_ui_update.sh
	

Modifying the UI Title
----------------------

You can modify the title that appears in the browser when you open the UI of the UForge Marketplace.  Open the config.xml file, and change the title attribute in the client section.

Run the marketplace_ui_update.sh script to enforce the changes.

.. code-block:: shell

	# vi /var/opt/UShareSoft/uforge-client/gwt/uforge/templates/config.xml
	<c:client>

		<c:title>UForge Marketplace</c:title>

	</c:client>

	# /opt/UShareSoft/uforge-client/bin/marketplace_ui_update.sh




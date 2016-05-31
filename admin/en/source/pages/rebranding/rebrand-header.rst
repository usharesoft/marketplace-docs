.. Copyright (c) 2007-2016 UShareSoft, All rights reserved

.. _rebrand-header:

Customizing the Header
----------------------

UForge Marketplace allows you to customize the header by modifying the logo at the top right. Note that the logo and header can be different depending on if the user is logged in or not.

.. image:: /images/header.jpg

You can modify the logo that appears at the top of the page BEFORE a user is signed in. The following attributes can be modified:

	* headerLogoUrl: string to the relative path of the logo image.
	* headerLogoTitle: string of the logo tooltip (when a user scrolls over the logo)
	* headerLogoLink: string of an external URL if the user clicks on the logo.

To do this, open the config.xml file and change the corresponding attributes in the ``client`` section. Run the marketplace_ui_update.sh script to enforce the changes.

.. code-block:: shell

	# vi /var/opt/UShareSoft/uforge-client/gwt/uforge/templates/config.xml

	<c:client>

	    <c:headerLogoUrl>images/signedInLogo.png</c:headerSignedInLogoUrl>
	    <c:headerLogoTitle>Go to UShareSoft.com</c:headerSignedInLogoTitle>
	    <c:headerLogoLink>http://usharesoft.com</c:headerSignedInLogoLink>

	</c:client>

	# /opt/UShareSoft/uforge-client/bin/marketplace_ui_update.sh
	


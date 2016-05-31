.. Copyright (c) 2007-2016 UShareSoft, All rights reserved

.. _modify-logo:

Modifying the Logo when Signed In
---------------------------------

You can modify the logo that appears at the top of the page once a user is signed in. The following attributes can be modified:

	* headerSignedInLogoUrl: string to the relative path of the logo image.
	* headerSignedInLogoTitle: string of the logo tooltip (when a user scrolls over the logo)
	* headerSignedInLogoLink: string of an external URL if the user clicks on the logo.

To do this, open the config.xml file and change the corresponding attributes in the client section. Run the marketplace_ui_update.sh script to enforce the changes.

.. code-block:: shell

	# vi /var/opt/UShareSoft/uforge-client/gwt/uforge/templates/config.xml

	<c:client>

	    <c:headerSignedInLogoUrl>images/headerSignedInLogo.png</c:headerSignedInLogoUrl>
	    <c:headerSignedInLogoTitle>Go to UShareSoft.com</c:headerSignedInLogoTitle>
	    <c:headerSignedInLogoLink>http://usharesoft.com</c:headerSignedInLogoLink>

	</c:client>

	# /opt/UShareSoft/uforge-client/bin/marketplace_ui_update.sh
	


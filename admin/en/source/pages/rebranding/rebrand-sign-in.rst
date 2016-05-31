.. Copyright (c) 2007-2016 UShareSoft, All rights reserved

.. _rebrand-sign-in:

Modifying the Sign-In and Sign-Up Page
--------------------------------------

You can modify a few elements on the sign-in and sign-up page.  

Figure 3.4: Sample Sign-in Page

You can modify the logo and that appears on the sign-in and sign-up page in client section of the config.xml file.  The following attributes can be modified:

	* signInLogoUrl: string to the relative path of the logo image.
	* signInLogoTitle: string of the logo tooltip (when a user scrolls over the logo)
	* signInLogoLink: string of an external URL if the user clicks on the logo.
	* externalSignUpUrl: string of an external URL used when a user clicks on “Need an account? Sign up” section.  This allows external custom sign up pages to be integrated with the Marketplace.

.. code-block:: shell

	# vi /var/opt/UShareSoft/uforge-client/gwt/uforge/templates/config.xml

	<c:client>

	    <c:signInLogoUrl>images/signInLogo.png</c:signInLogoUrl>
	    <c:signInLogoTitle>Go to UShareSoft.com</c:signInLogoTitle>
	    <c:signInLogoLink>http://usharesoft.com</c:signInLogoLink>
	    <c:externalSignUpUrl>http://www.usharesoft.com/products/signup</c:externalSignUpUrl>

	</c:client>

	# /opt/UShareSoft/uforge-client/bin/marketplace_ui_update.sh

Hiding Option to Modify Password
--------------------------------

You can choose to hide the option to modify the password on the “My Account” page (visible once a user has signed in).  This is interesting when you wish the user to manage the profile and password settings from another service or if have your own authentication mechanism and do not wish Marketplace users to be able to change the password, since their credentials are managed somewhere else. 

To do so, open the config.xml file and set the showChangePassword attribute to “false” in client section. Run the marketplace_ui_update.sh script to enforce the changes.

.. code-block:: shell

	# vi /var/opt/UShareSoft/uforge-client/gwt/uforge/templates/config.xml
	<c:client>

		<c:showChangePassword>false</c:showChangePassword>

	</c:client>

	# /opt/UShareSoft/uforge-client/bin/marketplace_ui_update.sh	


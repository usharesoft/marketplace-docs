.. Copyright (c) 2007-2016 UShareSoft, All rights reserved

.. _terms-of-use:

Modifying the Terms of Use or Privacy Policy
--------------------------------------------

If you wish to modify the terms of use or privacy policy you must include the UShareSoft “Terms of Use” and “Privacy Policy” as part of your own, or have written consent from UShareSoft that you can change these policies.

To modify the Terms of Use or Privacy Policy, open the config.xml file and go to the footer section and enter the path to the new terms of use and/or privacy policy. Run the marketplace_ui_update.sh script to enforce the changes.

.. code-block:: shell

	# vi /var/opt/UShareSoft/uforge-client/gwt/uforge/templates/config.xml

	<c:footer>
		<c:footerItem>
	           <c:title>terms of use</c:title>
	           <c:link>https//www.usharesoft.com/about/terms-of-use.html</c:link>
		</c:footerItem>
		<c:footerItem>
	           <c:title>privacy policy</c:title>
	           <c:link>https//www.usharesoft.com/about/privacy-policy.html</c:link>
		</c:footerItem>

	</c:footer>

	# /opt/UShareSoft/uforge-client/bin/marketplace_ui_update.sh


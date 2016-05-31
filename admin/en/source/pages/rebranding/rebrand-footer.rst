.. Copyright (c) 2007-2016 UShareSoft, All rights reserved

.. _rebrand-footer:

Customizing the Footer
----------------------

The following sections in the config.xml file allow you to customize the footer:

	* showUForgeUrl: boolean to determine if you display the base url of the Marketplace service
	* version: string displaying the current version of the UI
	* copyright: string displaying the copyright information

You can also customize the footer menu on the bottom left hand side (see figure 3.3).  This can be to replace, remove or add new text, icons and references.

Figure 3.3: Sample Footer with Default Settings

By default, UForge Marketplace has the following footer items:

	* Link to Twitter – https://twitter.com/usharesoft
	* Privacy policy – https://www.usharesoft.com/about/privacy-policy.html
	* Terms of Use – https://www.usharesoft.com/about/terms-of-use.html

Each footerItem contains:

	* title: a string display some text that is visible when the navigation bar is fully open.
	* icon: a relative path to the SVG image to display when the navigation bar is closed.
	* link: an URL to an external web page

You can remove and update any of the defaults or add new footer items.  For example, if you want to create a new footer item for a blog page, then you simply update the config.xml and run the marketplace_ui_update.sh script to enforce the changes.

.. code-block:: shell

	# vi /var/opt/UShareSoft/uforge-client/gwt/uforge/templates/config.xml

	<c:footer>

	    <c:footerItem>
	        <c:title>Blogs</c:title>
	        <c:icon>images/mycompany/blogs.svg</c:icon>
	        <c:link>https://www.myblog.com</c:link>
	    </c:footerItem>

	</c:footer>


	# /opt/UShareSoft/uforge-client/bin/marketplace_ui_update.sh


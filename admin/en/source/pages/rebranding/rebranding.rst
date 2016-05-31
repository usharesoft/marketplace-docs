.. Copyright (c) 2007-2016 UShareSoft, All rights reserved

.. _rebranding-mp:

Rebranding UForge Marketplace
=============================

The presentation layer is built using GWT (Google Web Toolkit) that produces HTML, Javascript and CSS.  A configuration file named config.xml is provided to facilitate basic customization of the user interface.  For more advanced rebranding, a custom CSS file is used to override the default stylesheets provided in UForge Marketplace.
The configuration file is located in::

	/var/opt/UShareSoft/customization/marketplace-client/config.xml

The custom css file to use for overriding default stylesheets is located in::

	/var/opt/UShareSoft/customization/marketplace-client/css/custo.css

Whenever changes have been made to either the custo.css or the config.xml files, for those changes to take effect, the administrator must run the following command. This will stop Tomcat, integrate the changes and restart Tomcat::

	# /opt/UShareSoft/uforge-client/bin/marketplace_ui_update.sh

This command stops the U web service (Tomcat), integrates the changes and restarts the web service.

The following sub-sections cover the various rebranding options in detail.

.. toctree::
   :titlesonly:

   custom-logos
   regrand-sign-in
   rebrand-welcome
   rebrand-header
   modify-logo
   rebrand-footer
   terms-of-use
   advanced-css
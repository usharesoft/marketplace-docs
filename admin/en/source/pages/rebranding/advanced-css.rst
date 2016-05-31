.. Copyright (c) 2007-2016 UShareSoft, All rights reserved

.. _advanced-css:

Advanced CSS
------------

To provide deeper customization, for example background, font types, sizes, colors and layouts, you will require to override the default cascading stylesheets of the marketplace UI.  Overriding these styles is provided by updating the custo.css file.

.. code-block:: shell

	# vi /var/opt/UShareSoft/customization/marketplace-client/css/custo.css

Some basic examples are provided in the custo.css file (commented out).

Changing Link Color
~~~~~~~~~~~~~~~~~~~

To change the default link color, simply override the following in the custo.css file:

.. code-block:: shell

	# vi /var/opt/UShareSoft/customization/marketplace-client/css/custo.css

	a {
	    color: rgb(0, 128, 0) !important;
	}
	a:hover {
	    color: rgb(50, 128, 0) !important;
	}

	# /opt/UShareSoft/uforge-client/bin/marketplace_ui_update.sh


Changing Title Fonts
~~~~~~~~~~~~~~~~~~~~

To change the default title font styling (in this example the color), simply override the following in the custo.css file:

.. code-block:: shell 

	# vi /var/opt/UShareSoft/customization/marketplace-client/css/custo.css

	.title, .subTitle {
	    color: rgb(255, 0, 0);
	}

	# /opt/UShareSoft/uforge-client/bin/marketplace_ui_update.sh


Changing Button Style
~~~~~~~~~~~~~~~~~~~~~

To change the button styling, simply override the following in the custo.css file:

.. code-block:: shell

	# vi /var/opt/UShareSoft/customization/marketplace-client/css/custo.css

	.expandableButton {
	    background: rgb(255, 215, 0);
	    border-color: rgb(255, 0, 0);
	}
	.expandableButton .expandableButtonContent svg path {
	    fill: rgb(255, 0, 0) !important;
	    stroke: rgb(255, 0, 0) !important;
	}

	# /opt/UShareSoft/uforge-client/bin/marketplace_ui_update.sh


.. Copyright (c) 2007-2016 UShareSoft, All rights reserved

.. _custom-logo:

Adding Custom Logos and Images
------------------------------

If you plan to include your own logos and images when customizing the user interface, you should create a sub-directory under: /var/opt/UShareSoft/uforge-client/gwt/uforge/templates/images

For example, place all your logos and images under the sub-directory “mycompany”::

	# mkdir -p /var/opt/UShareSoft/uforge-client/gwt/uforge/templates/images/mycompany

You can then update the relevant sections of the config.xml or custo.css to use these images.
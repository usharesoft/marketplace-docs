.. Copyright (c) 2007-2016 UShareSoft, All rights reserved

.. _marketplace-basic-concepts:

Basic Concepts
==============

The UForge Marketplace is an App Store for all types of Products such as: templates, machine images, plugins, binaries, scripts, etc. It is not limited to UForge appliance templates.

In order to add or download products from the Marketplace you must have an account and be logged in. However, to view and browse the marketplace you do not need to be logged in.

There are three types of user for the Marketplace:

	* ``Consumer``: A user who wishes to browse and buy product items in the Marketplace
	* ``Vendor``: A user who can add and manage product items in the Marketplace.  There are two types of vendors: ``Corporate`` or ``Developer``. A corporate vendor can have several members (users).
	* ``Channel Manager``: An administrator of the Marketplace who approves product items added by vendors.

.. image:: /images/marketplace-workflow.png

The figure illustrates the typical workflow. A Vendor posts a product to the Marketplace. Once the products are approved by the Channel Manager products are visible and accessible to other users of the Marketplace.

Each Product has a type (for example Template, image, plugin, binary, script) with optional marketing, support and pricing information.

.. image:: /images/product-schema.png

The Vendor defines the Marketing information, Support plan, and Pricing plan associated to the product.

Once you are logged in to the Marketplace you will see a general view of the marketplace, similar to the following.

.. note:: The menu options on the left hand will depend on whether your Marketplace is linked to an UForge AppCenter or not. The following image shows a Marketplace associated to an AppCenter.

.. image:: /images/MP-mainpage.jpg

* At the top of the page you can click to go to your private areas: My Purchases and My Favorites.
* In the main area you can filter and search for products available on the Marketplace.
* In the bottom part you can view the products which have been sorted by: Featured, Latest, Popular, Highly Rated.
* From the left-hand menu you can go to:

	* Marketplace, to view and purchase products.
	* Credentials, to manage your cloud accounts, SSH keys, as well as your password.
	* Profile, to change your contact information.
	* Administration (only if you are an administrator)
	* VM Builder. This is only available for users that also have a UForge AppCenter. This is where your appliances are created and listed. You also go to this page to add custom software, update packages in appliances, and create images.
	* Collaboration. This is only available for users that also have a UForge AppCenter. This is a private area where you can share appliances with other users who are part of your workspace. These users must be invited and join your workspace. 
	* Migration. This is only available for users that also have a UForge AppCenter. This is where you can launch a scan of a live system, view the results, or compare scans.
	* At the bottom left you will find standard links to twitter, terms of use and privacy policy.

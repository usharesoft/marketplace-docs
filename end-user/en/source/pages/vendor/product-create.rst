.. Copyright (c) 2007-2016 UShareSoft, All rights reserved

.. _product-create:

Creating a Product
------------------

In order to create a product, you must be a Vendor. When you create a new product, you must provide a unique name, version, type and part number. All the other elements of a product can be added at a later time. 

Once the product is created you can edit everything except the type.

.. Note:: The Marketing plan, Support plan and Pricing plan should already be created if you want to add them at the same time as you create a product. Otherwise you can create these elements later and add them to the product by updating the product.

Each product can have one or several `product items`. When using the Marketplace UI, you create the product item and product at the same time.

.. note:: Markdown is supported as an input language

From the Marketplace UI, create a product as follows:

	1. Click on ``My Listings``.
	2. If you have several vendors, click on the Vendor who will be the creator to the product. 

	.. image:: /images/create-product.jpg

	3. Click on create product +.

	.. image:: /images/create-productlisting.jpg

	4. Enter the Product Name, Type, Version and Part number. If you do not want to create a part number you can click “Generate part number” on the right (as shown in the following figure). Click the next arrow.

	.. image:: /images/create-SKU.jpg


	5. Add the Marketing Plan. If none have been created, you can create one by clicking on create one +. You can also skip this step and add the plan later by editing the product item. Refer to Creating a Marketing Plan with UI. Click the next arrow.
	6. Add the Support Plan. If none have been created, you can create one by clicking on create one +. You can also skip this step and add the plan later by editing the product item. Refer to Creating a Support Plan with UI. Click the next arrow.
	7. Add the Pricing Plan. If none have been created, you can create one by clicking on create one +. You can also skip this step and add the plan later by editing the product item. Refer to Creating a Pricing Plan with UI. Click the next arrow.
	8. Add the artifact (or URL in the case of a SaaS-type product). How you add this data to the product item will depend on the type of product:

		* For an Appliance template, you can connect to your UForge account.

		.. image:: /images/add-appliance-to-product.jpg

		* For a cloud add-on or software component, click on upload + to upload the data. The artifact can be a compressed archive (.tar, .tar.gz, .zip); or add-on file (e.g. .jar, .rpm etc). 
		* For Docker containers
		* For a Machine image, click on add + . Optionally you can connect to your UForge account if you want to use an image from your AppCenter. You can either upload the image to your marketplace, or provide a URL end-point where the consumer can access the machine image.

		.. image:: /images/add-image-to-product.jpg

		* For SaaS enter the URL for the SaaS landing page.

	9. Add the release notes and installation instructions.
	10. (Optionally) Add the products that are compatible by selecting them from the compatibility list. You can also search the compatible product list using the search filter. Click on the next arrow to continue.

	.. image:: /images/add-compatible-product.jpg

	11. Click save.

	.. note:: Once a product has been created, you must submit it for approval by a Channel Manager before it can be visible on the Marketplace. Refer to :ref:`submit-product`.
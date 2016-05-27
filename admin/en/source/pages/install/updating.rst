.. Copyright (c) 2007-2016 UShareSoft, All rights reserved

.. _updating-mp:

Updating UForge Marketplace
---------------------------

You must have completely installed and configured the Marketplace before running the update procedure.

If you wish to update UForge Marketplace to the latest version, you need to run the following steps.

	1. Run the following commands to refresh the UShareSoft Marketplace YUM repository:

	.. code-block:: shell

	    yum clean all
	    yum makecache

	2. Update all the UForge Marketplace packages::

	    yum update uforge-auth-db uforge-marketplace-*

	3. Apply the UForge Marketplace database schema updates::

	    /opt/UShareSoft/marketplace/db/conf/update_marketplace_db_schema.sh 

	If suspicious errors are displayed when running this command, please run it a second time.

	4. Update the UForge Marketplace webservice::

	    /opt/UShareSoft/marketplace/ws/conf/update_scripts/update_marketplace_ws.sh

	5. Check that the webservice is ok::

		curl http://localhost:8080/mpws/users/root -u ADMIN:PASSWORD

	Where ADMIN and PASSWORD can be found for the MARKETPLACE_REGISTRATION_USER in 
	etc/UShareSoft/marketplace/marketplace.conf
	This should not return an error.

	6. Update the portal::

	    /opt/UShareSoft/marketplace-client/bin/marketplace_ui_update.sh

	7. Restart the event bus controller::
	
	    service marketplace-event-controller restart

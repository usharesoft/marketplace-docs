.. Copyright (c) 2007-2016 UShareSoft, All rights reserved

.. _shared-storage:

Using Shared Storage
--------------------

You can use NFS to store the user UForge Marketplace data.  To setup the NAS or SAN for the UForge Marketplace you must create a shared directory.

To setup a shared storage:

	1. Log in to the machine where the NFS server is running.
	2. Create the Marketplace shared directory on the NFS server, for example: /volume1/MARKETPLACE

	The following NFS options are required::

		*(rw,async,no_wdelay,no_root_squash,insecure_locks,anonuid=0,anongid=0)
	
	3. On the UForge Marketplace server:

		a. For NFS, you may have to install the following package but it should be in the latest 3.0.3 Marletplace template::

			yum install nfs-utils

		b. Execute the following commands to setup the shared storage directory:

		.. code-block:: shell

			service tomcat stop
			mv /var/opt/UShareSoft/marketplace /var/opt/UShareSoft/marketplace-old
			mkdir /var/opt/UShareSoft/marketplace
			cd !$
			chown -R tomcat:tomcat

		c. Set the mount point: 

		.. code-block:: shell

			mount SAN_IP:/volume1/MARKETPLACE /var/opt/UShareSoft/marketplace 

		d. Execute the following commands to verify:

		.. code-block:: shell

			su - tomcat 
			cd /var/opt/UShareSoft/marketplace 
			touch test 

		This should not return::

			touch: cannot touch `test': Permission denied 
		
		Then execute::
		
			rm test

		e. Restore the initial Marketplace data::

			rsync -a --progress  /var/opt/UShareSoft/marketplace-old/* /var/opt/UShareSoft/marketplace/

		f. Check that the previously existing data are present on /var/opt/UShareSoft/marketplace, and delete the saved data:

		.. code-block:: shell

			ls -l /var/opt/UShareSoft/marketplace
			rm -rf /var/opt/UShareSoft/marketplace-old

		g. In order to have a persistent mount point on every boot, you need to add an entry in /etc/fstab, for example::

			SAN_IP:/volume1/MARKETPLACE	/var/opt/UShareSoft/marketplace/	nfs defaults,auto,noatime,nolock	0 0

		h. And finally execute::

			service tomcat start
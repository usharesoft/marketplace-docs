.. Copyright (c) 2007-2016 UShareSoft, All rights reserved

.. _install-requirements:

Hardware Requirements
---------------------

UForge Marketplace can be installed either on physical machines or in a virtual or cloud environment.  The minimal installation requirements are:

	* One physical or virtual machine where UForge will be installed
	* Optionally a NAS or SAN for storage (otherwise the local disk of the VM)

The UForge Marketplace platform requires the following hardware (for one-node installation):
CPU
4 cores (10 cores recommended)
RAM
4 GB or more  (10 GB recommended)
Local Hard Drive
30GB
Storage 
400GB, note this depends on the number and type of product artifacts you wish to store and show via the marketplace

Depending upon the scalability, security and reliability requirements the various components and networking architecture comprising the platform may be installed differently.  For example:

	* Multiple web servers can be deployed and load balanced.  The administrator may also wish to have multiple load balancers in the case where the load balancer itself may fail.
	* The database can be installed separately and also setup in master-slave or clustered mode for high availability.
	* The LDAP and IDM service can be installed  separately and also setup in MMR (multi-master replication) for high availability.
	* Create a DMZ between the web server layer and the generation cluster and database layers.

Installation Checklist
----------------------

Before you start deploying UForge Marketplace, ensure that you have all the following:

	* UForge Marketplace Media
	* Your activation credentials (ID and activation key) provided by UShareSoft
	* Architecture of the deployment (number of nodes and networking topology. See “Architecture and Networking Topologies” for more information)
	* The necessary system requirements
	* Your SSL certificates, key and chaining certificates, and all files corresponding to the following entries in /etc/httpd/conf.d/ssl.conf:

		- SSLCertificateFile
		- SSLCertificateKeyFile
		- SSLCACertificateFile
		- SSLCertificateChainFile (might be empty)
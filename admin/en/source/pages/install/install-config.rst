.. Copyright (c) 2007-2016 UShareSoft, All rights reserved

.. _install-config:

Configuring the Marketplace
---------------------------

Once the installation is complete on all the nodes you want to use for the UForge Marketplace platform, you are now ready to configure all the platform services.  An installation program is provided for a one-node Marketplace installation.  To configure the Marketplace:

	1. Launch the installer program:: 

		/opt/UShareSoft/marketplace/installer/marketplace-single-node-deployer.sh

	To view the options use::

		/opt/UShareSoft/marketplace/installer/marketplace-single-node-deployer.sh --help

	For example, to launch the configuration you will run something like::

		/opt/UShareSoft/marketplace/installer/marketplace-single-node-deployer.sh -e <email> -o <org> -p <password>

	This configuration phase will take approximately 10 to 15 minutes.  Once complete, the Marketplace will be available at the following URLs (unless you have customized them):

		* UI: http://youripaddress:8080/marketplace or https:youripaddress:8080/marketplace
		* API usage: http://youripaddress:8080/mpws or https://youripaddress:8080/mpws

	2. Customize config.xml for this instance. Refer to :ref:`rebranding-mp`

	vi /var/opt/UshareSoft/customization/marketplace-client/config.xml

	For instance in this file you can modify the following but default are set properly by the deployment scripts:

		* in the client section, edit the resourcesUrl and apiUrl with the correct machine ip/name
		* leave the c:activationKey to its default value

Configure Apache to use SSL Certificate
---------------------------------------

It is highly recommended that all communication with UForge is done via HTTPS.  After the initial installation of UForge, the HTTP server (Apache) is not yet configured to use a SSL certificate and allow HTTPS.

To configure both servers to use an SSL certificate:

	1. Log in as root to the machine running the UForge Apache and GlassFish Web Services
	2. Copy the SSL certificate files locally to the machine.  Note that you should have three to four files, for example:

		* SSLCertificateFile: server.crt.pem
		* SSLCertificateKeyFile: server.key.pem
		* SSLCACertificateFile: CA.crt.pem
		* SSLCertificateChainFile: intermediate.CA.crt.pem (this one is optional)
	
	You need to build a self contained certificate as follows::

		# cat server.crt.pem CA.crt.pem > server_CA_chain.crt.pem
	
	or::

		# cat server.crt.pem intermediate.CA.crt.pem CA.crt.pem > server_CA_chain.crt.pem


	Note that .pem files contain the following kind of data for certificate files:

	.. code-block:: shell

		# cat server.crt.pem
		-----BEGIN CERTIFICATE----- 
		MIIHJTCCBg2gAwIBAgIDB25YMA0GCSqGSIb3DQEBBQUAMIGMMQswCQYDVQQGEwJJ 
		...
		aW9uIEF1dGhvcml0eTADAgECGmRMaWFiaWxpdHkgYW5kIHdhcnJhbnRpZXMgYXJl
		V4XfZvZtrRcZ 
		-----END CERTIFICATE-----

	And the following data for the key file:

	.. code-block:: shell

		# cat server.key.pem
		-----BEGIN PRIVATE KEY----- 
		MIIEvwIBADANBgkqhkiG9w0BAQEFAASCBKkwggSlAgEAAoIBAQDaRIAE7wrKbS9T 
		...
		GdIr+qaNjk+eZLVsuPsAvwPlsWI/Cip7Zqygtvviteyen0VZbLpRJgbbjXqh9GwP 
		G33VnWF89pfm5FNRu3WHIf8Ukw== 
		-----END PRIVATE KEY----- 

	If this is not the case, refer to the OpenSSL documentation on how to convert certificate and key files from one format to another.

	3. Put the following entries in /etc/httpd/conf.d/ssl.conf:

	.. code-block:: shell

		SSLCertificateFile /etc/pki/tls/certs/server.crt.pem 
		SSLCertificateKeyFile /etc/pki/tls/private/server.key.pem 
		SSLCertificateChainFile /etc/pki/tls/certs/intermediate.CA.crt.pem 
		SSLCACertificateFile /etc/pki/tls/certs/CA.crt.pem

	4. Verify the permissions and ownerships of these files:

	.. code-block:: shell

		# ll -d /etc/pki/tls/certs/server.crt.pem /etc/pki/tls/private/localhost.key /etc/pki/tls/private/ /etc/pki/tls/certs/ 
		drwxr-xr-x. 2 root root 4096 Sep 25 12:05 /etc/pki/tls/certs/ 
		-rw-------. 1 root root 1188 Sep 25 12:05 /etc/pki/tls/certs/server.crt.pem 
		drwxr-xr-x. 2 root root 4096 Sep 25 12:05 /etc/pki/tls/private/ 
		-rw-------. 1 root root  887 Sep 25 12:05 /etc/pki/tls/private/server.key.pem 

	5. (Re)start the httpd server:

	.. code-block:: shell

		# service httpd restart
		...
		Starting httpd:                                            [  OK  ] 

	If the server does not start, this may be because of a bad certificate, key or CA certificate file. In this case, check the appropriate logs in /var/log/httpd.

	6. Verify the validity of the certificates:

	.. code-block:: shell

		# openssl s_client -connect localhost:443
		...
		    Verify return code: 0 (ok) 
		---
		Ctrl-C or Ctrl-D to leave openssl client

	If there is a problem with the certificate you might get outputs like:

	.. code-block:: shell

		# openssl s_client -connect localhost:443
		...
		    Verify return code: 18 (self signed certificate) 
		---

	or

	.. code-block:: shell

		# openssl s_client -connect localhost:443
		...
		    Verify return code: 21 (unable to verify the first certificate) 
		---
	 
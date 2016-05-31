.. Copyright (c) 2007-2016 UShareSoft, All rights reserved

.. _custom-plugins:

Custom Plugins for Marketplace
===============================

The marketplace can be easily extended to interact and integrate with other products and services to expand the Marketplace solution.  This is done via an event bus service.  Whenever a POST, PUT or DELETE request to the Marketplace a corresponding event is sent to the event bus.  Custom plugins can be built to listen for these events and trigger custom business logic or call out to other 3rd party systems.

The event bus service is based on RabbitMQ.  Custom plugins are known as “consumers”.
Custom plugins (RabbitMQ consumers) can be written in many different languages including:

	* Java
	* Ruby
	* C
	* Python
	* Erlang
	* PHP
	* Node.js etc

RabbitMQ is a message broker.  In essence, it accepts messages from “producers” and delivers them to “consumers”.  In-between, it can route, buffer and persist messages, known as the “queue”.  

When a POST, PUT or DELETE request is sent to the web service, then the Marketplace creates a message (the producer) and posts this to a routing service, called an exchange.  This exchange is configured to publish messages to the Marketplace queue.  When writing a custom plugin (consumer), it registers itself to this queue.  

Administrators can also reconfigure the event bus routing service to adapt to more complex workflows.  This is done in the event bus administration UI and use the root account of the Marketplace service, at:

http://youripaddress:15672
Login: uss-admin
Password: marketplace administration password

Refer to the `RabbitMQ documentation <https://www.rabbitmq.com/documentation.html>`_ for more information.


Writing a Custom Plugin (Consumer)
----------------------------------

Prior to writing a custom plugin, it is important to understand the producer messages created by the marketplace.  When a request is sent to the web service (POST, PUT or DELETE) the web service creates a producer message.  The contents of each message is described in the .xsd file on the `UShareSoft documentation page <https://www.usharesoft.com/resources/docs/>`_.

When creating a plugin, you will have access to all the attributes in a message.  The plugin will contain the custom business logic required.

By default, this mechanism is used to send notification emails.  For examples, refer to the `RabbitMQ tutorials <https://www.rabbitmq.com/getstarted.html>`_.

Registering a Custom Plugin to Event Bus
----------------------------------------

To register a custom plugin, you require to provide:
The event bus URI, can be found in the marketplace configuration file: /etc/UShareSoft/marketplace/marketplace.conf
The name of the queue

This information can be found in the RabbitMQ administration console.  

	1. Login to the administration console:

		http://youripaddress:15672
		Login: uss-admin
		Password: marketplace administration password

	2. Go to the ``Queues`` Tab, you will see the available queues.  The default marketplace queue is vendors.


.. image:: /images/queues.jpg


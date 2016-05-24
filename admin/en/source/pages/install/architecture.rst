.. Copyright (c) 2007-2016 UShareSoft, All rights reserved

.. _mp-architecture:

Marketplace Architecture Considerations
=======================================

UForge Marketplace is a scalable multi-tenant platform, and is split into five distinct parts:

   1. Messaging Bus: Providing the ability to integrate UForge AppCenter to other services required by the customer (for example CRM, support systems and billing).  Custom plugins can be registered to events created by UForge AppCenter.
   2. Meta-data SQL Store:This is a database holding all the meta-data of the platform.
   3. Identity Management Service: LDAP and Role-based access control (RBAC) features.  All user information is stored here.
   4. Web Services: This holds all the business logic, handling all incoming user requests.
   5. Presentation Layer: User interface or client command-line tools


Messaging Bus Layer
-------------------

Providing a messaging bus within UForge Marketplace allows the customer the required means to integrate with other software services.  The message bus can trigger plugins from events created by the platform.  The administrator can create custom plugins and register them to specific UForge Marketplace events.

UForge Marketplace uses RabbitMQ for the messaging bus service.

Meta-data SQL Store
-------------------

UForge Marketplace requires an SQL database to store all the business logic meta-data.  By default, UForge Marketplace uses MySQL.  MariaDb can also be used.

Identity Management Layer
-------------------------

UForge Marketplace provides an Identity Management service by default allowing a very flexible way to enforce role-base access control and to store all the user information including passwords (encrypted).  By default, no other IDM services are activated, however, this can be extended to provide identity management with other customer services and user synchronization.  

The identity management service uses:

   * Syncope: is an Open Source system for managing digital identities in enterprise environments.  It runs as a web service.  Apache tomcat is used as the web container
   * OpenDJ: LDAP service where the user information is actually stored

Web Services Layer
------------------

The web service layer is a RESTful (Representational State Transfer) web service built on top of Java and using the JSR-311 reference implementation (project Jersey).  The web service attempts to conform to the design principles of REST and Resource Orientated Architecture (ROA).  Resources are references with a unique global identifier (URI).  The web service uses the semantics of the HTTP protocol to manipulate these resources.  The HTTP response codes are used to determine whether a user's request was treated successfully or not.

Information is returned to the client in either XML or JSON, depending upon the “Accept-Type” header attribute used by the client.  If no “Accept-Type” header is provided, XML is returned by default.
To ensure security, communication is done via HTTPS.

The web service interacts with the SQL Store using Hibernate.  Hibernate is a high-performance Object/Relational persistence and query service.  Hibernate takes care of the mapping from Java classes to database tables and from Java data types to SQL data types. It provides data query and retrieval facilities, providing a buffer between the two data representations and enables a more elegant use of object orientation on the Java side.

The web service is deployed inside a web server container.  By default, Apache Tomcat is used.

Presentation Layer
------------------

The presentation layer is seperate from the web services.  This allows customers to create their own tools and presentation layers using the RESTful interface proposed by the web service layer.  By default, UForge Marketplace provides an HTML5 User Interface (UI) based on Google Web Toolkit (GWT).  This user interface has a client-server architecture.  

The server-side code runs inside an Apache Tomcat web container.
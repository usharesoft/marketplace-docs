.. Copyright (c) 2007-2016 UShareSoft, All rights reserved

.. _fiql-search:

FIQL and Marketplace
--------------------

The Uforge Marketplace uses FIQL (Feed Item Query Language) for search queries of objects in the marketplace. This is a powerful way to search for objects on the UForge RESTful Webservice.

For complete documentation on FIQL commands, we recommend you look at:

	* Apache CXF: `http://cxf.apache.org/docs/jax-rs-search.html <http://cxf.apache.org/docs/jax-rs-search.html>`_
	* `FIQL: The Feed Item Query Language <https://tools.ietf.org/html/draft-nottingham-atompub-fiql-00#section-4>`_

Search Examples
~~~~~~~~~~~~~~~

The following are a few search examples to get you started.

Note that in all these example http://localhost:9090/ufws/ is the address of the UForge platform to which the Marketplace is linked.

To find all the users of the UForge Platform that work for the company UShareSoft::

	curl "http://localhost:9090/ufws/users?query=company.name==UShareSoft"

To find all the users that have a company website starting with "http"::

	curl http://localhost:9090/ufws/users/\?query\=company.website\=\=http\*

To find all the vendors with a user with login test is a member of that are of type corporate::

	curl "http://myforge.usharesoft.com/ufws/users/Bob/vendors?query=type==corporate"

To find Vendors in which all the members are active users::

	curl "http://myforge.usharesoft.com/ufws/users/test/vendors?query=members.user.active==true"

To find all the vendors that are part of Organization with id 1 and that have the token "shop" in the name::

	curl "http://localhost:9090/ufws/orgs/1/vendors?query=name==*shop*"


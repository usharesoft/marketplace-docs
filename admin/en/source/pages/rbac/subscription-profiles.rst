.. Copyright (c) 2007-2016 UShareSoft, All rights reserved

.. _subscription-profiles:

Managing Subscription Profiles
------------------------------

A subscription profile defines the roles, OSes, formats the user has access to, in addition to any quotas. Since a subscription code is required to create a user, the UForge administrator must:

	1. Create subscription profiles
	2. Add the organization administrator to the admin list.

To create a subscription profile you must be the UForge administrator.

The subscription command allows you to create, manage and delete user accounts in UForge. Each user command can have mandatory and optional arguments to complete the request.

The subscription target has the following commands:

	.. code-block:: shell

		========================================================================================================================
		SubscriptionProfileCmds help
		========================================================================================================================
		admin                    | Manage subscription profile admins                                                     
		create                   | Create a new subscription profile within an organization.Create a new                  
		delete                   | Delete a subscription profile from an organization.                                    
		help                     | List available commands with "help" or detailed help with "help cmd".                  
		info                     | Get detailed information on a subscription profile within an organization.             
		list                     | List all the subscription profiles for a given organization. If no                     
		role                     | Manage subscription profile roles                                                      
		update                   | Updates a new subscription profile 

		...removed options for clarity

Creating and Enabling Subscription Profiles
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To create a subscription profile you must be a subscription profile administrator. 

There are two steps to adding subscription profiles:

	1. creating the profile
	2. enabling the profile

By default, the subscription profiles you create are not active. You can activate the subscription profile when you create it by using the argument ``--active``. Otherwise, you will need to activate it using the command subscription enable.

You can add the list of administrators that will be allowed to create users by using the argument ``--admin``.  If you do not want to define the administrators that will create the users at the same time as you create the subscription profile, you can do so later. See :ref:`subscription-administrator`.

When creating a subscription profile, you can also specify the following:

	* formats
	* OS
	* quotas
	* roles

If you specify any of the above when you create a subscription profile, then all users created using this subscription profile will have the formats, OSes, quotas and roles defined in the subscription profile.

	.. note:: Once you create a user with a specific subscription profile, even if you modify the subscription profile, the rights of the users already created will not be modified. For example, if profileA used to create UserA has quotas set to unlimited. Once UserA is created, you modify the profileA to set quota to 3 generations. UserA will still have quota set to unlimited, but UserB created with the updated profileA will have quota set to 3 generations.

	1. To create a subscription profile for an organization, run the command::

		# marketplacecli> subscription create --code <string> --name <string> --org usharesoft -u $ADMIN -p $PASS

	The code can be any alpha-numeric string, excluding spaces and special characters.

	2. To enable a subscription profile for an organization, run the command::

		# marketplacecli> subscription enable --name <string> --org usharesoft -u $ADMIN -p $PASS


Adding Roles to a Subscription Profile
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can add new roles to an existing subscription profile::

	# marketplacecli> subscription role add --name <NAME> –-roles <roleA> 

All new users created with this subscription profile will have the added roles as part of their profile. However this does not modify the profile of users previously created with this profile.

Deleting Roles from a Subscription Profile
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can delete roles from an existing subscription profile::

	# marketplacecli> subscription role delete --name <NAME> –-roles <roleA> 

This does not delete the role from users that have been created with this subscription profile in the past. However, new users created with this subscription profile will have the updates list of roles.


.. _subscription-administrator:

Allowing Administrators to Create Users
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In order to create a user, the following are required:

	* The organization Administrator needs to be part of the list of subscription profile administrator. Only users that are part of this list can create user accounts
	* Subscription profile code. This code must be part of the request to create a user. Only the UForge administrator can create these codes.

When creating subscription profiles, the Marketplace administrator can add subscription profile administrators. However, they can also be added after the fact, as follows::

	# marketplacecli> subscription admin add --admin kermit --name profileA --org usharesoft -u $ADMIN -p $PASS

The argument admin is the login of the user you want to add as an administrator. This administrator will be able to create users with the subscription profile specified by the argument name.

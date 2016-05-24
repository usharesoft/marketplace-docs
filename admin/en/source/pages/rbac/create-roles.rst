.. Copyright (c) 2007-2016 UShareSoft, All rights reserved

.. _create-roles:

Creating and Updating User Roles
--------------------------------

If the pre-defined roles delivered with UForge do not match with the permissions you want to allow users, you can either create a new role or modify an existing one.

To create a new role in the default organization::

	# marketplacecli> role create --name newrole --description “description of new role” -u $ADMIN -p $PASS

By default, this role will be empty (containing no entitlements).  You can then add entitlements to a role by using the command::

	# marketplacecli> role entitlement add --name newrole --entitlements appliance_create studio_access -u $ADMIN -p $PASS

You can also remove an entitlement from a role by using the command::

	# marketplacecli> role entitlement remove --name newrole --entitlements studio_access -u $ADMIN -p $PASS

You can add entitlements as part of the creation by using the --entitlements option in the create command::

	# marketplacecli> role create --name newrole --description “description of new role” --entitlements appliance_create studio_access -u $ADMIN -p $PASS

.. note:: You cannot modify the “root” role.


Listing Roles Assigned to a User
--------------------------------

To view the roles already assigned to a specific user, run the command::

	# marketplacecli> user role list --account <username> -u $ADMIN -p $PASS


.. _add-roles:

Adding a Role to a User
-----------------------

.. note:: Adding a specific role to a user (such as Administrator) is often only the first step in granting specific  rights. You must then specify the entity (for an Administrator this would be the organization) for which the user has the newly assigned rights. See the examples later in this section.

To add a role to a user::

	# marketplacecli> user role add --account <username> --roles newrole -u $ADMIN -p $PASS

To add several roles to the same user::

	# marketplacecli> user role add --account <username> --roles role1 role2 -u $ADMIN -p $PASS

.. _delete-roles:

Deleting a Role from a User
---------------------------

To delete a role from a user::

	# marketplacecli> subscription role remove --name <NAME> –-roles <roleA>  -u $ADMIN -p $PASS

.. note:: If this is the only role assigned to a user, once deleted, the user will no longer have any roles. With no roles the user will only be able to view the UForge account and dashboard.

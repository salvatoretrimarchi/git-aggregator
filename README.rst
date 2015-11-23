.. image:: https://img.shields.io/badge/licence-LGPL--3-blue.svg
   :target: http://www.gnu.org/licenses/lgpl-3.0-standalone.html
   :alt: License: LGPL-3

==============
git-aggregator
==============

Manage the aggregation of git branches from different remotes to build a consolidated one.



Command line Usage:
===================

Create a ``repos.yaml`` file:

  .. code-block:: yaml

	./product_attribute:
	    remotes:
		oca: https://github.com/OCA/product-attribute.git
		acsone: git+ssh://git@github.com/acsone/product-attribute.git
	    merges:
		- oca 9d7da70c4e17e1c5b8e89049d758c0f70be9636c
		- oca refs/pull/105/head
		- oca refs/pull/106/head
	    target: acsone aggregated_branch_name

	./connector-interfaces:
	    remotes:
		oca:  https://github.com/OCA/connector-interfaces.git
		acsone:  https://github.com/acsone/connector-interfaces.git
	    merges:
		- oca 6054de2c4e669f85cec380da90d746061967dc83
		- acsone 8.0-connector_flow
		- acsone 80_connector_flow_ir_cron_able-lmi
		- acsone 8.0_connector_flow_improve_eval_config
	    target: acsone aggregated_branch_name

Aggregate you repositories at any time:

  .. code-block:: bash

    $ gitaggregate -c repos.yaml

You can also aggregate and automatically push the result to the target:

  .. code-block:: bash

    $ gitaggregate -c repos.yaml -p

Only aggregate a specific repository using `fnmatch`_:

  .. code-block:: bash

    $ gitaggregate -c repos.yaml -p -d connector-interfaces

.. _fnmatch: https://docs.python.org/2/library/fnmatch.html

Credits
=======

Author:

  * Laurent Mignon (ACSONE)
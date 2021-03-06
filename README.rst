Amun Client
-----------

Autogenerated library for communication with
`Amun API <https://github.com/thoth-station/amun-api>`_

The swagger definition that is used for generating this swagger client can be
found in Amun API repository in file
`amun-api/openapi/openapi.yaml <https://github.com/thoth-station/amun-api/blob/master/openapi/openapi.yaml>`_.

Installation
============

This library is automatically released on changes to PyPI, so you can install
it using pip or Pipenv (recommended):

.. code-block:: console

  pipenv install amun
  # or use pip
  # pip3 install amun

Usage
=====

You can find autogenerated documentation in the 
`Amun client <https://github.com/thoth-station/amun-client>`_ repository,
under the
`Documentation directory <https://github.com/thoth-station/amun-client/tree/master/Documentation>`_.

To adjust client for a desired remote, you can use the following configuration chages:

.. code-block:: python

  from amun.swagger_client import InspectionApi
  from amun.swagger_client import InspectionSpecification
  from amun.swagger_client import Configuration
  from amun.swagger_client import ApiClient
  from pprint import pprint

  # Adjust remote to communicate with:
  configuration = Configuration()
  configuration.host = 'http://amun-api.your-cluster.redhat.com/api/v1'

  # Apply this configuration to API client:
  api_client = ApiClient(configuration)

  # Use the customized API client to talk to the remote API:
  api_instance = InspectionApi(api_client)
  specification = InspectionSpecification(base='fedora:28')
  
  api_response = api_instance.post_inspection(specification)
  pprint(api_response)

Or you can use the prepared wrapper for this purpose:

.. code-block:: python

  from amun import inspect

  inspect('http://amun-api.your-cluster.redhat.com/api/v1', base='fedora:28')

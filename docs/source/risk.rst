====
Risk
====

.. autosummary::
   :toctree: generated

.. warning::

   Any source code provided on this site is unaudited and provides no guarantee that it will be functional or safe to use. Ensure you
   test before deploying to mainnet or production use.

----------------
signata-risk-api
----------------

Deployment
^^^^^^^^^^

The Risk API is a python flask service using `Supabase <supabase.com>`_ for record retrieval and storage. It can be easily deployed on services like `DigitalOcean <https://m.do.co/c/7802e11be119>`_ with the following environment variables set:

``SUPABASE_URL``

``SUPABASE_KEY``

The Congruent Labs Risk API service is hosted at ``https://risk.signata.net/``

Get Risk Level
^^^^^^^^^^^^^^

Request:

``GET /api/v1/riskLevel/{addr}``

Response:

Just responding with single values in the body for consumption by oracles.

``0 - unknown risk level``

``1...5 - risk levels``

Errors:

``400 - Invalid Address``


Add Risk Event
^^^^^^^^^^^^^^

Request:

``POST /api/v1/riskEvent``

.. code-block:: json
    {
        "address": string, # the address of the identity to add
        "device_thumbprint": string, # deterministic thumbprint of the requestor's device thumbprint
        "geolocation_thumbprint": string, # deterministic thumbprint of the requestor's geolocation country
        "access_type": string, # type of the access event, e.g. "standard" or "privileged"
        "reported_by": string # the name of the reporting service, e.g. "signata-idp"
    }

Response:

``200 OK``

Errors:

``400 - Invalid Address``


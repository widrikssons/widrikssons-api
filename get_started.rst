Get Started
============


==============
Authorization
==============

The Widrikssons Last Mile REST API uses basic Auth as authentication.

To use the api Widrikssons will provide customers with a ApiKey and secret token, wich you will pass as a Authorization
header using Basic Auth.

base64 encode your apikey and token, using apikey as user and token ass password

{apikey}:{token}

**Example request**:

.. sourcecode:: http

      GET /oauth/token HTTP/1.1
      Host: example.com
      Content-Type: application/x-www-form-urlencoded
      Authorization: Basic 6gd2aikgd2kad=

.. note::

   Refresh token example will be added

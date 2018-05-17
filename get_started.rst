Get Started
============


==============
Authorization
==============

The Widrikssons Last Mile REST API uses the OAuth 2.0 protocol to authorize calls.

To use the api WIdrikssons will provide customers with a set of OAuth client ID and secret credentials. You pass these credentials in the Authorization header in a get access token request.

In exchange for these credentials, the authorization server issues access tokens called bearer tokens that you use for authorization when you make REST API requests.

Re-use the access token until it expires. When it expires, you can get a new token.

.. http:post:: /oauth/token

Post the client id and secret with grant_type client_credentials to get an accesstoken

   **Example request**:

   .. sourcecode:: http
      
      GET /oauth/token HTTP/1.1
      Host: example.com
      Content-Type: application/x-www-form-urlencoded

      grant_type=client_credentials
      &client_id=xxxxxxxxxx
      &client_secret=xxxxxxxxxx

   +------------------------+-----------------------------------------------------------+-----------------------+
   | grant_type             | client_credentials                                        | string                |
   +------------------------+-----------------------------------------------------------+-----------------------+
   | client_id              | The client_id received from widrikssons.                  | string                |
   +------------------------+-----------------------------------------------------------+-----------------------+
   | client_secret          | The client_secret received from widrikssons.              | string                |
   +------------------------+-----------------------------------------------------------+-----------------------+

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: application/json

      {
       "access_token": "Access-Token",
       "token_type": "Bearer",
       "expires_in": 3900,
       "refresh_token": "hg23h4g23hg4h32hg4h32="
      }

   +------------------------+--------------------------------------------------------------+--------------------+
   | access_token           | The access token to be included on all requests              | string             |
   +------------------------+--------------------------------------------------------------+--------------------+
   | token_type             | bearer                                                       | string             |
   +------------------------+--------------------------------------------------------------+--------------------+
   | expires_in             | The client_secret received from widrikssons.                 | string             |
   +------------------------+--------------------------------------------------------------+--------------------+
   | refresh_token          | Refresh token can be used to get new access token            | string             |
   +------------------------+--------------------------------------------------------------+--------------------+

With a valid access token, you can make REST API calls, just include the access_token in the Authorization header with bearer token type.

   **Example Request**:

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: application/json
      Authorization: bearer 6agfd7adgf7gf32fkljh3kjlf==

      {
       "access_token": "Access-Token",
       "token_type": "Bearer",
       "expires_in": 3900,
       "refresh_token": "hg23h4g23hg4h32hg4h32="
      }

.. note::

   Refresh token example will be added

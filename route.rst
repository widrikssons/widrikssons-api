Route
======

======================
Get Routes
======================

Following resource can be used to get routing schedule for the day.

.. http:get:: /v1/routes

Returns all routes and orders for the specific day.

**Example request**:

.. tabs::

   .. code-tab:: http

      GET /v1/routes HTTP/1.1
      Host: example.com
      Content-Type: application/json
      Authorization: bearer 6agfd7adgf7gf32fkljh3kjlf==

   .. tab:: CURL

      curl -X GET \
      https://example.com \
      -H 'Authorization: bearer askdj8auds8jaodsa==' \
      -H 'Cache-Control: no-cache' \

**Parameters:**

.. csv-table::
   :widths: 15, 10, 30

   "**date** *optional*", "string", "Filter for a specific date ('yyyy-MM-dd') default is today."

**Example response**:

.. sourcecode:: http

   HTTP/1.1 200 OK
   Content-Type: application/json

.. sourcecode:: json

   [
     {
       "routeId": "23hg4j23-23d23d2-d3232-d32d2",
       "routenumber": "K12",
       "routeDate": "2018-05-20",
       "status": "inprogress",
       "assignedDriver": {
         "name": "Doe John"
       },
       "deliveries": [
         {
           "orderId": "2323df23-23d23d2-d3232-d3234",
           "externalId": "1234ewq",
           "estimatedDeliveryTime": "2018-05-15T13:13:00z"
         },
         {
           "orderId": "2323df23-23d23d2-d3232-d3234",
           "externalId": "44433",
           "estimatedDeliveryTime": "2018-05-15T15:13:00z"
         }
       ]
     },
     {
       "routeId": "23hg4j22-23d23d2-d3232-d32d2",
       "routenumber": "K33",
       "routeDate": "2018-05-20",
       "status": "inprogress",
       "assignedDriver": null,
       "deliveries": {
         "orderId": "2323df23-23d23d2-d3232-d3234",
         "externalId": "1234ewq",
         "estimatedDeliveryTime": "2018-05-15T13:13:00z"
       }
     }
   ]


======================
Get Delivery
======================

.. http:get:: /v1/routes/{routeId}/deliveries/{deliveryId}

To get status of an order, Make a GET request to following resource.

**Example request**:

.. sourcecode:: http

   GET v1/orders/O234422 HTTP/1.1
   Host: example.com
   Content-Type: application/json
   Authorization: bearer 6agfd7adgf7gf32fkljh3kjlf==

**Example response**:

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

.. sourcecode:: json

    {
      "orderId": "23hg4j23-23d23d2-d3232-d32d2",
      "externalId": "123asd",
      "delivery": {
        "name": "John Doe",
        "phoneNumber": "+46XXXXXX",
        "comment": "Door code is 4534",
        "address": "Street 1",
        "address2": "",
        "postalCode": "14567",
        "city": "Stockholm",
        "selectedDate": "2018-05-20",
        "timeWindow": {
          "start": "14:00",
          "end": "18:00"
        }
      },
      "parcelWeight": 15,
      "parcelVolume": 200,
      "parcelCount": 2,
      "orderValueIncVat": 15900,
      "status": "delivered",
      "deliveredAt": "2018-05-21T14:13:00z",
      "routeId": "O15",
      "assignedDriver": {
        "name": "Doe John",
        "comment": "Left beside the door, customer not home"
      }
    }


**Route:**

.. csv-table::
   :widths: 15, 10, 30

   "**routeId**", "string", "Assigned route number"
   "**routeDate**", "string", "Route date"
   "**status**", "string", "Route status"
   "**assignedDriver** *null*", "AssignedDriver", "The assigned driver if started"
   "**deliveries**", "Delivery *array*", "List of scheduled deliveries for the route"

**Delivery:**

.. csv-table::
   :widths: 15, 10, 30

   "**orderId**", "string", "Assigned route number"
   "**externalId**", "string", "Route date"
   "**estimatedDeliveryTime**", "string", "Estimated time of delivery in UTC"

**AssignedDriver:**

.. csv-table::
   :widths: 20, 15, 60

   "**name**", "string", "Assigned drivers name"

.. note::

   This is example of response data. more data will be avaliable in the final version

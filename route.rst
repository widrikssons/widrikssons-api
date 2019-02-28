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
       "id": "23hg4j23-23d23d2-d3232-d32d2",
       "routenumber": "K12",
       "routeDate": "2018-05-20",
       "status": "inprogress",
       "deliveries": [
         {
           "id": "2323df23-23d23d2-d3232-d3234",
           "orderNumber": "1234ewq",
           "status": "pending",
           "estimatedDeliveryTime": "2018-05-15T13:13:00z",
           "trackingId": "KL825K"
         },
         {
           "id": "239e9718-8a8b-4443-a4dc-9c30c",
           "orderNumber": "1543qwf",
           "status": "pending",
           "estimatedDeliveryTime": "2018-05-12T15:10:00z",
           "trackingId": "KN8315"
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

To get status of an delivery, Make a GET request to following resource.

**Example request**:

.. sourcecode:: http

   GET v1/deliveries/O234422 HTTP/1.1
   Host: example.com
   Content-Type: application/json
   Authorization: bearer 6agfd7adgf7gf32fkljh3kjlf==

**Example response**:

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

.. sourcecode:: json

 {
    "id": "23hg4j23-23d23d2-d3232-d32d2",
    "orderNumber": "O234422",
    "status": "pending",
    "consumer": {
        "name": "John Doe",
        "phoneNumber": "+46XXXXXX",
        "comment": "Door code is 4534",
        "adress": "Street 1",
        "postalCode": "14567",
        "city": "Stockholm",
        "longitude": 20.023125,
        "latitude": 60.729582
    },
    "routeNumber": "F 01",
    "selectedDate": "2019-02-20",
    "timeWindow": {
        "start": "06:00",
        "end": "08:00"
    },
    "trackingId": "GT2010G"
}
**Route:**

.. csv-table::
   :widths: 15, 10, 30

   "**id**", "string", "Internal route id"
   "**routeNumber**", "string", "Assigned route number"
   "**routeDate**", "string", "Route date"
   "**status**", "string", "Route status, 'available, assigned, loading, started, completed, canceled'"
   "**deliveries**", "Delivery *array*", "List of scheduled deliveries for the route"

**Delivery:**

.. csv-table::
   :widths: 15, 10, 30

   "**id**", "string", "Internal delivery id"
   "**orderNumber**", "string", "Assigned ordernumber"
   "**status**", "string", "Delivery status, 'pending, delivered, notDelivered, issue, inprogress, unplanned, loaded'"
   "**consumer**", "consumer *object*", "Consumer object for the delivery"
   "**routeNumber**", "string", "Assigned routeNumber"
   "**selectedDate**", "string", "Delivery date"
   "**estimatedDeliveryTime**", "string", "Estimated time of delivery in UTC"
   "**timeWindow**", "Time window *object*", "Time window for the delivery"
   "**trackingId**", "string", "Id to track the specified delivery"

**TimeWindow:**

.. csv-table::
   :widths: 20, 15, 60

   "**start**", "string", "Timespan in UTC"
   "**end**", "string", "Timespan in UTC"

.. note::

   This is example of response data. more data will be avaliable in the final version

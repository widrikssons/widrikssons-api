Order
==========

======================
Get Order
======================

.. http:get:: /v1/orders/{orderId}

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

**Object**

.. csv-table::
   :header: "Prop", "Type", "Description"
   :widths: 15, 10, 30

   "externalId", "string", "External order id (Typically your order id) * must be unique"
   "delivery", "object", ""
   "delivery.name", "string", "Name of the recipient"
   "delivery.phoneNumber", "string", "Phonenumber"
   "delivery.comment", "string", "Customer comment"
   "delivery.address", "string", "Address"
   "delivery.address2", "string", "Additional address information"
   "delivery.postalCode", "string", "postalCode"
   "delivery.city", "string", "City of the delivery"
   "delivery.date", "string", "date of the delivery"
   "delivery.timeWindow", "object", ""
   "delivery.timeWindow.start", "string", "Preferred from time (14:00)"
   "delivery.timeWindow.end", "string", "Preferred to time (18:00)"
   "orderWeight", "int", "Order weight in grams"
   "orderVolume", "int", "order volume in cubic cm"
   "percelCount", "int", "number of percels"
   "orderValueInkVat", "int", "Order value including VAT in cents (560kr = 56000)"
   "status", "string", "Status of the order"
   "deliveredAt", "string", "Datetime in UTC when the order was delivered"
   "routeId", "string", "Routeid the order was assigned to"
   "assignedDriver", "object", ""
   "assignedDriver.name", "string", "name of the assigned driver"
   "assignedDriver.comment", "string", "Comment from the driver"


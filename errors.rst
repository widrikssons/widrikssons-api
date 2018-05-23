Errors
=======

==============
Status Codes
==============

Following status codes you should handle in you implementation


.. csv-table::
   :widths: 15, 10, 30

   "**200**", "OK", "Request succeeded"
   "**201**", "Created", "Resource is created, check Location header for link"
   "**400**", "BadRequest", "Request could not be executed, check error message for reason"
   "**401**", "UnAuthorized", "You are not authorized to perform this request"
   "**403**", "Forbidden", "You dont have the required permissions to access this resource"
   "**404**", "Not Found", "The resource you are requesting does not exist"
   "**429**", "To Many Requests", "There is to many requests in a short period of time, wait and try again"
   "**500**", "Internal Server Error", "There is somthing wrong with the backend, please try again"
   

=============
Errors
=============

Following format will be used on all 400 errors,


**Example error response**:

   .. sourcecode:: http
      
      HTTP/1.1 400 BadRequest
      Content-Type: application/json

      {
          "errorMessage": "All fields must be valid.",
          "code": "352",
          "invalidProperties": [
              {
                  "name": "postalCode",
                  "message": "Invalid postalCode, use XXXXX format."
              }
          ]
      }

   +--------------------------+----------------------------------------------------------------+-----------------------+
   | errorMessage             | Developer error message                                        | string                |
   +--------------------------+----------------------------------------------------------------+-----------------------+
   | code                     | Custom code describing the error                               | string                |
   +--------------------------+----------------------------------------------------------------+-----------------------+
   | invalidProperties        | List of invalid properties if any                              | string                |
   +--------------------------+----------------------------------------------------------------+-----------------------+
   | invalidProperties.name   | Name of the propertie                                          | string                |
   +--------------------------+----------------------------------------------------------------+-----------------------+
   | invalidProperties.message| Short message describing the error                             | string                |
   +--------------------------+----------------------------------------------------------------+-----------------------+
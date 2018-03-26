=============
Errors
=============

Following format will be used on all errors,


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
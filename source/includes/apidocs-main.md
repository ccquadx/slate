Hello and welcome to X for Developers! Here you'll find everything that you need to integrate with us and book your orders. We provide APIs for order creation, status management, and visibility of the whole order lifecycle until fulfillment.

# What We Will Be Providing #
---

### Slack Channel & Support ###
A Slack Channel will be provided as our medium of communication.
Inquiries, concerns, and other discussions related to this document and the processes it involves may be raised in the given channel, such as error-handling, process flow clarifications, etc.

### <a name="keys"></a>Keys ###
We will be providing you with a pair of API and Secret keys once you sign up for our services. The API key should be passed as the subject (sub) attribute of the JWT payload while the secret key is used to create the token signature. Never share your secret key and make sure that it would not be exposed at any time.

<p style="text-align:center;"><img src="https://www.quadx.xyz/wp-content/themes/quad-x/assets/img/footergreen.png"/></p>

# Authorization #
---

Some of the resources defined in this document are secured using [JSON Web Tokens (JWT)](https://jwt.io/). JWT is an [industry standard](https://tools.ietf.org/html/rfc7519) for authorization and exchanging claims between two parties.

Basic JSON Web Tokens are made up of three parts separated by dots, which are:
- Header
- Payload
- Signature

In turn, a JWT ends up looking like the following:
```
aaaaa.bbbbb.ccccc
```
The following subsections briefly explain these three parts.

### Header ###

The header is the first part of the token where the token type (typ) and hashing algorithm (alg) used to generate the signature are defined. Only `HMAC SHA256` is supported at the moment.

###### JSON Header ######
```json
{
"alg": "HS256",
"typ": "JWT"
}
```

This header is then encoded using `Base64Url`.

The following result is normally the header when dealing with our API:


###### Base64 Encoded Header (URL-safe) ######
```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9
```

### Payload ###
The payload is the second part of the token where the claims are defined. The following claims should always be present on the payload:
- __iat__ - Unix timestamp of when the token was created
- __jti__ - unique nonce value. Requests with a repeated jti value will be rejected.
- __sub__ - [your API key](#Keys)

###### JSON Payload ######
```json
{
"iat": 1463702400,
"jti": "abe953c8-3621-414b-99e9-a01d9461b129",
"sub": "2af9713592"
}
```

Like the header, this is then encoded using `Base64Url`.

###### Sample Generated Base64 Encoded Payload (URL-safe) ######
```
eyJpYXQiOjE0NjM3MDI0MDAsImp0aSI6ImFiZTk1M2M4LTM2MjEtNDE0Yi05OWU5LWEwMWQ5NDYxYjEyOSIsInN1YiI6IjJhZjk3MTM1OTIifQ
```

### Signature ###
The last part to be generated is the signature.
To generate this, concatenate the base64 encoded header and payload with a dot and generate the hash using HMAC SHA256.

###### For clarity, the process is as follows: ######
```js
signature = base64EncodeURL( hmac_sha256( base64EncodeURL(header) + '.' + base64EncodeURL(payload), SECRET_KEY ) )
```

###### For the purpose of comparison and checking, the produced signature for our previous header and payload examples is: ######
```
// when SECRET_KEY = 'itsasecret'
AXXvB0EgZWWTBQZsImnq_M6bHsEbw7H8k7tU_cYZz98
```

### Resulting JWT ###

The token is then built by concatenating dots in between the produced header, payload, and signature.

It should appear as follows:
```
(header).(payload).(signature)
```

###### Substituting the header, payload, and signature placeholders with their actual values, we finally have our JWT: ######
```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpYXQiOjE0NjM3MDI0MDAsImp0aSI6ImFiZTk1M2M4LTM2MjEtNDE0Yi05OWU5LWEwMWQ5NDYxYjEyOSIsInN1YiI6IjJhZjk3MTM1OTIifQ.AXXvB0EgZWWTBQZsImnq_M6bHsEbw7H8k7tU_cYZz98
```

### Sending the JWT ###

The token should be sent as a part of your HTTP Request Header.

###### Use the Authorization Bearer schema, as seen below: ######
```http
Authorization: Bearer {token}
```

######  Sample Header, using the JWT we generated in the previous example: ######
```http
POST /v1/orders HTTP/1.1
Host: api.lbcx.ph
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpYXQiOjE0NjM3MDI0MDAsImp0aSI6ImFiZTk1M2M4LTM2MjEtNDE0Yi05OWU5LWEwMWQ5NDYxYjEyOSIsInN1YiI6IjJhZjk3MTM1OTIifQ.3ZbAieutFTwQ0RXidGRCDO_hkSqZNydNz3fcwj3WAbA
```

### Additional Information ###
For more clarity on the subject of JWT, you can read the [Official JWT documentation](https://jwt.io/introduction/) to get a better idea regarding the token-generating process. You can also download their [3rd party libraries and SDKs](https://jwt.io/#libraries) to use in your APIs.



# Responses (Success, Errors) #
---
Standard HTTP status codes are returned on every response. `200` means that the request was successful, `4xx` indicates failure, and `500` means that something went wrong on our side. The error message and details are sent back as a JSON-encoded string in the response body. Here's a list of status codes that F3 uses:

<table>
  <tr>
    <th><b>Status</b></th>
    <th><b>Message</b></th>
    <th><b>Description</b></th>
  </tr>
  <tr>
    <td>200</td>
    <td>OK</td>
    <td>Success</td>
  </tr>
  <tr>
    <td>400</td>
    <td>Bad Request</td>
    <td>We didn't understand your request. Please make sure that you're sending a valid JSON payload in the request body.</td>
  </tr>
  <tr>
    <td>401</td>
    <td>Unauthorized</td>
    <td>The token is not valid or may have already expired. It could also be that you don't have sufficient privileges to access the resource.</td>
  </tr>
  <tr>
    <td>404</td>
    <td>Not Found</td>
    <td>The entity that you're looking for does not exist.</td>
  </tr>
  <tr>
    <td>413</td>
    <td>Request Entity Too Large</td>
    <td>You have exceeded the maximum allowable upload size of 1MB.</td>
  </tr>
  <tr>
    <td>422</td>
    <td>Unprocessable Entity</td>
    <td>Some of the parameters failed validation.</td>
  </tr>
  <tr>
    <td>429</td>
    <td>Too Many Requests</td>
    <td>Your account has been temporarily suspended because you have exceeded the allowable number of requests.</td>
  </tr>
  <tr>
    <td>500</td>
    <td>Internal Server Error</td>
    <td>Something went wrong. We're looking into it.</td>
  </tr>
</table>

###### Sample Successful Response #######
```http
    HTTP/1.1 200 OK
    Content-Type: application/json
```
```json
  {
    "id": 21,
    "currency": "PHP",
    "reference_id": "7336180193817RYKP",
    "tracking_number": "0000-0021-ZTMR",
    "payment_method": "cod",
    "status": "pending",
    "email": "johndoe@email.com",
    "contact_number": "+639172274819",
    "total": "3103.25",
    "paid": 0,
    "metadata": {
    "key_1": "value_1",
    "key_2": "value_2"
    },
    "preferred_pickup_time": "morning",
    "preferred_delivery_time": "3pm - 5pm",
    "pickup_address": {
    "name": "John Doe",
    "phone_number": "5713429",
    "mobile_number": "+639197421753",
    "line_1": "8F U825 Building A",
    "line_2": "711 Nulla St.",
    "city": "Makati",
    "state": "NCR",
    "postal_code": "1200",
    "remarks": "Optional notes / remarks go here."
    },
    "delivery_address": {
    "name": "Jane Doe",
    "phone_number": "6358972",
    "mobile_number": "+63907117421",
    "line_1": "3F U311 Bldg. C",
    "line_2": "Jade St.",
    "city": "Taguig",
    "state": "NCR",
    "postal_code": "1600",
    "remarks": "Optional notes / remarks go here."
    },
    "charge": {
    "status": "pending",
    "payment_method": "cod",
    "total_amount": 3103.25,
    "tendered_amount": 0,
    "change_amount": 0,
    "remarks": null
    },
    "items": [
      {
        "type": "product",
        "description": "Red Shirt",
        "amount": "1250.00",
        "quantity": 1,
        "metadata": {
          "size": "medium",
          "color": "red"
        }
      },
      {
        "type": "product",
        "description": "Blue Shirt",
        "amount": "700.00",
        "quantity": 2,
        "metadata": {
          "size": "medium",
          "color": "blue"
        }
      },
      {
        "type": "tax",
        "description": "Tax",
        "amount": "132.50",
        "quantity": 1,
        "metadata": null
      },
      {
        "type": "shipping",
        "description": "Expedited Shipping",
        "amount": "250.00",
        "quantity": 1,
        "metadata": null
      },
      {
        "type": "fee",
        "description": "Handling Fee",
        "amount": "20.00",
        "quantity": 1,
        "metadata": null
      },
      {
        "type": "fee",
        "description": "Gift Wrapping Fee",
        "amount": "50.75",
        "quantity": 1,
        "metadata": null
      }
    ]
  }
```

###### Sample Error Response (422) ######
```http
    HTTP/1.1 422 Unprocessable Entity
    Content-Type: application/json
```
```json
  {
    "status": 422,
    "message": "Unprocessable Entity",
    "description": "The given data failed to pass validation.",
    "parameters": {
      "payment_method": [
        "The selected payment method is invalid."
      ]
    }
  }
```

# Pagination #
---
All API resources that return lists or bulk data support pagination and share the same parameters.
All of these parameters are optional and have default values.
Pagination data is returned on both the header and response body for convenience.

<table>
  <tr>
    <th><b>Name</b></th>
    <th><b>Type</b></th>
    <th><b>Description</b></th>
    <th><b>Required?</b></th>
    <th><b>Default Value</b></th>
  </tr>
  <tr>
    <td>page</td>
    <td>integer</td>
    <td>Page Number</td>
    <td>optional</td>
    <td>1</td>
  </tr>
  <tr>
    <td>per_page</td>
    <td>integer</td>
    <td>Count per Page</td>
    <td>optional</td>
    <td>25</td>
  </tr>
</table>


###### Sample Response with Pagination ######
```http
    HTTP/1.1 200 OK
    Content-Type: application/json
    Link: <https://api.lbcx.ph/v1/orders?page=2>; rel="next"
    X-Pagination-Current-Page: 1
    X-Pagination-Page-Count: 8
    X-Pagination-Per-Page: 25
    X-Pagination-Total-Count: 192
    X-Powered-By: PHP/5.6.2
```
```json
  {
    "total": 192,
    "per_page": 25,
    "current_page": 1,
    "last_page": 8,
    "next_page_url": "https://api.lbcx.ph/v1/orders?page=2",
    "prev_page_url": null,
    "from": 1,
    "to": 25,
    "data": [
      {
        "id": 1,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0001-BSWF",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 2,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0002-SRFT",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 3,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0003-QMVL",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 4,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0004-VLSN",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 5,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0005-NQYS",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 6,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0006-ACZM",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 7,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0007-MAGY",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 8,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0008-KQNS",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 9,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0009-VDYH",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 10,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0010-JQXZ",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 11,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0011-ATHR",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 12,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0012-WCFM",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 13,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0013-ERTC",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 14,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0014-VLKU",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 15,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0015-TRXY",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 16,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0016-VHLD",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 17,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0017-WXHS",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 18,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0018-EKSQ",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 19,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0019-SYCA",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 20,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0020-WZGL",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 28,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0028-TWMB",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 21,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0021-ZTMR",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 22,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0022-RSBY",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 23,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0023-NDEH",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      },
      {
        "id": 24,
        "currency": "PHP",
        "reference_id": "7336180193817RYKP",
        "tracking_number": "0000-0024-PXYM",
        "payment_method": "cod",
        "status": "pending",
        "email": "johndoe@email.com",
        "contact_number": "+639172274819",
        "total": "3103.25",
        "paid": 0,
        "metadata": {
          "key_1": "value_1",
          "key_2": "value_2"
        },
        "preferred_pickup_time": "morning",
        "preferred_delivery_time": "3pm - 5pm"
      }
    ]
  }
```

# Webhooks #
---
A webhook is an HTTP callback that you define to process incoming events or status updates from our API.
We currently support both __HTTP__ and __HTTPS__ URLs but we advise you to use HTTPS as much as possible to ensure security. An alternate security measure you can do is to append a token to the URL in order to make it “unguessable” to the public.
We only send JSON data to your webhook URL via HTTP POST and expect a __200 HTTP status code__ in the response. Anything other than a 200 status code will be treated as failure and the request will be retried at a later time.
There is currently no user interface for setting the webhook URL so please send us an email or message us on your designated slack channel if you need to have it changed.

## Format ##

Every JSON payload sent to your webhook will have the following attributes:

<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
    <th>Required?</th>
    <th>Default Value</th>
  </tr>
  <tr>
    <td>`event`</td>
    <td>string</td>
    <td>type of event</td>
    <td>yes</td>
    <td>`status_update`</td>
  </tr>
  <tr>
    <td>`timestamp`</td>
    <td>integer</td>
    <td>Date and time in unix time when the data was sent to the webhook.</td>
    <td>yes</td>
    <td>N/A</td>
  </tr>
  <tr>
    <td>`data`</td>
    <td>json array</td>
    <td>Array of events; historical data.</td>
    <td>yes</td>
    <td>N/A</td>
  </tr>
</table>

###### Sample Payload ######

  ```http
    POST /your/webhook HTTP/1.1
    Content-Type: application/json
  ```
  ```json
  {
    "event": "status_update",
    "timestamp": 1512551041,
    "data": [{
        "event_id": 35862967,
        "tracking_number": "0495-0754-VZXJ",
        "reference_id": "17120514285DPEK.42ecdce0-d185-4356-a30f-d33ea14cff05",
        "created_at": "2017-12-06 16:41:31.898782+08",
        "status_updated_at": "2017-12-06 16:41:21+08",
        "status": "picked_up",
        "remarks": "Package successfully picked up",
        "fees": {
          "shipping_fee": 100,
          "insurance_fee": 9,
          "transaction_fee": 27
        },
        "party": {
          "id": 6,
          "external_id": null
        },
        "parent": {
          "id": null,
          "tracking_number": null,
          "reference_id": null
        }
      },
      {
        "event_id": 35862969,
        "tracking_number": "0476-8835-FHUL",
        "reference_id": "17120110305AQXW.db11da3c-15f9-4a79-a605-2aa59600790f",
        "created_at": "2017-12-06 16:41:31.939001+08",
        "status_updated_at": "2017-12-06 16:04:06+08",
        "status": "in_transit",
        "remarks": "FORWARDED TO PUERTO PRINCESA DELIVERY HUB",
        "fees": {
          "shipping_fee": 100,
          "insurance_fee": 5,
          "transaction_fee": 20
        },
        "party": {
          "id": 6,
          "external_id": null
        },
        "parent": {
          "id": null,
          "tracking_number": null,
          "reference_id": null
        }
      },
      {
        "event_id": 35862972,
        "tracking_number": "0479-8119-CWAX",
        "reference_id": "17120109493993N.88b7c455-cf29-404c-a91f-a398278ad1fd",
        "created_at": "2017-12-06 16:41:32.475252+08",
        "status_updated_at": "2017-12-06 16:20:19+08",
        "status": "in_transit",
        "remarks": "RECEIVED AT SOUTH LUZON AREA",
        "fees": {
          "shipping_fee": 100,
          "insurance_fee": 6.1,
          "transaction_fee": 20
        },
        "party": {
          "id": 6,
          "external_id": null
        },
        "parent": {
          "id": null,
          "tracking_number": null,
          "reference_id": null
        }
      },
      {
        "event_id": 35862977,
        "tracking_number": "0481-9668-HAJN",
        "reference_id": "17120113387HYRH.3623ee76-ee52-44a0-b890-f2bdc661078e",
        "created_at": "2017-12-06 16:41:33.064148+08",
        "status_updated_at": "2017-12-06 16:37:43+08",
        "status": "in_transit",
        "remarks": "RECEIVED AT SOUTH LUZON AREA",
        "fees": {
          "shipping_fee": 100,
          "insurance_fee": 5.52,
          "transaction_fee": 20
        },
        "party": {
          "id": 6,
          "external_id": null
        },
        "parent": {
          "id": null,
          "tracking_number": null,
          "reference_id": null
        }
      },
      {
        "event_id": 35862981,
        "tracking_number": "0492-6744-JFQD",
        "reference_id": "17120411264R1YD.8b95ac0c-4466-4053-bd03-ce1c9723b8fc",
        "created_at": "2017-12-06 16:41:33.193278+08",
        "status_updated_at": "2017-12-06 16:41:22+08"
      }
    ]
  }
  ```

## Retries ##
Our system has a retry protocol whenever we get an error response from the client (i.e. a non-200 HTTP status code).
Our retry phases are as follows:
1. Retry the failed message every 5 minutes for a maximum of 5 times.
2. If the status update still fails after the 5th retry, its contents go to our dead letter queue (DLQ) for manual investigation.
3. We (QuadX) report the failure to the client.

<p style="text-align:center;"><img src="https://www.quadx.xyz/wp-content/themes/quad-x/assets/img/footergreen.png"/></p>

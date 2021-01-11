# Orders
The following endpoints return information regarding Orders.
This API is the core of all order-related processes, from order creation, to getting orders and their statuses.

## <span class="http-post">POST</span> Create Orders

<div class="center-column"></div>
```
{{base_url}}/orders
```

### Request Headers ###

<b> Authorization: </b> `{{authorization}}`


> Example Request


```shell
curl --location --request POST '{{base_url}}/orders' \
--header 'Content-Type: application/json' \
--header 'Authorization: {{authorization}}' \
--data-raw '{
  "currency": "PHP",
  "total": "3153.25",
  "payment_method": "cod",
  "status": "for_pickup",
  "payment_provider": "lbcx",
  "shipment": "big-pouch",
  "buyer_name": "Test buyer",
  "buyer_id": "12345",
  "metadata": {"key_1":"value_1","key_2":"value_2"},
  "delivery_address": {
    "name": "Test buyer",
    "company": "Maxis",
    "phone_number": "6358972",
    "mobile_number": "+63907117421",
    "line_1": "3F U311 Bldg. C",
    "line_2": "Jade St.",
    "district": "San Fernando",
    "city": "Mangaldan",
    "state": "Pangasinan",
    "postal_code": "4233",
    "country": "PH",
    "remarks": "Optional notes / remarks go here."
  },
  "return_address": {
    "name": "JJ. ABC",
    "company": "Maxis",
    "phone_number": "6358972",
    "mobile_number": "+63907117421",
    "line_1": "3F U311 Bldg. C",
    "line_2": "Jade St.",
    "city": "Baguio City",
    "state": "Benguet",
    "postal_code": "1226",
    "country": "PH",
    "remarks": "Optional notes / remarks go here."
  },
  "pickup_address": {
    "name": "JJJ. Doe",
    "company": "Maxis",
    "phone_number": "6358972",
    "mobile_number": "+63907117421",
    "line_1": "3F U311 Bldg. C",
    "line_2": "Jade St.",
    "city": "Baguio City",
    "state": "Benguet",
    "postal_code": "1226",
    "country": "PH",
    "remarks": "Optional notes / remarks go here."
  },
  "preferred_pickup_time": "morning",
  "preferred_delivery_time": "3pm - 5pm",
  "reference_id": "{{reference_id}}",
  "email": "johndoe@email.com",
  "contact_number": "+639172274819",
  "items": [
    {
      "type": "product",
      "description": "Red Shirt",
      "amount": 1250,
      "quantity": 1,
      "metadata": {"size":"medium","color":"red"}
    },
    {
      "type": "product",
      "description": "Blue Shirt",
      "amount": 700,
      "quantity": 2,
      "metadata": {"size":"medium","color":"blue"}
    },
    {
      "type": "tax",
      "description": "Tax",
      "amount": 132.50
    },
    {
      "type": "shipping",
      "description": "Expedited Shipping",
      "amount": 150
    },
    {
      "type": "fee",
      "description": "Handling Fee",
      "amount": 20
    },
    {
      "type": "fee",
      "description": "Gift Wrapping Fee",
      "amount": 50.75
    },
    {
      "type": "insurance",
      "description": "Insurance",
      "amount": 150
    }
  ]
}'
```


> Example Response


```json
{
  "currency": "PHP",
  "total": "3153.25",
  "payment_method": "cod",
  "status": "for_dropoff",
  "payment_provider": "lbcx",
  "shipment": "big-pouch",
  "buyer_name": "Test buyer",
  "buyer_id": "12345",
  "metadata": {
    "key_1": "value_1",
    "key_2": "value_2"
  },
  "delivery_address": {
    "name": "Test buyer",
    "company": "Maxis",
    "phone_number": "6358972",
    "mobile_number": "+63907117421",
    "line_1": "3F U311 Bldg. C",
    "line_2": "Jade St.",
    "district": "San Fernando",
    "city": "Mangaldan",
    "state": "Pangasinan",
    "postal_code": "4233",
    "country": "PH",
    "remarks": "Optional notes / remarks go here."
  },
  "return_address": {
    "name": "JJ. ABC",
    "company": "Maxis",
    "phone_number": "6358972",
    "mobile_number": "+63907117421",
    "line_1": "3F U311 Bldg. C",
    "line_2": "Jade St.",
    "city": "Baguio City",
    "state": "Benguet",
    "postal_code": "1226",
    "country": "PH",
    "remarks": "Optional notes / remarks go here."
  },
  "pickup_address": {
    "name": "JJJ. Doe",
    "company": "Maxis",
    "phone_number": "6358972",
    "mobile_number": "+63907117421",
    "line_1": "3F U311 Bldg. C",
    "line_2": "Jade St.",
    "city": "Baguio City",
    "state": "Benguet",
    "postal_code": "1226",
    "country": "PH",
    "remarks": "Optional notes / remarks go here."
  },
  "preferred_pickup_time": "morning",
  "preferred_delivery_time": "3pm - 5pm",
  "reference_id": "7JUV0JNI",
  "email": "johndoe@email.com",
  "contact_number": "+639172274819",
  "items": [
    {
      "order_id": 908113,
      "type": "product",
      "description": "Red Shirt",
      "amount": 1250,
      "quantity": 1,
      "total": 1250,
      "metadata": {
        "size": "medium",
        "color": "red"
      },
      "insured_value": null,
      "id": 5286477
    },
    {
      "order_id": 908113,
      "type": "product",
      "description": "Blue Shirt",
      "amount": 700,
      "quantity": 2,
      "total": 1400,
      "metadata": {
        "size": "medium",
        "color": "blue"
      },
      "insured_value": null,
      "id": 5286478
    },
    {
      "order_id": 908113,
      "type": "tax",
      "description": "Tax",
      "amount": 132.5,
      "quantity": 1,
      "total": 132.5,
      "metadata": null,
      "insured_value": null,
      "id": 5286479
    },
    {
      "order_id": 908113,
      "type": "shipping",
      "description": "Expedited Shipping",
      "amount": 150,
      "quantity": 1,
      "total": 150,
      "metadata": null,
      "insured_value": null,
      "id": 5286480
    },
    {
      "order_id": 908113,
      "type": "fee",
      "description": "Handling Fee",
      "amount": 20,
      "quantity": 1,
      "total": 20,
      "metadata": null,
      "insured_value": null,
      "id": 5286481
    },
    {
      "order_id": 908113,
      "type": "fee",
      "description": "Gift Wrapping Fee",
      "amount": 50.75,
      "quantity": 1,
      "total": 50.75,
      "metadata": null,
      "insured_value": null,
      "id": 5286482
    },
    {
      "order_id": 908113,
      "type": "insurance",
      "description": "Insurance",
      "amount": 150,
      "quantity": 1,
      "total": 150,
      "metadata": null,
      "insured_value": null,
      "id": 5286483
    }
  ],
  "id": 908113,
  "tracking_number": "0090-8113-DFSY",
  "party_id": 7991,
  "charge": {
    "order_id": 908113,
    "status": "pending",
    "collector_party_id": null,
    "deposit_id": null,
    "reference_id": null,
    "total_amount": 3153.25,
    "tendered_amount": 0,
    "change_amount": 0,
    "remarks": null,
    "updated_by": null,
    "updated_at": {
      "date": "2018-11-19 12:42:03.901404",
      "timezone_type": 3,
      "timezone": "UTC"
    },
    "created_at": {
      "date": "2018-11-19 12:42:03.901404",
      "timezone_type": 3,
      "timezone": "UTC"
    }
  }
}
```


Creates an order for shipment.  Only authorized clients of QuadX can create orders.

An order is defined by a sender/shipper, a pickup address, the items (or parcels) being sent, the buyer, the recipient/consignee (possibly different from buyer), their delivery address, and payment information.

<p style="text-align:center;"><img src="https://i.imgur.com/LkBPnbV.png" class='small'/></p>

### Address Data ###
A delivery address is required to create an order.  A pickup address can be provided, but is only required once the order has been tagged as "ready for pickup".  An address is comprised of the following fields:

<table>
  <tr>
    <th>Field Name, Type, Character Limit, Required?</th>
    <th>Sample Value</th>
    <th>Definition</th>
  </tr>
  <tr>
    <td>`name`
    <i>string</i><br/>
    255 characters<br/>
    <i>required</i></td>
    <td>`John Doe`</td>
    <td>name of the sender/consignee</td>
  </tr>
  <tr>
    <td>`shipment`
    <i>string</i><br/>
    50 characters<br/>
    <i>required</i></td>
    <td>`small-pouch`</td>
    <td>type of package with possible values: `small-pouch, medium-pouch, big-pouch, box, oversized`</td>
  </tr>
  <tr>
    <td>`company`
    <i>string</i><br/>
    255 characters<br/>
    <i>optional</i></td>
    <td>`QuadX`</td>
    <td>company name (if applicable)</td>
  </tr>
  <tr>
    <td>`title`
    <i>string</i><br/>
    50 characters<br/>
    <i>optional</i></td>
    <td>`Mr.`</td>
    <td>title (eg, Mr., Mrs., Ms., Officer)</td>
  </tr>
  <tr>
    <td>`email`
    <i>string</i><br/>
    50 characters<br/>
    <i>optional</i></td>
    <td>johndoe@quadx.xyz</td>
    <td>email address</td>
  </tr>
  <tr>
    <td>`phone_number`
    <i>string</i><br/>
    50 characters<br/>
    <i>optional</i></td>
    <td>`4331234`</td>
    <td>phone number (landline)</td>
  </tr>
  <tr>
    <td>`mobile_number`
    <i>string</i><br/>
    50 characters<br/>
    <i>optional</i></td>
    <td>`09171234567`</td>
    <td>mobile number</td>
  </tr>
  <tr>
    <td>`fax_number`
    <i>string</i><br/>
    50 characters<br/>
    <i>optional</i></td>
    <td>`4331234`</td>
    <td>fax number</td>
  </tr>
  <tr>
    <td>`district`
    <i>string</i><br/>
    300 characters<br/>
    <i>optional</i></td>
    <td>`Poblacion`</td>
    <td>district</td>
  </tr>
  <tr>
    <td>`line_1`
    <i>string</i><br/>
    500 characters<br/>
    <i>required</i></td>
    <td>`2F U221 Bldg. A`</td>
    <td>address line 1</td>
  </tr>
  <tr>
    <td>`line_2`
    <i>string</i><br/>
    500 characters<br/>
    <i>optional</i></td>
    <td>`Emerald St.`</td>
    <td>address line 2 (if applicable)</td>
  </tr>
  <tr>
    <td>`city`
    <i>string</i><br/>
    300 characters<br/>
    <i>required</i></td>
    <td>`Makati`</td>
    <td>city</td>
  </tr>
  <tr>
    <td>`state`
    <i>string</i><br/>
    300 characters<br/>
    <i>required</i></td>
    <td>`Metro Manila`</td>
    <td>state or province</td>
  </tr>
  <tr>
    <td>`postal_code`
    <i>string</i><br/>
    50 characters<br/>
    <i>required</i></td>
    <td>`1600`</td>
    <td>postal or zip code</td>
  </tr>
  <tr>
    <td>`country`
    <i>string</i><br/>
    50 characters<br/>
    <i>required</i></td>
    <td>`PH`</td>
    <td>2-letter [ISO country code](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) (eg, US)</td>
  </tr>
  <tr>
    <td>`remarks`
    <i>string</i><br/>
    500 characters<br/>
    <i>optional</i></td>
    <td>`imported items; kindly double check`</td>
    <td>additional descriptive notes</td>
  </tr>
</table>

<p style="text-align:center;"><img src="https://i.imgur.com/LkBPnbV.png" class='small'/></p>

### Product Data ###
It is also required to pass the items which comprise the order.  This is used as the basis for printing the waybill, as well as computing insurance, shipping and transaction costs.  "items" is an array of items, each of which is described by the following fields:

<table>
  <tr>
    <th>Field Name, Type, Character Limit, Required?</th>
    <th>Sample Value</th>
    <th>Definition</th>
  </tr>
  <tr>
    <td>`type`
    <i>string</i><br/>
    10 characters<br/>
    <i>required</i></td>
    <td>`tax`</td>
    <td>one of product, shipping, tax, fee, insurance, discount (see below for definitions)</td>
  </tr>
  <tr>
    <td>`description`
    <i>string</i><br/>
    500 characters<br/>
    <i>required</i></td>
    <td>`Bracelet`</td>
    <td>item description</td>
  </tr>
  <tr>
    <td>`amount`
    <i>float</i><br/><br/>
    <i>required</i></td>
    <td>`123.45`</td>
    <td>amount of item (rounded to two decimal places)</td>
  </tr>
  <tr>
    <td>`quantity`
    <i>integer</i><br/><br/>
    <i>required</i></td>
    <td>`2`</td>
    <td>number of items (defaults to 1, applicable only to products)</td>
  </tr>
  <tr>
    <td>`preferred_pickup_time`
    <i>string</i><br/>
    100 characters<br/>
    <i>optional</i></td>
    <td>`morning`</td>
    <td>descriptive string re: preferred time of pickup</td>
  </tr>
  <tr>
    <td>`preferred_delivery_time`
    <i>string</i><br/>
    100 characters<br/>
    <i>optional</i></td>
    <td>`2pm-5pm`</td>
    <td>descriptive string re: preferred time of pickup</td>
  </tr>
  <tr>
    <td>`metadata`
    <i>jsonb</i><br/><br/>
    <i>optional</i></td>
    <td>{"product_image": "https://cdn.checkmeout.ph/v1/e87.png"}</td>
    <td>additional JSON-encoded metadata</td>
  </tr>
</table>

<p style="text-align:center;"><img src="https://i.imgur.com/LkBPnbV.png" class='small'/></p>

### Item Type Data ###
Each item can be one of several types.  At least one "product" must be present, with the others being optional.

<table>
  <tr>
    <th>Field Name</th>
    <th>Required?</th>
    <th>Definition</th>
  </tr>
  <tr>
    <td>`product`</td>
    <td>yes; at least 1</td>
    <td>at least 1 product entry is required</td>
  </tr>
  <tr>
    <td>`shipping`</td>
    <td>optional</td>
    <td>shipping fee charged, if any</td>
  </tr>
  <tr>
    <td>`tax`</td>
    <td>optional</td>
    <td>tax charged, if any</td>
  </tr>
  <tr>
    <td>`fee`</td>
    <td>optional</td>
    <td>additional fees charged, if any</td>
  </tr>
  <tr>
    <td>`insurance`</td>
    <td>optional</td>
    <td>insurance charged, if any</td>
  </tr>
  <tr>
    <td>`discount`</td>
    <td>optional</td>
    <td>discounts applied, if any (this must &lt;= 0))</td>
  </tr>
</table>

<p style="text-align:center;"><img src="https://i.imgur.com/LkBPnbV.png" class='small'/></p>

### Payment Data ###
Payment details consist of the currency, total amount, payment method and provider:

<table>
  <tr>
    <th>Field Name, Type, Character Limit, Required?</th>
    <th>Sample Value</th>
    <th>Definition</th>
  </tr>
  <tr>
    <td>`total`
    <i>float</i><br/><br/>
    <i>required; at least 1</i></td>
    <td>`305.63`</td>
    <td>total value of the order,<br/>must match sum total of order items</td>
  </tr>
  <tr>
    <td>`currency`
    <i>string</i><br/>
    5 characters<br/>
    <i>required</i></td>
    <td>`PHP`</td>
    <td>3-letter <a href="https://en.wikipedia.org/wiki/ISO_4217">ISO currency code</a> (eg, PHP)</td>
  </tr>
  <tr>
    <td>`payment_method`
    <i>string</i><br/>
    15 characters<br/>
    <i>required</i></td>
    <td>`credit_card`</td>
    <td>must be one of the following:<br/> `credit_card`, `debit_card`, `otc`, `cod`, or `other`</td>
  </tr>
  <tr>
    <td>`payment_provider`
    <i>string</i><br/>
    15 characters<br/>
    <i>required</i></td>
    <td>`paypal`</td>
    <td>must be one of the following:<br/> `asiapay`, `dragonpay`, `lbc`, `lbcx`, `paypal`, or `other`</td>
  </tr>
</table>

<p style="text-align:center;"><img src="https://i.imgur.com/LkBPnbV.png" class='small'/></p>

If QuadX is the collecting agent for the order, then a separate charge object (accessible from the order) is created to track payment.  This is the case if the payment method is "COD" or if the caller is a Fuse client.

<p style="text-align:center;"><img src="https://i.imgur.com/LkBPnbV.png" class='small'/></p>

### Remaining Fields ###
The remaining fields of an order are:

<table>
  <tr>
    <th>Field Name, Type, Character Limit, Required?</th>
    <th>Sample Value</th>
    <th>Definition</th>
  </tr>
  <tr>
    <td>`buyer_name`
    <i>string</i><br/>
    100 characters<br/>
    <i>required; at least 1</i></td>
    <td>`Jane Doe`</td>
    <td>buyer's name</td>
  </tr>
  <tr>
    <td>`buyer_id`
    <i>integer</i><br/><br/>
    </td>
    <td>`123`</td>
    <td>buyer's account id</td>
  </tr>
  <tr>
    <td>`email`
    <i>string</i><br/>
    50 characters<br/>
    <i>required</i></td>
    <td>`janedoe@quadx.xyz`</td>
    <td>buyer's email address (one of email/contact number is required)</td>
  </tr>
  <tr>
    <td>`contact_number`
    <i>string</i><br/>
    50 characters<br/>
    <i>required</i></td>
    <td>`4331234`</td>
    <td>buyer's contact number (one of email/contact number is required)</td>
  </tr>
  <tr>
    <td>`status`
    <i>string</i><br/>
    15 characters<br/>
    <i>optional</i></td>
    <td>`pending`</td>
    <td>one of the following:<br> `pending`, `confirmed` or `for_pickup` (defaults to pending)</td>
  </tr>
  <tr>
    <td>`reference_id`
    <i>string</i><br/><br/>
    <i>optional</i></td>
    <td>`QGZ63AWA`</td>
    <td>unique reference id for order</td>
  </tr>
  <tr>
    <td>`own_print`
    <i>boolean</i><br/><br/>
    <i>optional</i></td>
    <td>`true`</td>
    <td>if `true`, client will print label,<br>if `false`, QuadX will print the label.<br>defaults to `false` if not passed.</td>
  </tr>
  <tr>
    <td>`pickup_total`
    <i>float</i><br/><br/>
    <i>optional</i></td>
    <td>`200.00`</td>
    <td>indicates the amount the rider needs to collect from the merchant.<br>defaults to 0 if not passed.<br>if passed, should be a value greater than 0.</td>
  </tr>
  <tr>
    <td>`metadata`
    <i>jsonb</i><br/><br/>
    <i>optional</i></td>
    <td>{"shop_id": "12345"}</td>
    <td>additional JSON-encoded metadata</td>
  </tr>
</table>


## <span class="http-get">GET</span> Get Orders

<div class="center-column"></div>

```
{{base_url}}/orders
```

```json
{
   "total":2,
   "per_page":25,
   "current_page":1,
   "last_page":1,
   "next_page_url":null,
   "prev_page_url":null,
   "from":1,
   "to":2,
   "data":[
      {
         "id":58,
         "currency":"PHP",
         "reference_id":"PZZSJDYC",
         "tracking_number":"0000-0058-WJGH",
         "payment_method":"cod",
         "payment_provider":"lbcx",
         "status":"for_pickup",
         "buyer_name":"John Doe",
         "email":"johndoe@email.com",
         "contact_number":"+639172274819",
         "subtotal":"2650.00",
         "tax":"132.50",
         "fee":"70.75",
         "insurance":"150.00",
         "shipping":"250.00",
         "total":"3253.25",
         "transaction_fee":"97.60",
         "insurance_fee":"32.53",
         "shipping_fee":"150.00",
         "metadata":{
            "key_1":"value_1",
            "key_2":"value_2"
         },
         "preferred_pickup_time":"morning",
         "preferred_delivery_time":"3pm - 5pm",
         "created_at":"2016-12-01 07:29:58+08",
         "buyer_name_parsed":{
            "first_name":"John",
            "middle_name":null,
            "last_name":"Doe"
         }
      },
      {
         "id":57,
         "currency":"PHP",
         "reference_id":"ZMVA34FC",
         "tracking_number":"0000-0057-GWVQ",
         "payment_method":"cod",
         "payment_provider":"lbcx",
         "status":"delivered",
         "buyer_name":"John Doe",
         "email":"johndoe@email.com",
         "contact_number":"+639172274819",
         "subtotal":"2650.00",
         "tax":"132.50",
         "fee":"70.75",
         "insurance":"150.00",
         "shipping":"250.00",
         "total":"3253.25",
         "transaction_fee":"97.60",
         "insurance_fee":"32.53",
         "shipping_fee":"150.00",
         "metadata":{
            "key_1":"value_1",
            "key_2":"value_2"
         },
         "preferred_pickup_time":"morning",
         "preferred_delivery_time":"3pm - 5pm",
         "created_at":"2016-11-29 13:01:30+08",
         "buyer_name_parsed":{
            "first_name":"John",
            "middle_name":null,
            "last_name":"Doe"
         }
      }
   ]
}
```

Returns a list of orders. Only basic order details such as id, currency, amount, etc. will be returned. Pagination details will also be included on both the JSON payload and response headers.


## <span class="http-get">GET</span> Get Orders by Tracking Number

<div class="center-column"></div>

```
{{base_url}}/orders/{{tracking_number}}
```

### Request Headers ###

<b> Authorization: </b> `Bearer {{jwt}}`

```json
{
    "id": 757540,
    "party_id": 5123,
    "service_id": null,
    "currency": "PHP",
    "reference_id": "QGZ63AWA",
    "tracking_number": "0075-7540-EMBN",
    "payment_method": "cod",
    "payment_provider": "lbcx",
    "seller_payment_method": null,
    "seller_payment_provider": null,
    "service": "next_day",
    "status": "for_pickup",
    "status_updated_at": "2018-03-16 08:10:50.287292+00",
    "buyer_name": "The Podium podium ",
    "email": "jgaguan@olx.ph",
    "contact_number": "+63 9178793421",
    "subtotal": "129.00",
    "tax": "0.00",
    "fee": "0.00",
    "insurance": "0.00",
    "discount": "0.00",
    "shipping": "0.00",
    "total": "129.00",
    "transaction_fee": "25.00",
    "insurance_fee": "5.00",
    "shipping_fee": "60.00",
    "return_fee": "0.00",
    "metadata": null,
    "preferred_pickup_time": null,
    "preferred_delivery_time": null,
    "created_at": "2018-03-16 08:10:50+00",
    "tat": {
        "for_pickup": 1521187850
    },
    "shipment": "small-pouch",
    "remarks": null,
    "buyer_id": null,
    "parcel": null,
    "estimated_delivery_date": null,
    "updated_at": "2018-03-16 08:10:50+00",
    "pickup_at": null,
    "client": null,
    "organization": {
        "party_id": 5123,
        "name": null,
        "external_id": "Q3wcm97RhgbGOVLRNGMJlg0ojBd2"
    },
    "pickup_address": {
        "id": 1531606,
        "code": null,
        "name": "Sample  Seller ",
        "title": "XPOST",
        "email": "jgaguan@olx.ph",
        "phone_number": "+63 9178784703",
        "mobile_number": "+63 9178784703",
        "fax_number": "+63 9178784703",
        "company": "",
        "line_1": "40th ",
        "line_2": "UnionBank Plaza, Meralco Avenue",
        "district": "San Antonio",
        "city": "Pasig City",
        "state": "Metro Manila",
        "postal_code": "1605",
        "region": "MMB",
        "country": {
            "code": "PH",
            "name": "Philippines"
        },
        "xcode": null,
        "city_approximation": "Pasig City",
        "branch_code": null
    },
    "delivery_address": {
        "id": 1531607,
        "code": null,
        "name": "The Podium podium ",
        "title": "XPOST",
        "email": "jgaguan@olx.ph",
        "phone_number": "+63 9178793421",
        "mobile_number": "+63 9178793421",
        "fax_number": "+63 9178793421",
        "company": "",
        "line_1": "20",
        "line_2": "Doña Julia Vargas Avenue",
        "district": "Bagong Silang",
        "city": "Mandaluyong City",
        "state": "Metro Manila",
        "postal_code": "1122",
        "region": "MMB",
        "country": {
            "code": "PH",
            "name": "Philippines"
        },
        "xcode": null,
        "city_approximation": "Mandaluyong City"
    },
    "return_address": {
        "id": null,
        "code": null,
        "name": null,
        "title": null,
        "email": null,
        "phone_number": null,
        "mobile_number": null,
        "fax_number": null,
        "company": null,
        "line_1": null,
        "line_2": null,
        "district": null,
        "city": null,
        "state": null,
        "postal_code": null,
        "region": null,
        "country": {
            "code": null,
            "name": null
        },
        "xcode": null
    },
    "dropoff_address": {
        "id": null,
        "code": null,
        "name": null,
        "title": null,
        "email": null,
        "phone_number": null,
        "mobile_number": null,
        "fax_number": null,
        "company": null,
        "line_1": null,
        "line_2": null,
        "district": null,
        "city": null,
        "state": null,
        "postal_code": null,
        "region": null,
        "country": {
            "code": null,
            "name": null
        },
        "xcode": null
    },
    "charge": {
        "order_id": 757540,
        "status": "pending",
        "reference_id": "71001373462284",
        "total_amount": "129.00",
        "tendered_amount": "0.00",
        "change_amount": "0.00",
        "remarks": null,
        "created_at": "2018-03-16 08:10:50+00",
        "updated_at": "2018-03-16 08:10:50+00"
    },
    "claim": {
        "status": null,
        "amount": null,
        "shipping_fee_flag": null,
        "insurance_fee_flag": null,
        "transaction_fee_flag": null,
        "assets": null,
        "reason": null,
        "remarks": null,
        "created_at": null,
        "updated_at": null,
        "tat": null,
        "reference_id": null
    },
    "buyer_name_parsed": {
        "first_name": "The Podium podium ",
        "middle_name": null,
        "last_name": null
    },
    "items": [
        {
            "type": "product",
            "description": "Sample Item ",
            "amount": "129.00",
            "quantity": 1,
            "total": "129.00",
            "metadata": null,
            "insured_value": null
        }
    ],
    "segments": [
        {
            "courier": "Central Hub",
            "type": "pick_up",
            "barcode_format": "qr",
            "tat": {
                "end_date": null,
                "start_date": null
            },
            "shipping_type": "land",
            "currency": null,
            "amount": null,
            "reference_id": "0075-7540-EMBN",
            "active": true,
            "hub_code": "CTR",
            "pickup_address": {
                "name": "Sample  Seller ",
                "title": "XPOST",
                "email": "jgaguan@olx.ph",
                "phone_number": "+63 9178784703",
                "mobile_number": "+63 9178784703",
                "fax_number": "+63 9178784703",
                "company": "",
                "line_1": "40th ",
                "line_2": "UnionBank Plaza, Meralco Avenue",
                "district": "San Antonio",
                "city": "Pasig City",
                "state": "Metro Manila",
                "postal_code": "1605",
                "region": "MMB",
                "country": {
                    "code": "PH",
                    "name": "Philippines"
                },
                "xcode": null
            },
            "delivery_address": {
                "name": "Central Hub",
                "title": null,
                "email": null,
                "phone_number": null,
                "mobile_number": null,
                "fax_number": null,
                "company": null,
                "line_1": "Allegro Center",
                "line_2": null,
                "district": "Magallanes",
                "city": "Makati",
                "state": "Metro Manila",
                "postal_code": "1232",
                "region": "MMB",
                "country": {
                    "code": "PH",
                    "name": "Philippines"
                },
                "xcode": null
            }
        },
        {
            "courier": "Central Hub",
            "type": "delivery",
            "barcode_format": "qr",
            "tat": {
                "end_date": null,
                "start_date": null
            },
            "shipping_type": "land",
            "currency": null,
            "amount": null,
            "reference_id": "71001373462284",
            "active": false,
            "hub_code": "CTR",
            "pickup_address": {
                "name": "Central Hub",
                "title": null,
                "email": null,
                "phone_number": null,
                "mobile_number": null,
                "fax_number": null,
                "company": null,
                "line_1": "Allegro Center",
                "line_2": null,
                "district": "Magallanes",
                "city": "Makati",
                "state": "Metro Manila",
                "postal_code": "1232",
                "region": "MMB",
                "country": {
                    "code": "PH",
                    "name": "Philippines"
                },
                "xcode": null
            },
            "delivery_address": {
                "name": "The Podium podium ",
                "title": "XPOST",
                "email": "jgaguan@olx.ph",
                "phone_number": "+63 9178793421",
                "mobile_number": "+63 9178793421",
                "fax_number": "+63 9178793421",
                "company": "",
                "line_1": "20",
                "line_2": "Doña Julia Vargas Avenue",
                "district": "Bagong Silang",
                "city": "Mandaluyong City",
                "state": "Metro Manila",
                "postal_code": "1122",
                "region": "MMB",
                "country": {
                    "code": "PH",
                    "name": "Philippines"
                },
                "xcode": null
            }
        }
    ],
    "children": []
}
```

Returns the details of an order by tracking number. Use the unique ID that was returned when you created an order. All order details are returned including the order items, charge details, pick up and delivery addresses.


## <span class="http-get">GET</span> Get Order Statuses

<div class="center-column"></div>

```
{{base_url}}/orders/statuses
```

### Request Headers ###

<b> Authorization: </b> `{{authorization}}`

```json
[
    {
        "name": "pending",
        "label": "Pending"
    },
    {
        "name": "for_pickup",
        "label": "Ready for pickup"
    },
    {
        "name": "picked_up",
        "label": "Picked up"
    },
    {
        "name": "failed_pickup",
        "label": "Failed pickup"
    },
    {
        "name": "failed_delivery",
        "label": "Failed delivery"
    },
    {
        "name": "in_transit",
        "label": "In transit"
    },
    {
        "name": "claimed",
        "label": "Claimed"
    },
    {
        "name": "delivered",
        "label": "Delivered"
    },
    {
        "name": "return_in_transit",
        "label": "Returned - in transit"
    },
    {
        "name": "returned",
        "label": "Returned"
    },
    {
        "name": "failed_return",
        "label": "Failed return"
    },
    {
        "name": "out_for_delivery",
        "label": "Out for delivery"
    },
    {
        "name": "confirmed",
        "label": "Confirmed"
    },
    {
        "name": "canceled",
        "label": "Canceled"
    },
    {
        "name": "for_consolidation",
        "label": "For Consolidation"
    },
    {
        "name": "consolidated",
        "label": "Consolidated"
    },
    {
        "name": "for_dropoff",
        "label": "Ready for dropoff"
    },
    {
        "name": "dropped_off",
        "label": "Dropped off"
    },
    {
        "name": "for_transfer",
        "label": "For Transfer"
    },
    {
        "name": "for_acceptance",
        "label": "For Acceptance"
    },
    {
        "name": "accepted",
        "label": "Accepted"
    },
    {
        "name": "out_for_return",
        "label": "Out for Return"
    },
    {
        "name": "for_payment",
        "label": "For Payment"
    },
    {
        "name": "paid",
        "label": "Paid"
    }
]
```

Returns the list of supported order statuses.


## <span class="http-put">PUT</span> Update Order

<div class="center-column"></div>

```
{{base_url}}/orders/{{tracking_number}}
```

### Request Headers ###

<b> Authorization: </b> `{{authorization}}`

```json
{
    "id": 70652,
    "party_id": 85,
    "currency_id": 113,
    "reference_id": "4",
    "pickup_address_id": 112793,
    "delivery_address_id": 112795,
    "return_address_id": null,
    "active_segment_id": null,
    "tracking_number": "0007-0652-ZRFE",
    "payment_method": "cod",
    "payment_provider": "lbcx",
    "status": "pending",
    "buyer_name": "Marvin Calizo",
    "email": "mcalizo@olx.ph",
    "contact_number": "+639178973012",
    "subtotal": "3000.00",
    "shipping": "0.00",
    "tax": "0.00",
    "fee": "0.00",
    "insurance": "0.00",
    "discount": "0.00",
    "grand_total": "3000.00",
    "total_collected": "0.00",
    "shipping_fee": "50.00",
    "insurance_fee": "30.00",
    "transaction_fee": "75.00",
    "metadata": null,
    "parcel": null,
    "ip_address": "172.34.31.6",
    "preferred_pickup_time": null,
    "preferred_delivery_time": null,
    "tat": "{\"pending\": 1490876423}",
    "remarks": null,
    "pickup_attempts": 0,
    "delivery_attempts": 0,
    "status_updated_at": "2018-11-30",
    "flagged": 0,
    "created_at": "2017-03-30 20:20:23+08",
    "updated_by": null,
    "updated_at": {
        "date": "2018-11-27 08:39:59.120154",
        "timezone_type": 3,
        "timezone": "UTC"
    },
    "shipment": "small-pouch",
    "pickup_method": "for_pickup",
    "buyer_id": null,
    "parent_id": null,
    "dropoff_address_id": null,
    "service_id": null,
    "estimated_delivery_date": "2018-12-04 00:00:00+08",
    "return_fee": "0.00",
    "seller_payment_method": null,
    "seller_payment_provider": null,
    "pickup_address": {
        "id": 112793,
        "party_id": 85,
        "type": "pickup",
        "name": "Jane Doee",
        "title": null,
        "email": "johndoe@email.caom",
        "phone_number": "4218244",
        "mobile_number": "+639172947494",
        "fax_number": null,
        "company": null,
        "line_1": "3F U311 Bldg. C",
        "line_2": null,
        "district": null,
        "city": "Cebu City",
        "state": "Cebu",
        "postal_code": "1600",
        "region": "VIS",
        "country_id": 1,
        "remarks": "cebubugtest",
        "hash": "8d014cc49d3ad6368c3f466dd72c7008",
        "created_by": null,
        "created_at": "2017-03-13 19:54:27.532821+08",
        "updated_by": null,
        "updated_at": {
            "date": "2018-11-27 08:39:59.157129",
            "timezone_type": 3,
            "timezone": "UTC"
        },
        "code": null,
        "deleted_at": null,
        "deleted_by": null,
        "preferred": 0,
        "latitude": null,
        "longitude": null,
        "v_address": null,
        "xcode": null
    },
    "segments": [
        {
            "id": 166918,
            "order_id": 70652,
            "courier_party_id": 13,
            "shipping_type": "land",
            "type": "pick_up",
            "status": "pending",
            "currency_id": null,
            "amount": null,
            "reference_id": "0007-0652-ZRFE",
            "pickup_address_id": 112794,
            "delivery_address_id": 2,
            "barcode_format": "qr",
            "tat": null,
            "flagged": 0,
            "created_at": "2018-11-26 11:26:12.46617+08",
            "updated_at": "2018-11-26 12:35:49+08",
            "delivery_address": {
                "id": 2,
                "party_id": 13,
                "type": "business",
                "name": "LBCX Allegro",
                "title": null,
                "email": null,
                "phone_number": null,
                "mobile_number": null,
                "fax_number": null,
                "company": null,
                "line_1": "Allegro Center",
                "line_2": null,
                "district": "Magallanes",
                "city": "Makati",
                "state": "Metro Manila",
                "postal_code": "1232",
                "region": "MMB",
                "country_id": 1,
                "remarks": null,
                "hash": "3b54e7bb435e741a514cd806de84810a",
                "created_by": null,
                "created_at": "2017-03-07 01:26:51.702674+08",
                "updated_by": null,
                "updated_at": null,
                "code": null,
                "deleted_at": null,
                "deleted_by": null,
                "preferred": 0,
                "latitude": null,
                "longitude": null,
                "v_address": null,
                "xcode": null
            }
        },
        {
            "id": 166919,
            "order_id": 70652,
            "courier_party_id": 13,
            "shipping_type": "land",
            "type": "delivery",
            "status": "pending",
            "currency_id": null,
            "amount": null,
            "reference_id": "0007-0652-ZRFE",
            "pickup_address_id": 112794,
            "delivery_address_id": 112795,
            "barcode_format": "qr",
            "tat": null,
            "flagged": 0,
            "created_at": "2018-11-26 11:26:12.46617+08",
            "updated_at": null,
            "delivery_address": {
                "id": 112795,
                "party_id": 85,
                "type": "delivery",
                "name": "Marvin Calizo",
                "title": null,
                "email": null,
                "phone_number": null,
                "mobile_number": null,
                "fax_number": null,
                "company": "OLX Philippines",
                "line_1": "40F Unionbank Plaza",
                "line_2": "Meralco Ave., Ortigas Center",
                "district": null,
                "city": "Pasig City",
                "state": "NCR",
                "postal_code": "1605",
                "region": "Mmb",
                "country_id": 1,
                "remarks": "Prod Engineering Team",
                "hash": "6d50b4954316fa4e84733e247eb6cadd",
                "created_by": null,
                "created_at": "2017-03-13 20:03:22.182296+08",
                "updated_by": null,
                "updated_at": null,
                "code": null,
                "deleted_at": null,
                "deleted_by": null,
                "preferred": 0,
                "latitude": null,
                "longitude": null,
                "v_address": null,
                "xcode": null
            }
        }
    ],
    "organization": {
        "party_id": 85,
        "name": "Kimstore"
    }
}
```

Updates `pickup_address`.


## <span class="http-put">PUT</span> Set order status to confirmed

<div class="center-column"></div>

```
{{base_url}}/orders/{{tracking_number}}/confirm
```

### Request Headers ###
<b> Content Type: </b> `application/json`
<b> Authorization: </b> `{{authorization}}`

```json
{
  "payment_reference_id": "1234567890"
}
```

Sets the order status to confirmed.


## <span class="http-put">PUT</span> Set order status to cancel

<div class="center-column"></div>

```
{{base_url}}/orders/{{tracking_number}}/cancel
```

### Request Headers ###
<b> Content Type: </b> `application/json`
<b> Authorization: </b> `{{authorization}}`

Sets the order status to canceled. An order can be canceled provided they have not passed the cutoff date and time as specified in the contract.


## <span class="http-put">PUT</span> Set order status to for_pickup

<div class="center-column"></div>

```
{{base_url}}/orders/{{tracking_number}}/for-pickup
```

### Request Headers ###
<b> Content Type: </b> `application/json`
<b> Authorization: </b> `{{authorization}}`

> Example Request

```json
{
  "pickup_address": {
    "name": "Mart Rules 2",
    "company": "Company name",
    "phone_number": "12345",
    "mobile_number": "54321",
    "line_1": "Street 2",
    "line_2": "District 2",
    "city": "City 2",
    "state": "Abra 2",
    "postal_code": "1630-2",
    "country": "PH",
    "remarks": "Remarks here"
  }
}

```

> Example Response

```json
{"tracking_number":"0000-0060-HZFJ","old_status":"for_pickup","new_status":"failed_delivery"}
```

Sets the order status to for_pickup.


## <span class="http-put">PUT</span> Set order status to dropped_off

<div class="center-column"></div>

```
{{base_url}}/orders/{{tracking_number}}/dropped-off
```

### Request Headers ###
<b> Content Type: </b> `application/json`
<b> Authorization: </b> `{{authorization}}`

> Example Request

```json
{
  "tracking_number": "71000372125554",
  "shipment": "small-pouch",
  "branch_code": "ANT09",
  "return_address": {
      "name": "John Doe",
      "email": "johndoe@email.com",
      "company": "Maxis",
      "phone_number": "+1234567890",
      "mobile_number": "+1234567890",
      "line_1": "2F U221 Bldg. A",
      "line_2": "Emerald St.",
      "city": "Makati",
      "state": "Metro Manila",
      "postal_code": "1600",
      "country": "PH"
    },
  "parcel": {
    "weight": {
      "uom": "kg",
      "value": 5.7
    },
    "dimensions": {
      "length": 40,
      "width": 35,
      "height": 64,
      "uom": "cm"
    }
  }
}
```

> Example Response

```json
{"tracking_number":"0000-0060-HZFJ","old_status":"for_pickup","new_status":"failed_delivery"}

```

Sets the order status to dropped_off.

Required fields:
- tracking_number
- shipment
- branch_code

Optional field:
- return_address (array) - This attribute is included if the order's return address needs to be updated.
- parcel (array) - parcel attribute is only required if shipment's value is custom


## <span class="http-put">PUT</span> Set order status to for_dropoff

<div class="center-column"></div>

```
{{base_url}}/orders/{{tracking_number}}/for-dropoff
```

### Request Headers ###
<b> Content Type: </b> `application/json`
<b> Authorization: </b> `{{authorization}}`

> Example Request

```json
{
    "tracking_number": "0008-2110-HLKN",
    "remarks": "Remarks here",
    "return_address": {
      "name": "John Doe",
      "email": "johndoe@email.com",
      "company": "Maxis",
      "phone_number": "+1234567890",
      "mobile_number": "+1234567890",
      "line_1": "2F U221 Bldg. A",
      "line_2": "Emerald St.",
      "city": "Makati",
      "state": "Metro Manila",
      "postal_code": "1600",
      "country": "PH"
    },
    "metadata": {
      "merchant": {
        "email": "johndoe@email.com",
        "contact_number": "1234567890"
      }
    }
  }
```
> Example Response

```json
{"tracking_number":"0000-0060-HZFJ","old_status":"for_pickup","new_status":"failed_delivery"}
```

Sets the order status to for_dropoff.

Optional field:
- return_address (array)


# Orders
The following endpoints return information regarding Orders.
This API is the core of all order-related processes, from order creation, to getting orders and their statuses.

## Create Orders

<div class="center-column"></div>
```
{{base_url}}/orders
```

```
Example Request
```

```shell
curl --location --request POST '{{base_url}}/orders' \
--header 'Content-Type: application/json' \
--header 'Authorization: {{authorization}}' \
--data-raw '{
  "currency": "PHP",
  "total": "3153.25",
  "payment_method": "cod",
  "status": "for_dropoff",
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

```
Example Response
```

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

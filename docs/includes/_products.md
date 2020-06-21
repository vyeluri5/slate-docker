# PRODUCT

## Add Product

```shell

curl --request POST \
  --url /merchant/api/products/{merchantId} \
  --header 'Authorization: #qubykmarketplace' \
  --header 'Content-Type: application/json' \
  --data '{
	"merchantSku":"12345",
	"brand":"Gucci",
	"name":"T-shirt with two button fly and a pocket",
	"description":"This is an awesome T-Shirt",
	"productCode":"1298472923",
	"tags":["perfume"],
	"size":"12",
	"stock":5, 
	"price":4,
	"rrp":6,
	"shipTime":3,
	"categoryId":6,
	"image":[
                "https://hellworld.com/image1.png"
            ],
	"shipping":	[
					{
                        "countryCode":"US", "shippingFee": 1
                    },
                    {
                        "countryCode":"GB", "shippingFee": 1.5
                    }
				],
	"meta":	[
				{
                    "name": "length",
                    "value": "10"
                },
                {
                    "name": "width",
                    "value": "14"
                },
                {
                    "name": "height",
                    "value": "8"
                }
			]
}'

```

> The above command returns JSON structured like this:

```json
{
    "id": "d567ac34-e201-40de-b3d3-9d8f78f98e3f",
    "created": "2018-10-31T01:30:28.000+0000",
    "updated": "2018-10-31T01:30:28.000+0000",
    "merchantSku": "84300493",
    "brand": "Gucci",
    "name": "T-shirt with two button fly and a pocket",
    "description": "This is an awesome T-Shirt",
    "productCode": "1298472923",
    "tags": [
        "perfume"
    ],
    "size": "12",
    "stock": 5,
    "price": 4,
    "rrp": 6,
    "categoryId": "6",
    "shipTime": "3",
    "shipping": [
                    {
                        "countryCode":"US", "shippingFee": 1
                    },
                    {
                        "countryCode":"GB", "shippingFee": 1.5
                    }
    ],
    "image": [
        "https://hellworld.com"
    ],
    "meta": [
                {
                    "name": "length",
                    "value": "10"
                },
                {
                    "name": "width",
                    "value": "14"
                },
                {
                    "name": "height",
                    "value": "8"
                }
            ]
}
```

> Replace `merchantId` with your registered merchant account Id from your Merchant Portal.

This endpoint creates a new product with given attributes in example request.

### HTTP Request

`POST /merchant/api/products/{merchantId}`

### URL Parameters
Parameter | Required | Description
--------- | ------- | -----------
merchantId | Yes   | unique id created entire to qubyk marketplace


### Request Body (Json)

Parameter | Required | Description
--------- | ------- | -----------
merchantSku | Yes |The unique identifier that your system uses to recognize this product
brand |  Yes | Brand or manufacturer of your product
name |  Yes | Name of the product as shown to shoppers on qubyk marketplace
description | Yes | Description of the product. Text shouldn't contain any code or HTML. Add "\n" for a new line use 
productCode | Yes | Valid UPC or EAN code. No text characters are allowed
tags        | Yes | Comma separated list of strings that describe the product. Any tags past 10 will be ignored
size        | Yes | The size of the product
stock       | Yes | The physical quantities you have for this product
price       | Yes | The price of the variation when the user purchases one
rrp         | Yes | Manufacturer's Suggested Retail Price
categoryId  | Yes | CategoryId of product by its type. See [Get All Categories](#get-all-categories)
image       | Yes | Comma separated list of image urls of a product. Max 15 images allowed per product.
shipTime    | Yes | Minimum no of days requried to dispatch the order and cannot be less than 1
shipping    | Yes | Comma separated shipping objects with country code and shipping price. See Shipping Entity for parameters list
meta        | No  | Comma separated meta objects to add additional information to describe the product such as length, width, origin etc

### Required parameters for Shipping Entity

Parameter | Required | Description
--------- | ------- | -----------
countryCode | Yes   | Two letter country code
shippingFee | Yes   | Shipping fee for each country

**_(Optional)_** Meta entity can be optional, however, below fields are required in case it sent in add request. If it used the key values will be dynamically generated in our store front.

A maximum of 10 meta objects can be added for each product

Parameter | Required | Description
--------- | ------- | -----------
name | Yes   | name of the field. Ex: length
value | Yes   | value for the field. Ex: 10m


<aside class="success">
Remember — to use authorization key from <a href="#authentication">Authentication</a> to perform API requests.
</aside>


## Get Product


```shell
curl --request GET \
  --url /merchant/api/products/{merchantId}/{id} \
  --header 'Authorization: #qubykmarketplace'
```

> The above command returns JSON structured like this:

```json
{
    "id": "adc7e3d0-b4d7-4670-b0b8-34eb2b243bdc",
    "created": "2018-07-15T02:17:52.000+0000",
    "updated": "2018-07-15T02:56:57.000+0000",
    "sku": "MerchantId::12322",
    "merchantSku": "12322",
    "brand": "Gucci",
    "name": "T-shirt with two button fly and a pocket",
    "description": "This is an awesome T-Shirt",
    "productCode": "1298472923",
    "tags": [
        "perfume"
    ],
    "size": "12",
    "stock": "9",
    "price": 1,
    "rrp": 3,
    "categoryId": "8",
    "shipTime": "1",
    "shipping": [
        {
            "countryCode": "US",
            "shippingFee": 1
        }
    ],
    "image": [
        "https://hellworld.com"
    ],
    "meta": [
        {
            "name": "info",
            "value": "ss"
        }
    ]
}
```

> Replace `merchantId`,`id` with your registered merchant account Id and marketplace generated unique product id.

This endpoint is to retrieve a product information.

### HTTP Request

`GET /merchant/api/products/{merchantId}/{id}`

### URL Parameters
Parameter | Required | Description
--------- | ------- | -----------
merchantId | Yes   | unique id created entire to qubyk marketplace
id | Yes   | unique product id generated by qubyk marketplace

<aside class="success">
Remember — to use authorization key from <a href="#authentication">Authentication</a> to perform API requests.
</aside>


## Update Product

```shell
curl --request PUT \
  --url /merchant/api/products/{merchantId} \
  --header 'Authorization: #qubykmarketplace' \
  --header 'Content-Type: application/json' \
  --data '{
	"id":"02a6f431-2faf-4933-8af1-719b0dc37a56",
	"merchantSku":"988232932",
	"brand":"Gucci",
	"name":"T-shirt with two button fly and a pocket",
	"description":"This is an awesome T-Shirt",
	"productCode":"1298472923",
	"tags":["perfume"],
	"size":"12",
	"stock":9, 
	"price":1,
	"rrp":3,
	"categoryId": "9",
	"categoryId2": "8",
	"shipTime":1,
	"image":["https://hellworld.com"],
	"shipping":	[
					{ "countryCode":"US","shippingFee":1 }
				],
	"meta":	[
				{ "name":"info", "value": "ss" }
			]
}'
```

> The above command returns a status 204 No Content if request is successful.


This endpoint is to update product information.

### HTTP Request

`POST /merchant/api/products/{merchantId}`

###  Request Body (Json)


Parameter | Required | Description
--------- | ------- | -----------
merchantSku | Yes |The unique identifier that your system uses to recognize this product. It cannot be modified or updated
brand |  Yes | Brand or manufacturer of your product
name |  Yes | Name of the product as shown to shoppers on qubyk marketplace
description | Yes | Description of the product. Text shouldn't contain any code or HTML. Add "\n" for a new line use 
productCode | Yes | Valid UPC or EAN code. No text characters are allowed
tags        | Yes | Comma separated list of strings that describe the product. Any tags past 10 will be ignored
size        | Yes | The size of the product
stock       | Yes | The physical quantities you have for this product
price       | Yes | The price of the variation when the user purchases one
rrp         | Yes | Manufacturer's Suggested Retail Price
categoryId  | Yes | CategoryId of product by its type. See [link text](#get-all-categories)
image       | Yes | Comma separated list of image urls of a product. Max 15 images allowed per product.
shipTime    | Yes | Minimum no of days requried to dispatch the order and cannot be less than 1
shipping    | Yes | Comma separated shipping objects with country code and shipping price. See Shipping Entity for parameters list
meta        | No  | Comma separated meta objects to add additional information to describe the product such as length, width, origin etc

### Required parameters for Shipping Entity

Parameter | Required | Description
--------- | ------- | -----------
countryCode | Yes   | Two letter country code
shippingFee | Yes   | Shipping fee for each country

**_(Optional)_** Meta entity can be optional, however, below fields are required in case it sent in add request. If it used the key values will be dynamically generated in our store front.

A maximum of 10 meta objects can be added for each product

Parameter | Required | Description
--------- | ------- | -----------
name | Yes   | name of the field. Ex: length
value | Yes   | value for the field. Ex: 10m

<aside class="success">
Remember — to use authorization key from <a href="#authentication">Authentication</a> to perform API requests.
</aside>

## Update Price Stock

```shell
curl --request PUT \
  --url /merchant/api/products/pricestock/{merchantId} \
  --header 'Authorization: #qubykmarketplace' \
  --header 'Content-Type: application/json' \
  --data '{
	"id":"00126df4-5c48-449e-9466-f4d9c3d735fb",
	"merchantSku":"265756",
	"stock":10,
	"price":2,
	"rrp":7.97
}'
```
> The above command returns HTTP status 204 No Content if request is successful.

This end point is used to update pice and stock levels of a single product.

### HTTP Request

`PUT /merchant/api/products/pricestock/{merchantId}`

###  Request Body (Json)

Parameter | Required | Description
--------- | ------- | -----------
id      | Yes   | unique product id created entire to qubyk marketplace
merchantSku      | Yes   | The unique identifier that your system uses to recognize this product.
stock      | Yes   | The physical quantities you have for this product
price      | Yes   | The price of the variation when the user purchases one
rrp      | Yes   | Manufacturer's Suggested Retail Price


<aside class="success">
Remember — to use authorization key from <a href="#authentication">Authentication</a> to perform API requests.
</aside>

## Update Shipping

```shell
curl --request PUT \
  --url /merchant/api/products/shipping/{merchantId} \
  --header 'Authorization: #qubykmarketplace' \
  --header 'Content-Type: application/json' \
  --data '{
	"id":"00126df4-5c48-449e-9466-f4d9c3d735fb",
	"merchantSku":"23256756",
	"shipping":[
					{"countryCode":"US","shippingFee": 2.8},
					{"countryCode":"GB","shippingFee": 4.8}
				]	
}'
```
> The above command returns HTTP status 204 No Content if request is successful.

This end point is used to update shipping countries and cost. Previously set shipping options or prices will be replaced with current values.

### HTTP Request

`PUT /merchant/api/product/pricestock`

###  Request Body (Json)

Parameter | Required | Description
--------- | ------- | -----------
id      | Yes   | unique product id created entire to qubyk marketplace
merchantSku      | Yes   | The unique identifier that your system uses to recognize this product.
shipping    | Yes | Comma separated shipping objects with country code and shipping price. See Shipping Entity for parameters list. Any previous shipping entity will be overriden with current shipping values.


### Required parameters for Shipping Entity

Parameter | Required | Description
--------- | ------- | -----------
countryCode | Yes   | Two letter country code
shippingFee | Yes   | Shipping fee for each country

<aside class="success">
Remember — to use authorization key from <a href="#authentication">Authentication</a> to perform API requests.
</aside>

## Get All Categories


```shell
curl --request GET \
--url /store/api/categories \
--header 'Authorization: #qubykmarketplace'
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": "bc34b512dda44f54a5a93febe86862f5",
        "categoryId": 1,
        "categoryName": "Apps & Games"
    },
    {
        "id": "7150d67897e94d9fa492e755c4ec23fb",
        "categoryId": 2,
        "categoryName": "Arts, Crafts & Sewing"
    },
    {
        "id": "2ea84bbe0266495d968c64f7ee6233e1",
        "categoryId": 3,
        "categoryName": "Automotive Parts & Accessories"
    }
]
```

This endpoint is to retrieve a qubyk marketplace categories list. 

### HTTP Request

`GET /store/api/categories`

<aside class="success">
Remember — to use authorization key from <a href="#authentication">Authentication</a> to perform API requests.
</aside>

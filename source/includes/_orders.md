# Orders

## Get All Orders

```php
$api_client->get('orders', [
  'query' => [
    'page' => 4,
    'limit' => 50,
    'createdAfter' => '2000-04-03 00:00:00',
    'externalIds' => [
      'be7795a3-0f38-45c9-b534-661aade8ec1c',
      'test-external-id'
    ]
  ]
]);
```

> The above command returns JSON structured like this:

```json-doc
// -> Status Code: 200 OK
{
  "total_count": 12,
  "result": [
    {
      "id": 1,
      "external_id": "2964836b-e787-488f-a5e8-cc8bbb65822f",
      "transaction_id": 1,
      "status": "done",
      "created_at": "2020-04-07 20:12:36"
    },
    [...]
  ]
}
```

This endpoint retrieves all orders (without product keys).

### HTTP Request

`GET /orders`

### Query Parameters

Parameter | Type | Default | Required | Description
--------- | ---- | ------- | -------- | -----------
page | int | 1 | false | Current page (>= 1)
limit | int | 10 | false | Limit order count (between 1 and 100)
createdAfter | datetime | NULL | false | Get orders created after datetime
externalIds | array of strings | NULL | false | Find orders with given external id(s)

## Get Specific Order

```php
$api_client->get('orders/1');
```

> The above command returns JSON structured like this:

```json-doc
// -> Status Code: 200 OK
{
  "id": 1,
  "transaction_id": 1,
  "status": "done",
  "created_at": "2020-04-07 20:12:36",
  "product_keys": [
    {
      "product_id": 1,
      "type": "text/plain",
      "code": "0000-0000-0000-0000"
    },
    {
      "product_id": 2,
      "type": "image/jpeg",
      "code": "\/9j\/4AAQSkZJRgABAQAASABIAAD\/2wBDAAMCAgICAgMCAgIDAwMDBAYEBAQEBAgGBgUGCQgKCgkICQkKDA8MCgsOCwkJDRENDg8QEBEQCgwSExIQEw8QEBD\/wAALCAAoAWgBAREA\/8QAHAABAQEAAwEBAQAAAAAAAAAAAAgHBQYJBAEC\/8QAMRAAAQMEAgEDAwMEAQUAAAAAAgEDBAAFBgcIERIJEyEiMUEyYXEUFSNRF1NidIGi\/9oACAEBAAA\/APVOlKUpSlKUpSlKUpSlKUpSlKUpSlKUpSlKUpSlKVB\/qebt2Xj7OuOOGn79Is2SbXuyQX58V4mn246utMNsi4P1Ajrr6eRD0vi0Q\/YlRcS5EcIsh4Mazj8m+P8Au7M3MlxWZDPIUnvN+xObedBpTFtsU7D3TBCadV1FAl7L6fnbOcuzIm5vTDkbUiMDHHJoWPXFxgV7Rh450b3WkVfv4OeY9\/nxrsuuONuF8p\/T\/wBP6zzu7Xq22wLNaroj1odabf8AdaZMRHt1twfFUcLv6e\/hPmpk5V+nDxG4vabvGzb3sbY0maCf0dltx3CAi3C4Gi+018RO\/FOlM1T5QANU+ekXYvTN4tbE1fxqyzMxyJ3F8x2zBYkWg3YgPpaWGWn0gyDaNOjMikm6oL8eCtp8L5JXHMekrMz60OZLvzktm9+2JKFXluEN9HIcR9flERJAq66Ar9vEmfj4QRrmvSj2\/s7LrBszUWysmfyJNY3WLEt11lPE84rTpSQNn3S+o2wKL5B5KqojnXfigomfY7C2x6om0s1uZ7WvuE6HxC4raLdBspq27eHE7VDP58SNQ8XCJxDQEdbAQXsiqs+LvCLVvEu7X+663ybL7keRR2I8tu+TY74D7RESGHtMN9Evmvfff4+1YC76K3HB503S2VspFMlJepcD8r\/4tTjp3iTr61+pVaNX6aveQXXHtUux8gyK6XN5l00mxSFz2QVppsUH3zjMqKp5do8vfSdJ3nnTqbHd5+pnrfU+WzblEtGRYvDjSn7c423JbETuDiKBOAYovYJ9xX47r4+WfAuy8LtTSN\/cfd659ZrlYJ0Ns48y4tCclHnhaRGnIzbPRCpISiQkiiJ91bOLcl5+OcGrTye2ZCR65s4axd5jQojKTphAINInSdAj7pN9dJ0Pu\/CdJUX6F4vbh9ReySOQHJjduSW7GLrNfZsdis5IDZNtmoGbQH5NMNCaE2n0GZqBKRfZS\/jeOiN1emWlm3lx+3Df8gwVu4tQr3j16c8mh8+\/D3gDppxs+lD3BAHGyIPFV8u09N9WbCs22NcYzsrHUIbdk1rj3NgDXs2kdBCVsv8AuFVUV\/cVrtlKUpSlKUpSlKUpSlKUpSlKV5s890W3+oPxcvE9FGC7crdHAy\/Sjo3UO\/n9vdbVf\/VUd6kMuJD4TbRdmEKAcCI0Pf5cOdHEE\/nyVKk7PosuH6JlkZnIXuFHt7qd\/wDTO+oYf\/BDVocKZTEPh1qmZMfbYYZxGG466ZIINgLfakSr8IiIiqqrUb2FiV6m3MJ7J57Lr2htQP8AtQmXBVGbxJ8kVO0X7++QIZp19LDbYqgkfa+noiACgAKCIp0iInSIlR7zW5cX3Dp0fjRx0hu5JujMQ\/pGGYKof9iZcH5kOr9gd8FUhQlRAFPdNUFBQ+b4+cXG+JnFLKcQgSwuWYXSz3C63u5M99P3BYpIDbSr9Xtt9II99Kq+R9IpqiRD6eHEBvlRoq7psfamUWzArTksmPFxrHpTcVJNxWPGJ6XKIgNHP8ZMAAqPaeBKioir5arxaHM+JPPy48OIWeXfJtfZDa3J1qYub3uHCNIiygc6ToWzRGnWi8EETRQJRRUFEuPkpue2ce9I5Ztm4+2blkgEsFg1+JM5xUbjNf76J0gRevsPkv4qb\/So05dMU0tdN45qrsjLNt3E7zIkvp\/mKEJn7Kkv+3DN97tP1C63\/qsE5z4LkeyvU11tg+JbBuOD3i74xDZiZBbxMpEAkO4EpggONl2qCo\/Bj8Evz+K+Hlbwe37qbX\/\/ADVm\/I2ZviyYO81cpmN5n\/cQjk2po2piKTXPLrzRSRDbVRQvkv0rsfJfaEbkV6UFw2bieOt2SLLh2xXrPGRPahpDuzLDzTaIiJ7QEypD8J9Aj8JW4enJdrZd+FusXLQQEEa3vxXhFU7B9uU8LiKn4VSRV\/gkX81wPqnXe123hFnka5OgLtzftMSEBKnbj6XGO70P7oDThfwK12f077bcbVwu1XGugGDx2lySKGnS+y7JedaX+FbMFT9lSqOpSlKUpSlKUpSlKUpSlKUpSpf53cS7nykwCzP4TemrLn2FTiueOzXyIG1IvH3GCMUVW\/JW2iQ0ReiaH8Kq1NWfaV9TXlvarNpjfNrwvCMKiTGJN3vMCSwb1yRr7OG0y+6pl9yFtAZbU+lLrpOqM5j8eckyvhPN4+6KxhblLgRrLbrRbllMMKUeJJYVe3XjBvtG2lJVUkVVRfuq1ne3tNcrGvTtwXQWpMQVc1egW+xZVAC6w2XI9uFh1ZIC+bwtF5OCy2XgZeQOGiIqKqpkmh7L6qnHPW0DVutuKmumbTANx4npVzhOSZb7hdm88Y3UUM1+E76REERFERBRE3rD859TG\/aw2WudaYxDHsvYtLA4QNsmQySTNccUXlNSnvNorbaoY+4oipJ8+X6albQOm\/U747XbIsqxfjPiF9ynKZBP3PI8ivcCbcnkIvIm0dS5gggp\/WXQ9kXSkq+I+NpcW8z565Nmt1g8rtRYliuNBaicgSbRJjuuuzvdbRGyRua+viraur8iidinz+FweLxq5r8MNhZXM4ZWjFs315l8tZwY7e5INLbHVVek6cfY\/QK+CGDq+YCPmPYotd94kcSt3Qt8ZBy65W3S2OZ9eYxQ7bZ7c4LjVtbIBbUlIFUBUWgRoAAjTxIyIiJfj99QnRHIDk5lWt9R4Pirjes2Lk3dMrv39ziNI0ZGrSILBuo8assq8aILZIRPCifIr1Ztis1qxqyW\/G7HCbh221RWoUOO2nQMsNAgNgP7IIoifxXn5zJ0Py4uHNLEOSHHXVNuypvFcfix2HLjdIbMZZQuS0Ns2nJTLpIgPivYqidqnyvSpXA7Tw31XuVOLu6g2Jr\/AAHXeL3dxobpLhz2OnmgMTQTVuXKd8fIRXxAR8uulXpVSrS1TxtwfWnHG2capoLfMeas8i1XMnx8P65ZKuHKPpF7DzN5xRRFVRRURF+O6i7F+LvqA8Kr3eLTxOvOPbCwG6yymM2a9vMtGyap0hOA64ygueKCKmy6iH4ipCnSIOOWaVu71BuTTGgeWuwbfgTOFyXJLuHxIhRXJj7fw83G7Uxcd9vtUcN0\/FsiNoTFTr2EslmteOWeBjtkgswrba4zUOHGaToGGGwQG2xT8IIiiJ+yVyNKUpSlKUpSlKUpSlKUpSlKUpSlKUpSlKUpSlTjv7gxp\/kNsKxbXvN1yvE8vsCAjF5xaaxDkvK2SEyTpOMu9k2qfQSIJIi9KqogoNAwIr0KBFhyJ8me6w0DTkqQgI6+QiiK4aNiIIRKna+IiPar0iJ8V9tKUpSlKUpSlKUpSlKUpSlK\/9k="
    }
  ]
}
```

This endpoint retrieves a specific order.

### HTTP Request

`GET /orders/{ID}`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the order to retrieve

<aside class="notice">
The product keys will only be included if the order status is <code>done</code>
</aside>

## Place Order

```php
$api_client->post('orders', [
  'json' => [
    'products' => [
      [
        'product_id' => 1,
        'quantity' => 4,
        'price_cents' => 615
      ],
      [...]
    ]
  ]
]);
```

> The above command returns JSON structured like this:

```json-doc
// -> Status Code: 201 Created
{
  "order_id": 14
}

// -> Status Code: 409 Duplicate
{
  "order_id": 12 // Id of already existing order
}
```

This endpoint places a new order. Please do not exceed a maximum of 50 units per order.

### HTTP Request

`POST /orders`

### Body Parameters

Parameter | Type | Default | Required | Description
--------- | ---- | ------- | -------- | -----------
products | array of products | - | true | Requested products
products.*.product_id | int | - | true | Product ID
products.*.quantity | int | - | true | Desired Quantity (max. 50)
products.*.price_cents | int | - | true | Maximum price in cents
external_id | string (max. 64 chars) | NULL | false | **strongly recommended** External ID to avoid duplicate orders (because of connection problems or similar)

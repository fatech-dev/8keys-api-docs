# User

## Get Balance

```php
$api_client->get('balance');
```

> The above command returns JSON structured like this:

```json-doc
// -> Status Code: 200 OK
{
  "balance": 10000 // 100.00 €
}
```

This endpoint retrieves your current balance in cents. Make sure to use the appropriate endpoint.

### HTTP Request

`GET /balance`

### Query Parameters

No parameters available.

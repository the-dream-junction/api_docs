# Cancel Order

Submit an order cancellation request.

## Order Cancel Request

  `DELETE https://api.thedreamjunction.com/api/v3/orders/<order_id>`  
  `Content-Type: application/json`  
  `Authorization: Token token=<16-24 character API key>`

## Order Cancel Example Request

  `DELETE https://api.thedreamjunction.com/api/v3/orders/7048816`  
  `Content-Type: application/json`  
  `Authorization: Token token=<16-24 character API key>`

## Order Cancel Example Response

### Response Parameters

**status**
: Response type (ok, unprocessable_entity). Expected status codes are: [200, 422].

**message**
: Message string describing success or reason for failure.

**order**
: The id of the order requested.

## Success

```json
{
  "status": "ok",
  "message": "Order 7048816 successfully canceled.",
  "order": 7048816
}
```

## Failure

```json
{
  "status": "unprocessable_entity",
  "message": "This order is already canceled.",
  "order": 7048816
}
```

```json
{
  "status": "unprocessable_entity",
  "message": "This order is already in production and cannot be canceled.",
  "order": 7048816
}
```

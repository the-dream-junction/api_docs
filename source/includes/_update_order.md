# Update Order

Submit an order change request for the shipping carrier, method, or address.

## Update Order Request

  `PUT https://api.thedreamjunction.com/api/v3/orders/<order_id>`  
  `Content-Type: application/json`  
  `Authorization: Token token=<16-24 character API key>`

## Update Order Example Request

  `PUT https://api.thedreamjunction.com/api/v3/orders/7048816`  
  `Content-Type: application/json`  
  `Authorization: Token token=<16-24 character API key>`

## Update Order Parameters

> Example

```json
{
  "ship_provider": "UPS",
  "ship_method": "Ground",
  "ship_to": {
    "first_name": "Customer",
    "last_name": "Name",
    "company_name": "",
    "address": "1915 S Susan St",
    "address_2": "",
    "city": "Santa Ana",
    "state": "",
    "zip_code": "92704",
    "country": "US",
    "email": "customer@domain.com",
    "telephone": "5555555555"
  }
}
```

## Update Order Example Response

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
  "message": "Order 7048816 successfully updated.",
  "order": 7048816
}
```

## Failure

```json
{
  "status": "unprocessable_entity",
  "message": "This order is already packaged or shipped and cannot be updated.",
  "order": 7048816
}
```

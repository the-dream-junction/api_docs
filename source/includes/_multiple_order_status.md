# Multiple Order Status
Request status of 100 most recent orders, with pagination.

## Multiple Order Status Request
	`GET http://api.thedreamjunction.com/api/v3/orders`  
	`Content-Type: application/json`  
	`Authorization: Token token=<16-24 character API key>`

### Example Request
	`GET http://api.thedreamjunction.com/api/v3/orders`  
	`Content-Type: application/json`  
	`Authorization: Token token=<16-24 character API key>`

## Multiple Order Status Response

```jso
    {
      "orders": [
        {
          "order": {
            "id": 999,
            "purchase_order": "123456789",
            "created_at": "2014-06-30T23:56:24.691-07:00",
            "status": "open",
            "client_amount": 5.25,
            "items": [
              {
                "id": 33448,
                "customer_sku": "1415956-15",
                "sku_id": 202,
                "description": "T-Shirt",
                "workflow_state": "open",
              }
            ]
          }
        },
        {
          "order": {
            "id": 998,
            "purchase_order": "987654321",
            "created_at": "2014-06-30T23:00:25.492-07:00",
            "status": "open",
        ...
    }
```

<aside class="notice">
For element details, please refer to the Order Status request above.
</aside>

## Additional Parameters
To retrieve a list of orders, optional url parameters listed below can be used in conjunction to retrieve a filtered list of orders:

**order_status**
:	The status of the orders to retrieve. Order status can be received, open, packaged, shipped and canceled.

**created_at_min**
:	Show orders created after date (format: 02-25-2015).

**created_at_max**
:	Show orders created before date (format: 02-26-2015).

**limit**
:	Amount of results. Default is 100. Maximum is 200.

**page**
:	The page number to retrieve the next list orders based on specified parameters.

### Request
	 `GET http://api.thedreamjunction.com/api/v3/orders?order_status=<order_status>&limit=<limit_number>`  
	 `Content-Type: application/json`  
	 `Authorization: Token token=<16-24 character API key>`

### Example Request
	 `GET http://api.thedreamjunction.com/api/v3/orders?order_status=shipped&limit=50`  
	 `Content-Type: application/json`  
	 `Authorization: Token token=<16-24 character API key>`

## Order Notifications
   <aside class="notice">
   If you would prefer that the Dream Junction system send order notifications instead of polling for order status please contact your Dream Junction representative. We can POST order notifications as the order status updates through to shipped.
   </aside>

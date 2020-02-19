# Multiple Order Status

Request status of 100 most recent orders, with pagination.

## Multiple Order Status Request

`GET https://api.thedreamjunction.com/api/v3/orders`  
`Content-Type: application/json`  
`Authorization: Token token=<16-24 character API key>`

## Example Request

`GET https://api.thedreamjunction.com/api/v3/orders`  
`Content-Type: application/json`  
`Authorization: Token token=<16-24 character API key>`

## Multiple Order Status Response

```json
{
  "orders": [
    {
      "order": {
        "id": 6724120,
        "purchase_order": "5697626056",
        "location": "Santa Ana",
        "received_at": "2020-02-01T23:00:24.691 -07:00",
        "created_at": "2020-02-01T23:56:24.691 -07:00",
        "shipped_at": "2020-02-02T12:21:24.691 -07:00",
        "status": "completed",
        "client_amount": 5.25,
        "order_notes": "Job 10315476 - 5000_RED_L on order in the following purchase order(s) | PO: 131671 - Arriving: 02/01/20 - From: Alpha Broder | ",
        "fulfillment_notes": "",
        "items": [
          {
            "id": 3344800,
            "customer_sku": "1415956-15",
            "sku_id": 2032,
            "description": "T-SHIRT",
            "workflow_state": "completed"
          }
        ],
        "shipments": [
          {
            "shipping_carrier": "DHL",
            "shipping_method": "Smartmail Expedited",
            "tracking_number": "9374869903500930473876",
            "search_link": "https://webtrack.dhlglobalmail.com/?trackingnumber=9374869903500930473876",
            "delivered": false
          }
        ],
        "order_status_notes": [
          {
            "note": "Job 10315476 - 5000_RED_L on order in the following purchase order(s) | PO: 131622 - Arriving: 02/06/20 - From: Alpha Broder |",
            "created_at": "2020-02-05T11:53:08-08:00"
          }
        ],
        "service_requests": [
          {
            "reason": "Order status inquiry",
            "workflow_state": "open",
            "items_count": 1,
            "created_at": "2020-02-10T15:20:14-08:00"
          }
        ]
      },
      {
        "order": {
          "id": 998,
          "purchase_order": "987654321",
          "created_at": "2018-06-30T23:00:25.492-07:00",
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
: The status of the orders to retrieve. Order status can be received, open, packaged, shipped and canceled.

**created_at_min**
: Show orders created after date (format: 02-25-2018).

**created_at_max**
: Show orders created before date (format: 02-26-2018).

**limit**
: Amount of results. Default is 100. Maximum is 200.

**page**
: The page number to retrieve the next list orders based on specified parameters.

### Request

`GET https://api.thedreamjunction.com/api/v3/orders?order_status=<order_status>&limit=<limit_number>`  
`Content-Type: application/json`  
`Authorization: Token token=<16-24 character API key>`

### Example Request

`GET https://api.thedreamjunction.com/api/v3/orders?order_status=shipped&limit=50`  
`Content-Type: application/json`  
`Authorization: Token token=<16-24 character API key>`

## Order Notifications

<aside class="notice">
If you would prefer that the Dream Junction system send order notifications instead of polling for order status please contact your Dream Junction representative. We can POST order notifications as the order status updates through to shipped.
</aside>

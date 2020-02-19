# Order Status

Request status of a single order

## Order Status Arguments

**id**
: Internal order id used by Dream Junction.

**purchase_order**
: Customer purchase order provided with the order.

## Order Status Request by Order ID

`GET https://api.thedreamjunction.com/api/v3/orders/<order_id>`  
 `Content-Type: application/json`  
 `Authorization: Token token=<16-24 character API key>`

## Example Request by Order ID

`GET https://api.thedreamjunction.com/api/v3/orders/6724120`  
 `Content-Type: application/json`  
 `Authorization: Token token=<16-24 character API key>`

## Order Status Request by Purchase Order

`GET https://api.thedreamjunction.com/api/v3/orders/show?purchase_order=<purchase_order>`  
 `Content-Type: application/json`  
 `Authorization: Token token=<16-24 character API key>`

## Example Request by Purchase Order

`GET https://api.thedreamjunction.com/api/v3/orders/show?purchase_order=5697626056`  
 `Content-Type: application/json`  
 `Authorization: Token token=<16-24 character API key>`

## Order Status Example Response

```json
{
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
}
```

**id**
: Internal order id.

**purchase_order**
: Customer purchase order number or string.

**location**
: The name of the location where the order will be produced.

**received_at**
: The timestamp of when the order was submitted via the API.

**created_at**
: The timestamp of when the order was released to production.

**shipped_at**
: The timestamp of when the order was shipped. Present if the order has shipped.

**status**
: Order status can be:

- received - Order has been received and is enqueued.
- production_hold - Order production location is being evaluated for optimal production.
- intake_hold - Order is being reviewed for address, artwork and inventory availability.
- open - The order is in production.
- completed - All items in the order have been printed.
- shipped - The order has been packaged and shipped.
- canceled - The order was canceled on request.

**client_amount**
: Order cost expected to be billed to client. Note: This can change as the order changes within our system and does not typically include the shipping carrier charges.

**order_notes**
: The latest order status note. A full list of notes is also available.

**fulfillment_notes**
: A list of issues that are blocking the order or items from production. Our automated systems will update this list and customer service will contact the account when it is possible to rectify.

**items**

- id: Internal item id.
- customer_sku: Customer-provided SKU name if provided.
- sku_id: Internal sku identification number.
- workflow_state: Item workflow state can be:
  - production_hold - The item production location is being evaluated for optimal production.
  - intake_hold - Item order is being reviewed for address, artwork and inventory availability.
  - open - The item is in production.
  - completed - The item has been printed.
  - shipped - The item has been shipped.
  - canceled - The item was canceled on request.

**shipments**

- shipping_carrier: The name of the shipping carrier.
- shipping_method: Shipping method returned by the shipping provider.
- tracking_number: Tracking number returned by the shipping provider for the package.
- search_link: Link to shipping carrier website for tracking information and progress.
- delivered: If tracking allows, a boolean with delivery confirmation.

**address** : Current delivery address for the order.

- ship_to_first_name
- ship_to_last_name
- ship_to_company_name
- ship_to_address
- ship_to_address_2
- ship_to_city
- ship_to_state
- ship_to_zip_code
- ship_to_country
- ship_to_email
- ship_to_telephone

**order_status_notes**

- note: The text contents of the note created by our production staff or inventory system.
- created_at: Timestamp of the date the note was created.

**service_requests**

- reason: The reason provided for the service request.
- items_count: The number of items affected by the service request reason.
- created_at: Timestamp of the date the note was created.
- workflow_state: The status of the service request. Service Request workflow state can be:
  - open - The service request is open and enqueued to be reviewed.
  - rejected - A Dream Junction employee has rejected the request with a follow-up.
  - approved - The request has been approved and next steps are provided.
  - closed - The request has been closed and can be completed or reopened.
  - canceled - Customer has canceled the request.
  - completed - The request has been closed and now completed. A request can still be reopened if not satisfactory.

## Order Status Response (no order found)

Status Code 404 Not Found

```json
{
  "status": "not_found",
  "message": "An order with that ID cannot be located"
}
```

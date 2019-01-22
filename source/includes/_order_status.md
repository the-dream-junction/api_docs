# Order Status

Request status of a single order

## Order Status Arguments

**id**
: Internal order id used by Dream Junction.

**purchase_order**
: Customer purchase order provided with the order.

## Order Status Request by Order ID

  `GET http://api.thedreamjunction.com/api/v3/orders/<order_id>`  
  `Content-Type: application/json`  
  `Authorization: Token token=<16-24 character API key>`

## Example Request by Order ID

  `GET http://api.thedreamjunction.com/api/v3/orders/16724`  
  `Content-Type: application/json`  
  `Authorization: Token token=<16-24 character API key>`

## Order Status Request by Purchase Order

  `GET http://api.thedreamjunction.com/api/v3/orders/show?purchase_order=<purchase_order>`  
  `Content-Type: application/json`  
  `Authorization: Token token=<16-24 character API key>`

## Example Request by Purchase Order

  `GET http://api.thedreamjunction.com/api/v3/orders/show?purchase_order=5697626056`  
  `Content-Type: application/json`  
  `Authorization: Token token=<16-24 character API key>`

## Order Status Example Response

```json
    {
      "id": 16724,
      "purchase_order": "5697626056",
      "created_at": "2014-06-30T23:56:24.691 -07:00",
      "shipped_at":  "2014-07-01T12:21:24.691 -07:00",
      "status": "shipped",
      "client_amount": 5.25,
      "items": [
        {
          "id": 33448,
          "customer_sku": "1415956-15",
          "sku_id": 202,
          "description": "T-Shirt",
          "workflow_state": "packaged",
        }
      ],
      "shipments": [
      {
        "shipping_method": "Smartmail Expedited",
        "tracking_number": "9374869903500930473876",
        "search_link": "http://webtrack.dhlglobalmail.com/?trackingnumber=9374869903500930473876"
        }
      ]
    }
```

**id**
: Internal order id

**purchase_order**
: Customer purchase order

**shipped_at**
: Present if the order has shipped

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

**items**

- id: Internal item id
- customer_sku: Customer-provided SKU
- sku_id: Internal sku
- workflow_state: Item workflow state can be:
  - production_hold - The item production location is being evaluated for optimal production.
  - intake_hold - Item order is being reviewed for address, artwork and inventory availability.
  - open - The item is in production.
  - completed - The item has been printed
  - shipped - The item has been shipped.
  - canceled - The item was canceled on request.

**shipments**

- shipping_method: Shipping method returned by the shipping provider.
- tracking_number: Tracking number returned by the shipping provider for the package.
- search_link: Link to shipping carrier website for tracking information and progress.

**address**  : Address fields included with the original order request or updated if requested.

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

## Order Status Response (no order found)

  Status Code 404 Not Found

```json
  {
    "status": "not_found",
    "message": "An order with that ID cannot be located"
  }
```
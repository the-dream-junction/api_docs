
# New Order
Create a new order
### New Order Request

`POST http://api.thedreamjunction.com/api/v3/orders`  
`Content-Type: application/json`    
`Authorization: Token token=<16-24 character API key>`  

### New Order Arguments

> Example

```json
    {
      "type": "order",
      "account_id": 1,
      "account_zip": "92704",
      "purchase_order": "1729598549",
      "garments_provided": false,
      "ship_provider": "DHL",
      "ship_method": "Ground",
      "ship_to": {
        "first_name": "Bob",
        "last_name": "Smith",
        "company_name": "The Dream Junction",
        "address": "123 Main St",
        "address_2": "Apt 1",
        "city": "Portland",
        "state": "Oregon",
        "zip_code": "97034",
        "country": "US",
        "email": "johnsmith@gmail.com",
        "telephone": "800-555-1212"
      },
      "ship_from": {
        "first_name": "",
        "last_name": "",
        "company_name": "The Dream Junction",
        "address": "1915 S Susan St",
        "address_2": "",
        "city": "Santa Ana",
        "state": "California",
        "zip_code": "92704",
        "country": "US"
      },
      "order_notes": "Beware the ferocious guard cat.",
      "shipping_label_url": "https://clientdomain.com/services/receipt?id=1729598549",
      "production_priority": "normal",
      "items": [
        {
          "customer_sku": "574247-15",
          "sku": "2001_ASPHALT_L",
          "name": "Breathe!",
          "description": "T-shirt - Womens Fitted Tee White LARGE",
          "quantity": "1",
          "attributes": {
            "style": "2001",
            "color": "asphalt",
            "size": "large"
          },
          "designs": [
            {
              "placement": "Front Center",
              "art_file": "art.tif",
              "art_url": "http:\/\/clientdomain.com\/wp-content\/assets\/art.tif",
              "thumbnail_url": "http:\/\/clientdomain.com\/wp-content\/assets\/thumbnail.jpg",
              "underbase": true
            }
          ]
        }
      ],
	"inserts": [
	 {
		"identifier": "insert-card-10-off-spring",
		"preview_url": "http:\/\/clientdomain.com\/wp-content\/assets\/insert.jpg"
	 }
	]
    }
```

**type**
:    Set to order

**account_id**
:	Assigned during your account setup. Contact support for your account number.

**account_zip**
:	Assigned during your account setup. Contact support for your account zip.

**purchase_order**
:	Any purchase order or internally assigned identifier. Must be unique to each order submission.

**ship_provider (optional)**
:	Describe carrier for shipping. Options include: UPS, USPS, FedEx or DHL. DHL is our preferred service, but other services can be discussed.

**ship_method (optional)**
:	Describe service level for shipping provider. Please contact support for a list of supported methods.

**tracking_number (optional)**
:	The tracking number associated with a provided shipment label. Used for customer service. If provided, the ship method is required.

**shipping_label_url (optional)**
:	The url of the pre-paid shipping label for this order.

**ship_to**
:	Provide as much information as possible. Address info is verified at time of packaging an order. Missing data can delay an order from entering production.

- first_name
- last_name
- company_name
- address
- address_2
- city
- state
- zip_code
- country
- email
- telephone

**ship_from (optional)**
:	Company name or first and last name are required. Address fields are required to override account level ship from address for shipping label return addresses.

- first_name
- last_name
- company_name
- address
- address_2
- city
- state
- zip_code
- country

**order_notes (optional)**
:	Any additional information for this order

**production_priority**
:	normal (default) or express

**items**
:	Array of one or more printable items.

- customer_sku (optional): For your internal tracking. Can be the item purchase order or a descriptive name for the item. This will be returned in order status notifications for each item.
- sku: Internal Dream Junction SKU. Optional if attributes below are provided.
- name (optional): Name of the product, usually to describe the design
- description (optional): Description of the product, usually used to describe the garment
- quantity: Integer of 1 or greater.
- attributes: If the sku is not provided, the attributes must be provided. Not all combinations are available. Refer to a Dream Junction SKUs list.
    * style: Short identifier matching Dream Junction garment style
    * color: Short identifier matching Dream Junction colors by style
    * size: Short identifier matching Dream Junction size by style

**designs**
:	Array of one or more designs to apply to an item.

- placement: Unspecified is default and will result in a front print. Possible values currently: 'Front', 'Back'
- art_file: Filename for print ready art. If not available locally, we will retrieve asynchronously from the art_url and name the retrieved file with this art_file name.
- art_url: Location of print ready art. If art_file is not available locally, we will retrieve it asynchronously from this url.
- thumbnail_url: Location of thumbnail. If not available locally, we will retrieve it asynchronously from this url.
- underbase: true or false. Indicate whether a white underbase layer should be applied to the print.

 **inserts (optional)**
:	Array of one or more inserts to apply to an order.

- identifier: Unique identifier string for an insert. If matched to an existing identifier in your account, then the insert graphic will be reused.
- preview_url: Location of preview image. We will retrieve the image asynchronously from this url.

## New Order Response

> Status Code 200 OK

```json
{
   "status": "ok",
   "message": "Order <order_id> successfully created.",
   "order": <order_id>
}
```
Status Code 200 OK

## Failed New Order Response Examples
> duplicate order  
> Status Code 422 Unprocessable Entity  

```json
    {
      "status": "unprocessable_entity",
      "message": "Validation failed: Purchase order has already been taken",
		"order": <order_id>
    }
```

  > missing items  
  > Status Code 422 Unprocessable Entity

  ```json

  {
    "status": "unprocessable_entity",
    "message": "Order is missing one or more items."
  }
  ```

  > missing skus  
  > Status Code 422 Unprocessable Entity

  ```json
    {
      "status": "unprocessable_entity",
      "message": "SKU cannot be found to process this item. SKU: sku_name"
    }
  ```

  > missing designs  
  > Status Code 422 Unprocessable Entity

  ```json
  {
    "status": "unprocessable_entity",
    "message": "Item is missing one or more designs"
  }
```

Status Code 422 Unprocessable Entity  

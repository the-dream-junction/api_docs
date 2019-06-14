
# New Order

Submit a new order request.

## New Order Request

`POST https://api.thedreamjunction.com/api/v3/orders`  
`Content-Type: application/json`  
`Authorization: Token token=<16-24 character API key>`

## New Order Parameters

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
    "state": "OR",
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
    "state": "CA",
    "zip_code": "92704",
    "country": "US"
  },
  "order_notes": "Beware the ferocious guard cat.",
  "shipping_label_url": "https://clientdomain.com/shipments/shipping-label.pdf",
  "packing_slip_url": "https://clientdomain.com/shipments/packing-slip.pdf",
  "addtl_ship_docs_url": "https://clientdomain.com/shipments/customs-declaration.pdf",
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
        "color": "ASPHALT",
        "size": "L"
      },
      "custom_tags": [
        {
          "tag_code": "NewTag",
          "tag_type": "hang tag",
          "image": "https://s3.amazonaws.com/pms-masters/2/IN.HO/BRJZ02101/M/S.png"
        },
        {
          "tag_code": "ExistingTag"
        }
      ],
      "designs": [
        {
          "placement": "Front Center",
          "art_file": "art.tif",
          "art_url": "https://clientdomain.com/wp-content/assets/art.tif",
          "thumbnail_url": "https://clientdomain.com/wp-content/assets/thumbnail.jpg",
          "underbase": true
        }
      ]
    }
  ],
  "inserts": [
    {
      "identifier": "insert-card-10-off-spring",
      "preview_url": "https://clientdomain.com/wp-content/assets/insert.jpg"
    }
  ]
}
```

**type**
: Set to order

**account_id**
: Assigned during your account setup. Contact support for your account number.

**account_zip**
: Assigned during your account setup. Contact support for your account zip.

**purchase_order**
: Any purchase order or internally assigned identifier. Must be unique to each order submission.

**ship_provider**
: The shipping provider to be used for the order. Options include:

- UPS
- USPS
- FedEx
- OSM
- DHL

OSM is our default domestic service provider. DHL is our default international service provider. If other service providers are needed please contact your account representative as additional setup may be required.

**ship_method (optional)**
: Describe service level for shipping provider. Please contact support for a list of supported methods.

**tracking_number (optional)**
: The tracking number associated with a provided shipment label. Used for customer service. If provided, the ship method is required.

**shipping_label_url (optional)**
: The url of a pre-paid shipping label for this order. Dream Junction will request the label and prepare it for our shipping system at the time of order print completion. Accepted formats include: JPG, GIF, PNG and PDF.

**packing_slip_url (optional)**
: The url of a packing slip document. Dream Junction will request the document and prepare it for our shipping system at the time of order print completion. Accepted formats include: JPG, GIF, PNG and PDF. If needed please contact your Dream Junction account manager as an additional cost may incur.

**addtl_ship_docs_url (optional)**
: The url of a additional shipping documents for this order. Dream Junction will request the document and prepare it for our shipping system at the time of order print completion. Accepted formats include: JPG, GIF, PNG and PDF. If needed please contact your Dream Junction account manager as an additional cost may incur.

**ship_to**
: Provide as much information as possible. Address information is verified at the time of order print completion. Missing data can delay an order from entering production.

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
: Company name or first and last name are required. Address fields are required to override account level ship from address for shipping label return addresses.

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
: Any additional information for this order.

**production_priority**
: normal (default) or rush. Rush orders will incur an additional fee to expedite the production of the order.

**items**
: Array of one or more printable items.

- customer_sku (optional): For your internal tracking. Can be the item purchase order or a descriptive name for the item. This will be returned in order status notifications for each item.
- sku: Internal Dream Junction SKU. Optional if attributes below are provided.
- name (optional): Name of the product or to describe the design.
- description (optional): Description of the product, used to describe the garment.
- quantity: Integer of 1 or greater.
- attributes: If the sku is not provided, the attributes must be provided. Not all combinations are available. Refer to the Dream Junction SKUs list.
  - style: Short identifier matching Dream Junction garment style.
  - color: Short identifier matching Dream Junction colors by style.
  - size: Short identifier matching Dream Junction size by style.

**designs**
: Array of one or more designs to apply to an item. Dream Junction attempts to store and reuse artwork if it currently exists to avoid duplication and allow for artwork updates as needed. If you prefer that each artwork file or design be downloaded at time of order please let your Dream Junction integration specialist know.

- placement: Unspecified is default and will result in a front center print. Print locations are approximate and any placement within the artwork can affect the position. Possible values include:  
  - 'Front Center' - Artwork will be printed on the front and center of the garment.
  - 'Back Center' - Artwork will be printed on the back and center of the garment.
  - 'Front Left Chest' - Artwork will be printed on the front and left chest area of the garment.
  - 'Front Right Chest' - Artwork will be printed on the front and right chest area of the garment.
  - 'Neck' - Artwork will be printed on the interior neck area of the garment.
- art_file: Filename for print ready art. If not available locally, we will retrieve asynchronously from the art_url and name the retrieved file with this art_file name.
- art_url: URL of print ready art. If art_file is not available locally, we will retrieve it asynchronously from this url. Supported formats include: PNG, TIFF, and JPG. Note: JPG file do not include transparency and can result in a large ink print area.
- thumbnail_url: Location of thumbnail. If not available locally, we will retrieve it asynchronously from this url.
- underbase: true (default) or false. Indicate whether a white underbase layer should be applied to the print.

**custom_tags (optional)**
: Array of one or more custom application tags to apply to an item in an order. Custom tags must be prearranged with the Dream Junction as they are physical goods and may incur an additional charge per item.

- tag_code: Unique identifier string for a custom tag. If matched to an existing identifier in your account, then the custom tag settings will be reused.
- tag_type: Type of custom tag to notify team of application type ie. 'hang tag', 'sticker'
- image: Location of preview image of the custom tag. We will retrieve the image asynchronously from this url.

**inserts (optional)**
: Array of one or more inserts to apply to an order. Inserts must be prearranged with the Dream Junction as they are physical goods and may incur an additional charge per insert.

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

Status Code 422 Unprocessable Entity

> Duplicate Order
> Status Code 422 Unprocessable Entity

```json
{
  "status": "unprocessable_entity",
  "message": "Validation failed: Purchase order has already been taken",
  "order": <order_id>
}
```

> Missing Items
> Status Code 422 Unprocessable Entity

```json
{
  "status": "unprocessable_entity",
  "message": "Order is missing one or more items."
}
```

> Missing Skus
> Status Code 422 Unprocessable Entity

```json
{
  "status": "unprocessable_entity",
  "message": "SKU cannot be found to process this item. SKU: <sku_name>"
}
```

> Missing Designs
> Status Code 422 Unprocessable Entity

```json
{
  "status": "unprocessable_entity",
  "message": "Item is missing one or more designs"
}
```

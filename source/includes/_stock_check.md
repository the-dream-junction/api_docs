# Stock Check

Request the current inventory status by SKU identifier.

## Stock Check Request

  `GET https://api.thedreamjunction.com/api/v3/stocks/<sku_identifier>`  
  `Content-Type: application/json`  
  `Authorization: Token token=<16-24 character API key>`

## Stock Check Example Request

  `GET https://api.thedreamjunction.com/api/v3/stocks/2001_BLACK_S`  
  `Content-Type: application/json`  
  `Authorization: Token token=<16-24 character API key>`

## Stock Check Example Response

### Repsonse Parameters

**id**
: The id of the sku queried.

**quantity**
: The quantity of stock on hand.

**identifier**
: The string identifier of the sku.

**on_order**
: The quantity of stock on order and arriving from a garment provider.

**eta**
: An array indicating the delivery dates for replenishment of the sku inventory.

```json
{
  "id": 14,
  "quantity": 2,
  "identifier": "GI18000_WHITE_M",
  "on_order": 12,
  "eta": [
    "2016-01-16 00:00:00 -0800"
  ]
}
```

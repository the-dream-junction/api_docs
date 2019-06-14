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

### Response Parameters

**id**
: The id of the sku queried.

**sku_identifier**
: The string identifier of the sku.

**sku_gtin**
: The GTIN (Global Trade Item Number) of the sku.

**location_id**
: The id of the stock warehouse location.

**location_name**
: The name of the stock warehouse location.

**quantity**
: The quantity of stock on hand.

**amt_on_order**
: The quantity of stock on order and arriving from a garment provider.

**expected_etas**
: An array indicating the delivery dates for replenishment of the sku inventory.

```json
[
  {
    "id": 2174,
    "sku_identifier": "2000_BLACK_L",
    "sku_gtin": "00821780001020",
    "location_id": 1,
    "location_name": "Santa Ana",
    "quantity": 1325,
    "amt_on_order": 216,
    "expected_etas": [
      "2019-06-11T15:32:23.000-07:00"
    ]
  },
  {
    "id": 20658,
    "sku_identifier": "2000_BLACK_L",
    "sku_gtin": "00821780001020",
    "location_id": 38,
    "location_name": "Kentucky",
    "quantity": 967,
    "amt_on_order": 1584,
    "expected_etas": [
      "2019-06-07T00:00:00.000-07:00",
      "2019-06-11T15:32:13.000-07:00"
    ]
  }
]
```

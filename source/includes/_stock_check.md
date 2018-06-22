# Stock Check
Request the current quantity in stock by SKU.

## Stock Check Request
	 `GET http://api.thedreamjunction.com/api/v3/stocks/sku_identifier`  
	 `Content-Type: application/json`  
	 `Authorization: Token token=<16-24 character API key>`

### Stock Check Example Request
	 `GET http://api.thedreamjunction.com/api/v3/stocks/2001_BLACK_S`  
	 `Content-Type: application/json`  
	 `Authorization: Token token=<16-24 character API key>`

### Example Response
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

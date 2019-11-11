# ENDPOINT 1

** **

**ASSETS  ** ​ https://api.citex.io/v1/market/assets

The assets endpoint is to provide a detailed summary for each currency available on the exchange.
```javascript
{  
   "BTC":{  
      "name":"bitcoin", 
      "unified_cryptoasset_id" :"1", 
      "can_withdraw": True, 
      "can_deposit": True, 
      "min_withdraw":"0.01", 
      "max_withdraw ":0
      "name":"bitcoin", 
      "maker_fee":"0.001", 
      "taker_fee":"0.001", 
   }, 
   "ETH":{  
      "name":"ethereum", 
      "unified_cryptoasset_id":"1027", 
      "can_withdraw": False, 
      "can_deposit": False, 
      "min_withdraw":"10.00", 
      "max_withdraw ":0 
      "maker_fee":"0.001", 
      "taker_fee":"0.001", 
   } 
} 
```

Assets response descriptions.

| **Name** | **Type** | **Description** |
| --- | --- | --- |
| name | string | Name of cryptocurrency. |
| unified\_cryptoasset\_id | integer | Unique ID of cryptocurrency assigned by​​Unified Cryptoasset ID​. |
| can\_withdraw | boolean | Identifies whether withdraws are enabled or disabled. |
| can\_deposit | boolean | Identifies whether deposits are enabled or disabled. |
| min\_withdraw | string | Identifies the single minimum withdraw amount of a cryptocurrency. |
| max\_withdraw | int | Identifies the single maximum withdraw amount of a cryptocurrency. 0 means no limit. |
| maker\_fee | string | Fees applied when liquidity is added to the order book. |
| taker\_fee | string | Fees applied when liquidity is removed from the order book. |

# ENDPOINT 2

**TICKER  ** ​https://api.citex.io/v1/market/ticker

The ticker endpoint is to provide a 24-hour pricing and volume summary for each market pair available on the exchange.
```javascript
{
    "ETH_BTC": {
        "base_id": 1,
        "quote_id": 2,
        "last_price": "0.930892",
        "quote_volume": "85157",
        "base_volume": "97886.872894",
        "isFrozen": 1
    },
    "BTC_USDT": {
        "base_id": 2,
        "quote_id": 3,
        "last_price": "17.01",
        "quote_volume": "112",
        "base_volume": "2",
        "isFrozen": 1
    }
}
```

Ticker response descriptions.

| **Name** | **Type** | **Description** |
| --- | --- | --- |
| Last\_price |   string | Last price in base pair. |
| base\_volume |   string | 24 hours transaction amount in base pair volume. |
| isFrozen |   int | 1 : enable. 0 : disable. |



# ENDPOINT 3

**ORDERBOOK  ** ​https://api.citex.io/v1/market/orderbook/market\_pair?market\_pair=ETH\_BTC&amp;depth=10

The order book endpoint is to provide a complete level 2 order book (arranged by best asks/bids) with full depth returned for a given market pair.

Parameters:

| **Name** | **Type** | **Description** |
| --- | --- | --- |
| market\_pair | string |   A pair such as &quot;ETH\_BTC&quot; |
| Depth(Optional) | Int |   Orders depth   List of size.   Default is 20. Max is 50. |
```javascript
{  
   "timestamp":"1566359163", 
   "bids":[  
      [  
         "12462000", 
         "0.04548320" 
      ], 
      [  
         "12457000", 
         "3.00000000" 
      ] 
   ], 
   "asks":[  
      [  
         "12506000", 
         "2.73042000" 
      ], 
      [  
         "12508000", 
         "0.33660000" 
      ] 
   ] 
} 
```

Order book response descriptions.

| **Name** | **Type** | **Description** |
| --- | --- | --- |
| timestamp |   string | Unix timestamp in milliseconds for when the last updated time occurred. |
| bids |   string | An array containing 2 elements. The offer price and quantity for each bid order. |
| asks |   string | An array containing 2 elements. The ask price and quantity for each ask order. |

# ENDPOINT 4

**TRADES  ** ​https://api.citex.io/v1/market/trades/market\_pair?market\_pair=ETH\_BTC&amp;side=sell

The trades endpoint is to return data on 50 recently completed trades for a given market pair.

Parameters:

| **Name** | **Type** | **Description** |
| --- | --- | --- |
| market\_pair | string |  A pair such as &quot;ETH\_BTC&quot;. |
| side(Optional) | string |  Query buy side or sell side. Default return both buy and sell sides. |
```javascript
[  
   { 	 
      "tradeID":3523643, 
      "price":"0.01", 
      "base_volume":"569000", 
      "quote_volume":"0.01000000", 
      "trade_timestamp":"1566360780", 
      "type":"sell" 
   } 
]
```

Trades response descriptions.

| **Name** | **Type** | **Description** |
| --- | --- | --- |
| trade\_id |   integer | A unique ID associated with the trade for the currency pair transaction |
| price |   string | Transaction price in base pair volume. |
| base\_volume |   string | Transaction amount in base pair volume. |
| quote\_volume |   string | Transaction amount in quote pair volume. |
| trade\_timestamp |   int | Unix timestamp in milliseconds for when the transaction occurred. |
| type |   string | Used to determine whether or not the transaction originated as a buy or sell.   Buy – Identifies an ask was removed from the order book.   Sell – Identifies a bid was removed from the order book. |
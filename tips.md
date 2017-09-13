# Tips

## Overview
|Endpoints|Description|
|----------|----------|
|[`GET /tips`](#get-tips)| Returns a list of tips for your channel |



## `GET /tips`
:key: Requires authentication  

Returns a list of tips for your channel.  

### Example Request  
```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/tips
```
  

### Example Response

```json
{
  "docs": [
    {
      "_id": "59b946aa19dff05ba6d3f676",
      "updatedAt": "2017-08-28T04:39:00.000Z",
      "_user": "59b946aac3df40c1a288e440",
      "approved": "allowed",
      "createdAt": "2017-08-28T04:39:00.000Z",
      "status": "success",
      "donation": {
        "amount": 92,
        "currency": "USD",
        "message": "Supplied message by user",
        "user": {
          "username": "User1"
        }
      },
      "provider": "paypal"
    },
    {
      "_id": "59b946aa1eb34da9188dce35",
      "updatedAt": "2017-08-28T04:36:29.000Z",
      "_user": "59b946aa7a4de7141b14a2dd",
      "approved": "allowed",
      "createdAt": "2017-08-28T04:36:29.000Z",
      "status": "success",
      "donation": {
        "amount": 80,
        "currency": "USD",
        "message": "User supplied message!",
        "user": {
          "username": "User2"
        }
      },
      "provider": "paypal"
    }
  ],
  "total": 2,
  "limit": 100,
  "offset": 0
}
```


# Tipping

## Overview
|Endpoints|Description|
|----------|----------|
|[`GET /tipping`](#get-tipping)| Returns an object with information about your tipping settings |
|[`GET /tipping/overlay?token=Api-Token`](#get-tippingoverlaytokenapi-token)| Returns an object with information about a users tipping settings using their Api-Token |
|[`PUT /tipping`](#put-tipping)| Updates your tipping settings |


## `GET /tipping`
:key: Requires authentication  

Returns an object with information about your tipping settings  

### Example Request  
```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/tipping
```
  
  
## `GET /tipping/overlay?token=Api-Token`
:key: Requires authentication  

Returns an object with information about your tipping settings  

### Example Request  
```bash
curl -X GET https://api.streamelements.com/kappa/v1/tipping/overlay?token=Api-Token
```

### Example Response

```json
{
  "_id": "37a02b4515fa1eaf1a03d215",
  "username": "user",
  "display_name": "user",
  "avatar": "https://static-cdn.jtvnw.net/jtv_user_pictures/user-profile_image-84f37fev24e59e92-300x300.jpeg",
  "tipping": {
    "_id": "27da6aba25ca17a71e08da17",
    "updatedAt": "2015-11-12T12:32:13.238Z",
    "createdAt": "2015-11-12T12:32:13.238Z",
    "title": "user's tippingpage",
    "_username": "user",
    "_user": "37a02b4515ff1eaf1a03d215",
    "memo": "",
    "profanity": {
      "custom": [],
      "replace": [],
      "mode": 1,
      "default": false,
      "filter": false
    },
    "moderation": {
      "moderators": [],
      "enabled": false
    },
    "currency": {
      "symbol": "$",
      "name": "U.S. Dollar",
      "code": "USD"
    },
    "leaderboard": {
      "totalAmount": false,
      "enabled": false
    },
    "minimum": 1,
    "suggested": 1,
    "forceLogin": false,
    "background": "https://s3.amazonaws.com/streamelements-uploads-dev/testing/fullbgplanet.jpg",
    "header": "https://s3.amazonaws.com/streamelements-uploads-dev/testing/planetheader.jpg"
  }
}
```


## `PUT /tipping`
:key: Requires authentication  

Updates your tipping settings  

### Example request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-H 'Content-Type: application/json' \
-X PUT https://api.streamelements.com/kappa/v1/tipping \
-d 'DATA'
```

DATA:
```
{
    "_id": "27da6aba25ca17a71e08da17",
    "updatedAt": "2015-11-12T12:32:13.238Z",
    "createdAt": "2015-11-12T12:32:13.238Z",
    "title": "user's tippingpage",
    "_username": "user",
    "_user": "37a02b4515ff1eaf1a03d215",
    "memo": "",
    "profanity": {
      "custom": [],
      "replace": [],
      "mode": 1,
      "default": false,
      "filter": false
    },
    "moderation": {
      "moderators": [],
      "enabled": false
    },
    "currency": {
      "symbol": "$",
      "code": "USD"
    },
    "leaderboard": {
      "totalAmount": false,
      "enabled": false
    },
    "minimum": 1,
    "suggested": 1,
    "forceLogin": false,
    "background": "https://s3.amazonaws.com/streamelements-uploads-dev/testing/fullbgplanet.jpg",
    "header": "https://s3.amazonaws.com/streamelements-uploads-dev/testing/planetheader.jpg",
    "paypalEmail": "user@example.com"
  }
```
### Example Response

```
{"status":200,"message":"Tipping settings was updated"}
```

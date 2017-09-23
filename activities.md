# Activities

## Overview
|Endpoints|Description|
|----------|----------|
|[`GET /activities`](activities.md#get-activities)|Returns a list of activities sorted by *createdAt*|
|[`GET /activities/:id`](activities.md#get-activitiesid)|Returns a single activity|

### Properties
|Type|Description|More|
|----|-----------|----|
|follow|When someone follows||
|host|When you get hosted|`username` is hosting you for `amount` viewers (soon)|
|tip|When someone tips|`data` also has `amount`, `currency` (soon) and the `message`|
|subscriber|When someone subscribes|`data` also has `amount` (in months) and the `message`|
|cheer|When someone cheers|`data` also has `amount` (in bits) and the `message`|

## `GET /activities`

:key: Requires authentication  

Returns a list of activities sorted by *createdAt*.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/activities
```

### Example Response

```json
[
  {
    "_id": "577c1d1b4d85915c2c121592",
    "_user": "577d1d1b4d85915c2c121593",
    "type": "follow",
    "data": {
     "username": "random"
    },
    "createdAt": "2016-10-10T19:30:30.625Z"
  },
  {
    "_id": "577c1d1b4d85915c2c121593",
    "_user": "577d1d1b4d85915c2c121593",
    "type": "subscriber",
    "data": {
      "username": "user",
      "amount": 12,
      "message": "HeyGuys"
    },
    "createdAt": "2016-10-07T11:35:37.479Z"
  }
]
```

## `GET /activities/:id`

:key: Requires authentication  

Returns a single activity

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/activities/:id
```

### Example Response

```json
{
  "_id": "577c1d1b4d85915c2c121593",
  "_user": "577d1d1b4d85915c2c121593",
  "type": "subscriber",
  "data": {
    "username": "user",
    "amount": 12,
    "message": "HeyGuys"
  },
  "createdAt": "2016-10-07T11:35:37.479Z"
}
```

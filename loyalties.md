# Loyalties

## Overview
|Endpoints|Description|
|----------|----------|
|[`GET /loyalties`](#get-loyalties)|Returns an object with information about your loyalties|
|[`GET /loyalties/:channel`](#get-loyaltieschannel)|Returns an object with information about someone's loyalties|

### Properties
|Fields|Type|Description|
|------|----|-----------|
|name|String|Name of the currency ( default 'points', maximum 30 )|
|enabled|Boolean|If it's enabled in the chat ( default true )|
|amount|Number|Amount of points earned every 10 minutes ( default 5, minimum 1, maximum 100 )|
|subscriberMultiplier|Number|What subs get extra (*amount* * X) ( default 3, minimum 1, maximum 10 )|
|bonuses|Object|Contains information about the bonus points|
|bonuses.cheer|Number|Bonus on cheer ( default 0, minimum 1, maximum 1000 )|
|bonuses.subscriber|Number|Bonus on subscribe ( default 0, minimum 1, maximum 1000 )|
|bonuses.tip|Number|Bonus on tip ( default 0, minimum 1, maximum 1000 )|
|bonuses.follow|Number|Bonus on follow ( default 0, minimum 1, maximum 1000 )|

## `GET /loyalties`
:key: Requires authentication  
  
Returns an object with information about your loyalties.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/loyalties
```

### Example Response

```json
{
  "_id": "57c12bb325ca27a71608da1b",
  "updatedAt": "2016-09-26T15:32:52.107Z",
  "createdAt": "2016-09-07T19:34:13.244Z",
  "_username": "streamelements",
  "loyalty": {
    "bonuses": {
      "cheer": 0,
      "subscriber": 0,
      "tip": 0,
      "follow": 0
    },
    "subscriberMultiplier": 3,
    "amount": 5,
    "enabled": true,
    "name": "points"
  }
}
```

## `GET /loyalties/:channel`
:old_key: Requires no authentication  
  
Returns an object with information about someone's loyalties.

### Example Request

```bash
curl -X GET https://api.streamelements.com/kappa/v1/loyalties/:channel
```

### Example Response

```json
{
  "name": "points",
  "enabled": true,
  "amount": 5,
  "subscriberMultiplier": 3,
  "bonuses": {
    "follow": 0,
    "tip": 0,
    "subscriber": 0,
    "cheer": 0
  }
}
```

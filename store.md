# Store

## Overview
|Endpoints|Description|
|----------|----------|
|[`GET /store/:channel/redemptions`](store.md#get-storechannelredemptions)| Returns a list of  redemptions. |
|[`GET /store/:channel/redemptions?limit=25&pending=true`](store.md#get-storechannelredemptionslimit25pendingtrue)| Returns a list of latest 25 redemptions with a pending state. |
|[`GET /store/:channel/items`](store.md#get-storechannelitems)| Returns a list of available items in the store. |
|[`PUT /store/:channel/items/:itemid`](store.md#put-storechannelitemsitemid)| Change a store items details. |
|[`POST /store/:channel/items`](store.md#post-storechannelitems)| Create a new store item. |



## `GET /store/:channel/redemptions`
:key: Requires authentication  

Returns a list of redemptions.

### Example Request  
```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/store/channelname/redemptions
```


### Example Response

```json
{
    "_total": 1,
    "docs": [
        {
            "_id": "59b6c8aa030e904baddb1f88",
            "updatedAt": "2017-09-11T17:32:26.707Z",
            "createdAt": "2017-09-11T17:32:26.707Z",
            "_user": "59bd7a5cad43c8dc2abae2e5",
            "redeemer": {
                "_id": "59bd7a5cad43c8dc2abae2e5",
                "username": "user1",
                "avatar": "https://static-cdn.jtvnw.net/jtv_user_pictures/59bd7a5cad43c8ec2abae2e5-profile_image-300x300.png",
                "inactive": false
            },
            "item": null,
            "input": [],
            "completed": true,
            "redeemerType": "User"
        }
    ]
}
```


## `GET /store/:channel/redemptions?limit=25&pending=true`
:key: Requires authentication  

Returns a list of latest 25 redemptions with a pending state.

### Example Request  
```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/store/channelname/redemptions?limit=25&pending=true
```


### Example Response

```json
{
    "_total": 1,
    "docs": [
        {
            "_id": "59bd7a5cf6f348388ae64ac4",
            "updatedAt": "2017-09-16T19:20:13.360Z",
            "createdAt": "2017-09-16T19:20:13.360Z",
            "_user": "59bd7a5cad43c8dc2abae2e5",
            "redeemer": {
                "_id": "59bd7a5cad43c8ec2fbae2e5",
                "username": "user1",
                "avatar": "https://static-cdn.jtvnw.net/jtv_user_pictures/59bd7a5cad43c8ec2fbae2e5-profile_image-300x300.png",
                "inactive": false
            },
            "item": {
                "_id": "59bd7a5c52aa9ae3cf2ed631",
                "name": "Ask a Question",
                "userInput": [
                    "Your question"
                ]
            },
            "input": [
                "test"
            ],
            "completed": false,
            "redeemerType": "User"
        }
    ]
}
```


## `GET /store/:channel/items`
:key: Requires authentication  

Returns a list of available items in the store.

### Example Request  
```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/store/channelname/items
```


### Example Response

```json
[
    {
        "_id": "59bd82379b0470affa06cf1f",
        "updatedAt": "2017-09-10T22:22:32.096Z",
        "createdAt": "2017-09-10T22:22:32.096Z",
        "_user": "59bd7a5cad43c8ec2fbae2e5",
        "enabled": true,
        "featured": false,
        "name": "Twitter Follow",
        "type": "perk",
        "accessLevel": 100,
        "cost": 1000,
        "cooldown": 15,
        "description": "I'll follow you on Twitter. Yep, like for real.",
        "preview": "https://cdn.streamelements.com/uploads/1775ec6f-d310-4b18-a85e-79530b094445.png",
        "public": false,
        "alert": {
            "enabled": true,
            "audio": {
                "volume": 0.5,
                "src": null
            },
            "graphics": {
                "duration": 8
            }
        },
        "userInput": [
            "Your Twitter Name"
        ],
        "quantity": {
            "total": -1
        },
        "bot": {
            "enabled": true,
            "identifier": "twitter_follow"
        }
    },
    {
        "_id": "59bd824be626b5ee20a5ecfa",
        "updatedAt": "2017-09-10T22:23:49.098Z",
        "createdAt": "2017-09-10T22:23:49.098Z",
        "_user": "59bd7a5cad43c8ec2fbae2e5",
        "enabled": true,
        "featured": false,
        "name": "Twitch Shoutout",
        "type": "perk",
        "accessLevel": 100,
        "cost": 200,
        "cooldown": 15,
        "description": "I'll give your twitch channel a shout out on social media!",
        "preview": "https://cdn.streamelements.com/uploads/1775ec6f-d310-4b18-a85e-79530b094445.png",
        "public": false,
        "alert": {
            "enabled": true,
            "audio": {
                "volume": 0.5,
                "src": null
            },
            "graphics": {
                "duration": 8
            }
        },
        "userInput": [
            "Your Twitch Channel"
        ],
        "quantity": {
            "total": -1
        },
        "bot": {
            "enabled": true,
            "identifier": "twitch_shoutout"
        }
    }
]
```


## `PUT /store/:channel/items/:itemid`
:key: Requires authentication  

Change a store items details.


### Example Request  
```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-H 'content-type: applicaiton/json' \
-X PUT -d'{
  "name": "Twitch Shoutout",
  "description": "I will give your twitch channel a shout out on social media!",
  "enabled": false,
  "cost": 200,
  "cooldown": 15
}' https://api.streamelements.com/kappa/v1/store/:channel/items/:itemid
```


### Example Response

```json
{
    "_id": "59bd824be626b5ee20a5ecfa",
    "updatedAt": "2017-09-16T20:16:16.376Z",
    "createdAt": "2017-09-10T22:22:32.096Z",
    "_user": "59bd7a5cad43c8ec2fbae2e5",
    "enabled": false,
    "featured": false,
    "name": "Twitch Shoutout",
    "type": "perk",
    "accessLevel": 100,
    "cost": 200,
    "cooldown": 15,
    "description": "I will give your twitch channel a shout out on social media!",
    "preview": "https://cdn.streamelements.com/uploads/1775ec6f-d310-4b18-a85e-79530b094445.png",
    "public": false,
    "alert": {
        "enabled": true,
        "audio": {
            "volume": 0.5,
            "src": null
        },
        "graphics": {
            "duration": 8
        }
    },
    "userInput": [
        "Your Twitter Name"
    ],
    "quantity": {
        "total": -1
    },
    "bot": {
        "enabled": true,
        "identifier": "twitter_follow"
    }
}
```


## `POST /store/:channel/items`
:key: Requires authentication  

Create a new store item.


### Example Request  
```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-H 'content-type: applicaiton/json' \
-X POST -d'{
	"name": "TestShoutout",
	"description": "This is a new shoutout test!",
	"enabled": true,
	"type": "perk",
	"accessLevel": 100,
	"cost": 100,
	"cooldown": 15,
	"preview": "https://cdn.streamelements.com/uploads/1775ec6f-d310-4b18-a85e-79530b094445.png",
	"alert": {
        "enabled": true,
        "audio": {
            "volume": 0.5,
            "src": null
        },
        "graphics": {
            "duration": 8
        }
    },
    "userInput": [
        "Your Twitter Name"
    ],
    "quantity": {
        "total": -1
    },
    "bot": {
        "enabled": true,
        "identifier": "testshoutout"
    }
}' https://api.streamelements.com/kappa/v1/store/:channel/items
```


### Example Response

```json
{
    "_id": "59bd824be626b5ee20a5ecfa",
    "updatedAt": "2017-09-16T20:16:16.376Z",
    "createdAt": "2017-09-10T22:22:32.096Z",
    "_user": "59bd7a5cad43c8ec2fbae2e5",
    "enabled": false,
    "featured": false,
    "name": "Twitch Shoutout",
    "type": "perk",
    "accessLevel": 100,
    "cost": 200,
    "cooldown": 15,
    "description": "I will give your twitch channel a shout out on social media!",
    "preview": "https://cdn.streamelements.com/uploads/1775ec6f-d310-4b18-a85e-79530b094445.png",
    "public": false,
    "alert": {
        "enabled": true,
        "audio": {
            "volume": 0.5,
            "src": null
        },
        "graphics": {
            "duration": 8
        }
    },
    "userInput": [
        "Your Twitter Name"
    ],
    "quantity": {
        "total": -1
    },
    "bot": {
        "enabled": true,
        "identifier": "twitter_follow"
    }
}
```
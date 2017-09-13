# Sessions

## Overview
|Endpoints|Description|
|----------|----------|
|[`GET /sessions`](#get-sessions)| Returns an object with information about your stream session |


## `GET /sessions`
:key: Requires authentication  

Returns an object with information about your stream session.

### Example Request  
```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/sessions
```
  
  
### Example Response

```json
{
    "_id": "59b946aa19dff05ba6d3f676",
    "updatedAt": "2017-09-10T06:48:22.446Z",
    "createdAt": "2017-09-10T06:48:21.961Z",
    "_user": "59b946aac3df40c1a288e440",
    "data": {
        "cheer-alltime-top-donator": {
            "amount": 0,
            "name": ""
        },
        "cheer-monthly-top-donator": {
            "amount": 0,
            "name": ""
        },
        "cheer-weekly-top-donator": {
            "amount": 0,
            "name": ""
        },
        "cheer-session-top-donator": {
            "amount": 0,
            "name": ""
        },
        "cheer-alltime-top-donation": {
            "amount": 0,
            "name": ""
        },
        "cheer-monthly-top-donation": {
            "amount": 0,
            "name": ""
        },
        "cheer-weekly-top-donation": {
            "amount": 0,
            "name": ""
        },
        "cheer-session-top-donation": {
            "amount": 0,
            "name": ""
        },
        "cheer-recent": [],
        "cheer-latest": {
            "message": "",
            "amount": 0,
            "name": ""
        },
        "cheer-goal": {
            "amount": 0
        },
        "cheer-count": {
            "count": 0
        },
        "cheer-total": {
            "amount": 0
        },
        "cheer-month": {
            "amount": 0
        },
        "cheer-week": {
            "amount": 0
        },
        "cheer-session": {
            "amount": 0
        },
        "host-recent": [],
        "host-latest": {
            "amount": 0,
            "name": "HostingUser1"
        },
        "tip-goal": {
            "amount": 10
        },
        "tip-count": {
            "count": 0
        },
        "tip-total": {
            "amount": 10
        },
        "tip-month": {
            "amount": 10
        },
        "tip-week": {
            "amount": 0
        },
        "tip-session": {
            "amount": 0
        },
        "tip-alltime-top-donator": {
            "amount": 82,
            "name": "User1"
        },
        "tip-monthly-top-donator": {
            "amount": 82,
            "name": "User1"
        },
        "tip-weekly-top-donator": {
            "amount": 0,
            "name": ""
        },
        "tip-session-top-donator": {
            "amount": 0,
            "name": ""
        },
        "tip-alltime-top-donation": {
            "amount": 82,
            "name": "User1"
        },
        "tip-monthly-top-donation": {
            "amount": 82,
            "name": "User1"
        },
        "tip-weekly-top-donation": {
            "amount": 0,
            "name": ""
        },
        "tip-session-top-donation": {
            "amount": 0,
            "name": ""
        },
        "tip-recent": [
            {
                "_id": "59b946aa7a4de7141b14a2dd",
                "amount": 82,
                "name": "User1"
            },
            {
                "_id": "59b946aa1eb34da9188dce35",
                "amount": 5,
                "name": "User2"
            }
        ],
        "tip-latest": {
            "message": "User1 Tip Message Supplied Here",
            "amount": 82,
            "name": "User1"
        },
        "subscriber-total": {
            "count": 0
        },
        "subscriber-goal": {
            "amount": 0
        },
        "subscriber-month": {
            "count": 0
        },
        "subscriber-week": {
            "count": 0
        },
        "subscriber-session": {
            "count": 0
        },
        "subscriber-recent": [],
        "subscriber-latest": {
            "message": "",
            "tier": "",
            "amount": 0,
            "name": ""
        },
        "follower-total": {
            "count": 45
        },
        "follower-goal": {
            "amount": 45
        },
        "follower-month": {
            "count": 33
        },
        "follower-week": {
            "count": 2
        },
        "follower-session": {
            "count": 0
        },
        "follower-recent": [
            {
                "createdAt": "2017-09-09T03:29:00.139Z",
                "name": "User1"
            },
            {
                "createdAt": "2017-09-08T05:22:02.503Z",
                "name": "User2"
            }
        ],
        "follower-latest": {
            "name": "User1"
        }
    },
    "lastReset": "2017-09-10T06:48:21.916Z"
}
```
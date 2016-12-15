# Points


## `GET /points`
🔒 Requires authentication  

Returns a list of all channels where you have points.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/points
```

### Example Response

```json
[
    {
        "channel": {
            "username": "97jameslp",
            "display_name": "97JamesLP",
            "avatar": "https://static-cdn.jtvnw.net/jtv_user_pictures/97jameslp-profile_image-4104f9921065a118-300x300.jpeg",
            "header_image": "https://s3.amazonaws.com/streamelements-uploads-dev/testing/2016-07-04_23-59-51.png"
        },
        "currencyName": "points",
        "points": 5,
        "pointsAlltime": 5,
        "rank": 507
    },
    {
        "channel": {
            "username": "abathur1613",
            "display_name": "Abathur1613",
            "avatar": "https://static-cdn.jtvnw.net/jtv_user_pictures/abathur1613-profile_image-62a40e3a8afbb3e6-300x300.png",
            "header_image": "https://s3.amazonaws.com/streamelements-uploads-dev/testing/2016-07-04_23-59-51.png"
        },
        "currencyName": "points",
        "points": 5,
        "pointsAlltime": 5,
        "rank": 1786
    },
    {
        "channel": {
            "username": "alexafka",
            "display_name": "alexafka",
            "avatar": "https://static-cdn.jtvnw.net/jtv_user_pictures/xarth/404_user_150x150.png",
            "header_image": "https://s3.amazonaws.com/streamelements-uploads-dev/testing/2016-07-04_23-59-51.png"
        },
        "currencyName": "points",
        "points": 0,
        "pointsAlltime": 0,
        "rank": 0
    }
]
```

## `PUT /points/:username/:amount`
🔒 Requires authentication  

Adds or removes points from a user

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X PUT https://api.streamelements.com/kappa/v1/points/nuuls/100
```

### Example Response

```json
{
    "amount": 123,
    "channel": "stylerdev",
    "message": "Added 100 points to user nuuls in channel stylerdev",
    "newAmount": 420,
    "username": "nuuls"
}
```

## `DELETE /points/:username`
🔒 Requires authentication  

Reset a users points.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X DELETE https://api.streamelements.com/kappa/v1/points/nuuls
```

### Example Response

```json
{
    "channel": "stylerdev",
    "message": "nuuls was sucesfully reset in channel stylerdev",
    "username": "nuuls"
}
```

## `GET /points/:channel/alltime/:amount`

Returns a list of alltime top *X* users in the channel.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/points/nuuls/alltime/10
```

### Example Response

```json
{
    "_total": 1018,
    "users": [
        {
            "username": "ardbug",
            "points": 275
        },
        {
            "username": "steevdave",
            "points": 204
        },
        {
            "username": "frost_bytes",
            "points": 204
        },
        {
            "username": "revelati0nz",
            "points": 176
        },
        {
            "username": "streamelements",
            "points": 154
        },
        {
            "username": "girlvsdumb",
            "points": 154
        },
        {
            "username": "senorcristos",
            "points": 150
        },
        {
            "username": "leishaaa321",
            "points": 148
        },
        {
            "username": "fess_unreal",
            "points": 142
        },
        {
            "username": "piratekxng",
            "points": 136
        }
    ]
}
```

## `GET /points/:channel/top/:amount`

Returns a list of top *X* users in the channel.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/points/nuuls/top/10
```

### Example Response

```json
{
    "_total": 1018,
    "users": [
        {
            "username": "ardbug",
            "points": 275
        },
        {
            "username": "steevdave",
            "points": 204
        },
        {
            "username": "frost_bytes",
            "points": 204
        },
        {
            "username": "revelati0nz",
            "points": 176
        },
        {
            "username": "streamelements",
            "points": 154
        },
        {
            "username": "girlvsdumb",
            "points": 154
        },
        {
            "username": "senorcristos",
            "points": 150
        },
        {
            "username": "leishaaa321",
            "points": 148
        },
        {
            "username": "fess_unreal",
            "points": 142
        },
        {
            "username": "piratekxng",
            "points": 136
        }
    ]
}
```

## `GET /points/:channel/:username`

Get points for a user in a channel

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/points/stylerdev/nuuls
```

### Example Response

```json
{
    "channel": "stylerdev",
    "username": "nuuls",
    "points": 274380,
    "pointsAlltime": 3160,
    "rank": 23
}
```


## `GET /points/:channel/:username/rank`

Get the rank for a user in a channel.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/points/stylerdev/nuuls
```

### Example Response

```json
{
    "username": "stylerdev",
    "rank": 23
}
```
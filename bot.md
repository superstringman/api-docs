# Bot


## `GET /bot`

Returns an object with information about the bot.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/bot
```

### Example Response

```json
{
  "bot": {
    "_user": "577c1d1b4d85915c2c121591",
    "muted": false,
    "joined": true,
    "name": "streamelements",
    "enabled": true
  },
  "stats": {
    "commands": 0,
    "messages": 1,
    "timeouts": 0
  }
}
```

## `GET /bot/logs`

Returns the bots action log. These logs include command updates.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/bot
```

### Example Response

```json
[
  {
    "type": "command",
    "username": "test-user",
    "message": "added command with trigger lul",
    "_id": "57e86eced4044679cf99d774",
    "createdAt": "2016-09-26T00:41:50.108Z"
  },
  {
    "type": "command",
    "username": "test-user",
    "message": "added command with trigger feelsgoodman",
    "_id": "57f962671faa243d4d8e1913",
    "createdAt": "2016-10-08T21:17:27.664Z"
  },
  {
    "type": "command",
    "username": "test-user",
    "message": "added command with trigger toodank",
    "_id": "57f962721faa243d4d8e1915",
    "createdAt": "2016-10-08T21:17:38.307Z"
  },
  {
    "type": "command",
    "username": "test-user",
    "message": "added command with trigger memes",
    "_id": "57f962791faa243d4d8e1917",
    "createdAt": "2016-10-08T21:17:45.496Z"
  }
]
```

## `POST /bot/:action`

### Parameters

|Action|Description|
|------|-----------|
|`join`|Makes the bot join the current user's channel.|
|`part`|Makes the bot part the current user's channel.|
|`mute`|Mutes the bot in the current user's channel.|
|`unmute`|Unmutes the bot in the current user's channel.|

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X POST https://api.streamelements.com/kappa/v1/bot/mute
```

### Example Response

```json
{
  "status": 200,
  "channel": "stylerdev",
  "message": "Muted the bot in your channel"
}
```

## `POST /bot/say`

Makes the bot send a message in current user's the channel.

### Parameters

|Parameter|Type|Required|Description|
|------|------|------|-----------|
|`message`|String|Required|The message to be send in chat.|

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X POST https://api.streamelements.com/kappa/v1/bot/say \
-D '{"message": "Keepo"}'
```

### Example Response

```json
{
  "status": 200,
  "channel": "stylerdev",
  "message": "Keepo"
}
```

## `GET /bot/levels`

Returns an array of users with levels in your channel.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/bot/levels
```

### Example Response

```json
[
  {
    "username": "memes",
    "lastActive": "2016-12-01T10:40:27.237388766Z",
    "moderator": true,
    "subscriber": true,
    "level": 1000
  },
  {
    "username": "kkaper",
    "lastActive": "2016-12-01T11:50:31.32667705Z",
    "moderator": true,
    "subscriber": true,
    "level": 1000
  },
  {
    "username": "tooDank",
    "lastActive": "2016-12-01T10:22:37.336637238Z",
    "moderator": true,
    "subscriber": true,
    "level": 500
  },
  {
    "username": "lul",
    "lastActive": "2016-11-27T10:42:56.804385019Z",
    "moderator": true,
    "subscriber": true,
    "level": 500
  },
  {
    "username": "user",
    "lastActive": "2016-10-31T05:52:17.131936612Z",
    "moderator": true,
    "subscriber": true,
    "level": 500
  }
]
```

## User Level

|Userlevels|Level|Description|
|------|------|-----------|
|`Broadcaster`|1500|Channel Owner|
|`Super Moderator`|1000|Trustworthy Moderators or Managers|
|`Moderator`|500|Channel Moderator|
|`Regulars`|300|Regulars|
|`Subscriber`|250|Channel Subscriber|
|`Everyone`|100|Normal user (Default)|

## `POST /bot/levels`

Create a new permission for the current channel

### Parameters

|Parameter|Type|Required|Description|
|------|------|------|-----------|
|`username`|String|Required|Pass the username|
|`level`|Enum|Required|The <a href="#user-level">user levels</a> required to use the command.|


### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X POST https://api.streamelements.com/kappa/v1/bot/levels \
-D '{"username": "streamelements", "level": 1000}'
```

### Example Response

```json
{
  "username": "streamelements",
  "lastActive": "0001-01-01T00:00:00Z",
  "moderator": false,
  "subscriber": false,
  "level": 1000
}
```

### Error

```json
{
  "statusCode": 400,
  "error": "Bad Request",
  "message": "Validation Error",
  "details": [
    {
      "path": "username",
      "message": "\"username\" must be a string"
    },
    {
      "path": "level",
      "message": "\"level\" must be a number"
    }
  ]
}
```

## `DELETE /bot/levels/:username`

### Parameters

|Parameter|Type|Required|Description|
|------|------|------|-----------|
|`username`|String|Required|Pass the username|

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X DELETE https://api.streamelements.com/kappa/v1/bot/levels/streamelements
```

### Example Response

```json
{
  "statusCode": 201,
  "message": "Removed user streamelements"
}
```
### Errors

```json
{
  "statusCode": 404,
  "error": "Not Found"
}
```

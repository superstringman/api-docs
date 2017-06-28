# Bot


## `GET /bot`
🔒 Requires authentication  

Returns an object with information about the bot.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/bot
```

### Example Response
🌏
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

Create a new permission for the current channel.

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

### Error

```json
{
  "statusCode": 404,
  "error": "Not Found"
}
```

# Commands

## Overview

|Endpoints|Description|
|----------|----------|
|[`GET /bot/commands`](#get-botcommands)|Returns an array of commands|
|[`GET /bot/commands/:id`](#get-botcommandsid)|Returns a single command|
|[`POST /bot/commands`](#post-botcommands)|Create a new bot command|
|[`PUT /bot/commands/:id`](#put-botcommandsid)|Update the command by passing the id|
|[`DELETE /bot/commands/:id`](#delete-botcommandsid)|Delete a command by the id|

### Properties

|Fields|Type|Description|
|------|----|-----------|
|`enabled`|Boolean|The state of the command ( default true )|
|`command `|String|The command’s unique name|
|`reply`|String|The message that will get sent once the command is called|
|`accessLevel`|Number|The <a href="#user-level">user levels</a> required to use the command ( default 100 )|
|`type`|String|How should the bot send the message by "say", "reply" or "whisper" ( default "say" )|
|`cost`|Number|The price of redeeming this command ( default 0, minimum 0, maximum 100000 )|
|`cooldown`|Object|Contains information about the command|
|`cooldown.global`|Number|The amount of seconds between each command to prevent spam ( default 5 )|
|`cooldown.user`|Number|The amount of seconds a user has to wait on calling that command again to prevent spam ( default 15 )|
|`aliases`|String[]|Create an alias that will trigger the same command ( maximum 5 )|

## `GET /bot/commands`

Returns an array of commands.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/bot/commands
```

### Example Response

```json
[
  {
    "_id": "584da59e601791435f483e86",
    "updatedAt": "2016-12-11T19:14:38.370Z",
    "createdAt": "2016-12-11T19:14:38.370Z",
    "_user": "577c1d1b4d85915c2c121591",
    "_username": "streamelements",
    "command": "points",
    "reply": "${user} has ${user.points} ${pointsname}",
    "accessLevel": 100,
    "type": "reply",
    "cost": 0,
    "cooldown": {
      "global": 0,
      "user": 5
    },
    "enabled": true,
    "aliases": []
  },
  {
    "_id": "584da5a4601791435f483e8d",
    "updatedAt": "2016-12-11T19:14:44.760Z",
    "createdAt": "2016-12-11T19:14:44.760Z",
    "_user": "577c1d1b4d85915c2c121591",
    "_username": "streamelements",
    "command": "lastseen",
    "reply": "${user} was last seen ${user.lastseen} ago and last active in Chat ${user.lastactive} ago. His last Message was: ${user.lastmessage}",
    "accessLevel": 100,
    "type": "reply",
    "cost": 0,
    "cooldown": {
      "global": 5,
      "user": 10
    },
    "enabled": true,
    "aliases": [
      "lastmessage",
      "lastactive"
    ]
  },
  {
    "_id": "584da5b4601791435f483e92",
    "updatedAt": "2016-12-11T19:15:00.149Z",
    "createdAt": "2016-12-11T19:15:00.149Z",
    "_user": "577c1d1b4d85915c2c121591",
    "_username": "streamelements",
    "command": "followers",
    "reply": "We currently have ${channel.followers} Followers PogChamp",
    "accessLevel": 100,
    "type": "reply",
    "cost": 0,
    "cooldown": {
      "global": 5,
      "user": 10
    },
    "enabled": true,
    "aliases": []
  }
]
```

## `GET /bot/commands/:id`

Returns a single command.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/bot/commands/584da5a4601791435f483e8d
```

### Example Response

```json
{
    "_id": "584da5a4601791435f483e8d",
    "updatedAt": "2016-12-11T19:14:44.760Z",
    "createdAt": "2016-12-11T19:14:44.760Z",
    "_user": "577c1d1b4d85915c2c121591",
    "_username": "streamelements",
    "command": "lastseen",
    "reply": "${user} was last seen ${user.lastseen} ago and last active in Chat ${user.lastactive} ago. His last Message was: ${user.lastmessage}",
    "accessLevel": 100,
    "type": "reply",
    "cost": 0,
    "cooldown": {
      "global": 5,
      "user": 10
    },
    "enabled": true,
    "aliases": [
      "lastmessage",
      "lastactive"
    ]
}
```

### Error

```json
{
  "statusCode": 404,
  "error": "Not Found"
}
```

## `POST /bot/commands`

Create a new bot command.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X POST https://api.streamelements.com/kappa/v1/bot/commands \
-D '{ "command": "points", "reply": "${user} has ${user.points} ${pointsname}" }'
```

### Example Response

```json
{
  "updatedAt": "2016-12-11T20:47:45.975Z",
  "createdAt": "2016-12-11T20:47:45.975Z",
  "_user": "577c1d1b4d85915c2c121591",
  "_username": "streamelements",
  "command": "points",
  "reply": "${user} has ${user.points} ${pointsname}",
  "_id": "584dbb71601791435f4843e1",
  "accessLevel": 100,
  "type": "say",
  "cost": 0,
  "cooldown": {
    "global": 5,
    "user": 15
  },
  "enabled": true,
  "aliases": []
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
      "path": "command",
      "message": "\"command\" is required"
    },
    {
      "path": "reply",
      "message": "\"reply\" is required"
    }
  ]
}
```

If the command already exists.

```json
{
  "statusCode": 409,
  "error": "Conflict",
  "message": "Command points already exists"
}
```

## `PUT /bot/commands/:id`

Update the command by passing the id.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X PUT https://api.streamelements.com/kappa/v1/bot/commands/584dbb71601791435f4843e1 \
-D '{ "command": "points", "reply": "${user} has ${user.points} ${pointsname}", "accessLevel" : "500"}'
```

### Parameters

|Parameter|Type|Required|Description|
|------|------|------|-----------|
|`command`|String|Required|The command’s unique name|
|`reply`|String|Required|The message that will get sent once the command is called.|

### Example Response

```json
{
  "_id": "584dbb71601791435f4843e1",
  "updatedAt": "2016-12-11T21:36:49.145Z",
  "createdAt": "2016-12-11T20:47:45.975Z",
  "_user": "577c1d1b4d85915c2c121591",
  "_username": "streamelements",
  "command": "points",
  "reply": "${user} has ${user.points} ${pointsname}",
  "accessLevel": 500,
  "type": "say",
  "cost": 0,
  "cooldown": {
    "global": 5,
    "user": 15
  },
  "enabled": true,
  "aliases": []
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
      "path": "command",
      "message": "\"command\" is required"
    }
  ]
}
```

## `DELETE /bot/commands/:id`

Delete a command by the id.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X DELETE https://api.streamelements.com/kappa/v1/bot/commands/584dbb71601791435f4843e1
```

### Example Response

```json
{
  "_id": "584dbb71601791435f4843e1",
  "updatedAt": "2016-12-11T21:51:43.368Z",
  "createdAt": "2016-12-11T21:51:43.368Z",
  "_user": "577c1d1b4d85915c2c121591",
  "_username": "streamelements",
  "command": "points",
  "reply": "${user} has ${user.points} ${pointsname}",
  "accessLevel": 500,
  "type": "say",
  "cost": 0,
  "cooldown": {
    "global": 5,
    "user": 15
  },
  "enabled": true,
  "aliases": []
} 
```

### Error

```json
{
  "statusCode": 404,
  "error": "Not Found"
}
```

# Timers

## Overview
|Endpoints|Description|
|----------|----------|
|[`GET /bot/timers`](#get-bottimers)|Returns an array of timers|
|[`GET /bot/timers/:id`](#get-bottimersid)|Returns a single timer|
|[`PUT /bot/timers/:id`](#put-bottimersid)|Update a single timer|
|[`POST /bot/timers`](#post-bottimers)|Create a new timer|
|[`DELETE /bot/timers/:id`](#delete-bottimersid)|Delete a single timer|

### Properties

|Fields|Type|Description|
|------|------|------|
|`enabled`|Boolean|The state of the timer ( default true )|
|`message `|String|The response when the timer is triggered|
|`name`|String|The name of the timer|
|`chatLines`|Number|Minimum lines between the last timer and this timer ( default 0, minimum 0, maximum 5000 )|
|`online`|Object|Contains information about the online timer|
|`online.enabled`|Number|The state of the online timer ( default true )|
|`online.interval`|Number|How frequently in minutes do you want this timer to appear in the chat ( default 3, minimum 1, maximum 120 )|
|`offline`|Object|Contains information about the offline timer|
|`offline.enabled`|Number|The state of the offline timer ( default true )|
|`offline.interval`|Number|How frequently in minutes do you want this timer to appear in the chat ( default 3, minimum 1, maximum 120 )|

## `GET /bot/timers`

Returns an array of timers.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/bot/timers
```

### Example Response

```json
[
  {
    "_id": "583f065112c67b3c01b96d33",
    "updatedAt": "2016-11-30T17:03:13.956Z",
    "createdAt": "2016-11-30T17:03:13.956Z",
    "_user": "577c1d1b4d85915c2c121591",
    "_username": "streamelements",
    "name": "link",
    "message": "/me check out the commands https://streamelements.com/streamelements/commands",
    "chatLines": 5,
    "offline": {
      "interval": 30,
      "enabled": true
    },
    "online": {
      "interval": 5,
      "enabled": true
    },
    "enabled": true
  },
  {
    "_id": "58505d1a18e3a7493d17f26c",
    "updatedAt": "2016-12-13T20:42:02.888Z",
    "createdAt": "2016-12-13T20:42:02.888Z",
    "_user": "577c1d1b4d85915c2c121591",
    "_username": "streamelements",
    "name": "leaderboard",
    "message": "/me check out the leaderboard https://streamelements.com/streamelements/leaderboard",
    "chatLines": 8,
    "offline": {
      "interval": 2,
      "enabled": true
    },
    "online": {
      "interval": 5,
      "enabled": true
    },
    "enabled": true
  }
]
```

## `GET /bot/timers/:id`

Returns a single timer.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/bot/timers/58505d1a18e3a7493d17f26c 
```

### Example Response

```json
{
  "_id": "58505d1a18e3a7493d17f26c",
  "updatedAt": "2016-12-13T20:42:02.888Z",
  "createdAt": "2016-12-13T20:42:02.888Z",
  "_user": "577c1d1b4d85915c2c121591",
  "_username": "streamelements",
  "name": "leaderboard",
  "message": "/me check out the leaderboard https://streamelements.com/streamelements/leaderboard",
  "chatLines": 8,
  "offline": {
    "interval": 2,
    "enabled": true
  },
  "online": {
    "interval": 5,
    "enabled": true
  },
  "enabled": true
}
```

## `PUT /bot/timers/:id`

Update a single timer.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X PUT https://api.streamelements.com/kappa/v1/bot/timers/583f065112c67b3c01b96d33 \
-D `{"name":"discord","message":"/me link to the discord https://discordapp.com/","chatLines":24}` 
```

```json
{
  "_id": "583f065112c67b3c01b96d33",
  "updatedAt": "2016-12-13T22:03:39.164Z",
  "createdAt": "2016-11-30T17:03:13.956Z",
  "_user": "577c1d1b4d85915c2c121591",
  "_username": "streamelements",
  "name": "discord",
  "message": "/me link to the discord https://discordapp.com/",
  "chatLines": 24,
  "offline": {
    "interval": 30,
    "enabled": true
  },
  "online": {
    "interval": 5,
    "enabled": true
  },
  "enabled": true
}
```

### Errors 

```json
{
  "statusCode": 400,
  "error": "Bad Request",
  "message": "Validation Error",
  "details": [
    {
      "path": "name",
      "message": "\"name\" is required"
    },
    {
      "path": "chatLines",
      "message": "\"chatLines\" is required"
    },
    {
      "path": "message",
      "message": "\"message\" is required"
    }
  ]
} 
```

## `POST /bot/timers`

Create a new timer.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X POST https://api.streamelements.com/kappa/v1/bot/timers \
-D `{"name":"testing","message":"this is a test","chatLines":24,"offline":{"interval":10,"enabled":true},"online":{"interval":32,"enabled":true},"enabled":true}` 
```

### Example Response

```json
{
  "updatedAt": "2016-12-13T21:39:37.955Z",
  "createdAt": "2016-12-13T21:39:37.955Z",
  "_user": "577c1d1b4d85915c2c121591",
  "_username": "streamelements",
  "name": "testing",
  "message": "this is a test",
  "_id": "58506a9918e3a7493d17f45e",
  "chatLines": 24,
  "offline": {
    "interval": 10,
    "enabled": true
  },
  "online": {
    "interval": 32,
    "enabled": true
  },
  "enabled": true
} 
```

### Errors 

```json
{
  "statusCode": 400,
  "error": "Bad Request",
  "message": "Validation Error",
  "details": [
    {
      "path": "name",
      "message": "\"name\" is required"
    },
    {
      "path": "chatLines",
      "message": "\"chatLines\" is required"
    },
    {
      "path": "message",
      "message": "\"message\" is required"
    }
  ]
} 
```

## `DELETE /bot/timers/:id`

Delete a single timer.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X DELETE https://api.streamelements.com/kappa/v1/bot/timers/577c1d1b4d85915c2c121591
```

### Example Response

```json
{
  "statusCode": 201,
  "message": "Timer was deleted"
}
```

### Errors

```json
{
  "statusCode": 404,
  "error": "Not Found"
}
```

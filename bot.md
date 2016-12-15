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
<table>
    <thead>
        <tr>
            <th>Action</th>
            <th width=90%>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>join</code></td>
            <td>Makes the bot join the current user's channel.</td>
        </tr>
        <tr>
            <td><code>part</code></td>
            <td>Makes the bot part the current user's channel.</td>
        </tr>
        <tr>
            <td><code>mute</code></td>
            <td>Mutes the bot in the current user's channel.</td>
        </tr>
        <tr>
            <td><code>unmute</code></td>
            <td>Unmutes the bot in the current user's channel.</td>
        </tr>
    </tbody>
</table>

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
<table>
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Type</th>
            <th>Required</th>
            <th width=90%>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>message</code></td>
            <td>String</td>
            <td>Required</td>
            <td>The message to be send in chat.</td>
        </tr>
    </tbody>
</table>

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
<table>
    <thead>
        <tr>
            <th>Userlevels</th>
            <th>Level</th>
            <th width=70%>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>Broadcaster</code></td>
            <td>1500</td>
            <td>Channel Owner</td>
        </tr>
        <tr>
            <td><code>Super Moderator</code></td>
            <td>1000</td>
            <td>Trustworthy Moderators or Managers</td>
        </tr>
        <tr>
            <td><code>Moderator</code></td>
            <td>500</td>
            <td>Channel Moderator</td>
        </tr>
        <tr>
            <td><code>Regulars</code></td>
            <td>300</td>
            <td>Regulars</td>
        </tr>
        <tr>
            <td><code>Subscriber</code></td>
            <td>250</td>
            <td>Channel Subscriber</td>
        </tr>
        <tr>
            <td><code>Plep</code></td>
            <td>100</td>
            <td>Normal user</td>
        </tr>
    </tbody>
</table>

## `POST /bot/levels`

Create a new permission for the current channel

### Parameters
<table>
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Type</th>
            <th>Required</th>
            <th width=90%>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>username</code></td>
            <td>String</td>
            <td>Required</td>
            <td>Pass the username</td>
        </tr>
        <tr>
            <td><code>level</code></td>
            <td>enum</td>
            <td>Required</td>
            <td>The <a href="#user-level">user levels</a> required to use the command.</td>
        </tr>
    </tbody>
</table>

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
<table>
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Type</th>
            <th>Required</th>
            <th width=90%>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>username</code></td>
            <td>String</td>
            <td>Required</td>
            <td>Pass the username</td>
        </tr>
    </tbody>
</table>


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

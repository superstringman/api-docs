# StreamElements API 1.0 API documentation <img src="https://static-cdn.jtvnw.net/emoticons/v1/25/1.0">

### Base url: [https://api.streamelements.com/kappa/v1](https://api.streamelements.com/kappa/v1)

### Authentication

StreamElements uses the [JWT](https://jwt.io/) standard for authorizing requests to our api.
You can get your very own token right here xd [streamelements.com](https://streamelements.com/dashboard/account/information)

Calling GET kappa/v1/users/me using a jwt
```json
curl https://api.streamelements.com/kappa/v1/users/me \
     -H 'authorization: Bearer JWT-TOKEN'
```

### Errors

StreamElements uses standard HTTP status codes to communicate errors

|Status code|Status text|Description|
|-----------|-----------|-----------|
|200|OK|Everything went as planned|
|400|Bad Request|Something in your header or request body was malformed|
|401|Unauthorized|Necessary credentials were either missing or invalid|
|403|Forbidden|Your credentials are valid but you don’t have access to the requested resource|
|404|Not Found|The object you’re requesting doesn’t exist|
|429|Too Many Requests|You are calling our APIs more frequently than we allow|
|5XX|Server Errors|Something went wrong on our end|

In addition to the status code, the HTTP body of the response will also contain a JSON representation of the error.

```json
{
  "statusCode": 400,
  "error": "Bad Request",
  "message": "Validation Error",
  "details": [
    {
      "path": "username",
      "message": "\"username\" is required"
    },
    {
      "path": "level",
      "message": "\"level\" must be one of [100, 250, 300, 500, 1000, 1500, 2000]"
    }
  ]
}
```

# Ressources
- [Bot](bot.md)
    - [`Commands`](bot.md#commands)
    - [`Filters`](bot.md#filters)
    - [`Timers`](bot.md#timers)
    - [`Modules`](bot.md#modules)

- [`Activities`](activities.md)
- [`Logs`](logs.md)
- [`Tipping`](tipping.md)
- [`Tips`](tips.md)
- [`Uploads`](uploads.md)
- [`Users`](users.md)
- [`Loyalties`](loyalties.md)
- [`Points`](points.md)
- [`Sessions`](sessions.md)
- [`Chatstats`](chatstats.md)

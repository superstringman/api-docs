# StreamElements API 1.0 API documentation <img src="https://static-cdn.jtvnw.net/emoticons/v1/25/1.0">

### Base url: [https://api.streamelements.com/kappa/v1](https://api.streamelements.com/kappa/v1)

### Authentication

StreamElements uses the [JWT](https://jwt.io/) standard for authorizing requests to our api.
You can get your very own token right here xd [streamelements.com](https://streamelements.com/dashboard/account/information)

Calling GET /v1/appusers using a jwt
```json
curl https://api.streamelements.com/v1/users/me \
     -H 'authorization: Bearer YOUR-TOKEN'
```

### Errors

StreamElements uses standard HTTP status codes to communicate errors

<table>
    <thead>
        <tr>
            <th>Status code</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>200	OK</td>
            <td>Everything went as planned.</td>
        </tr>
        <tr>
            <td>400	Bad Request</td>
            <td>Something in your header or request body was malformed.</td>
        </tr>
        <tr>
            <td>401	Unauthorized</td>
            <td>Necessary credentials were either missing or invalid.</td>
        </tr>
        <tr>
            <td>403	Forbidden</td>
            <td>Your credentials are valid but you don’t have access to the requested resource.</td>
        </tr>
        <tr>
            <td>404	Not Found</td>
            <td>The object you’re requesting doesn’t exist.</td>
        </tr>
        <tr>
            <td>429	Too Many Requests</td>
            <td>You are calling our APIs more frequently than we allow.</td>
        </tr>
        <tr>
            <td>500, 502, 503, 504	Server Errors</td>
            <td>Something went wrong on our end. </td>
        </tr>
    </tbody>
</table> 

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
- [Tipping](tipping.md)
- [Tips](tips.md)
- [Uploads](uploads.md)
- [Users](users.md)
- [Loyalties](loyalties.md)
- [Points](points.md)
- [Sessions](sessions.md)
- [Chatstats](chatstats.md)
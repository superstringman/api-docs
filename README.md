# StreamElements API 1.0 API documentation

### Base url: [https://api.streamelements.com/kappa/v1](https://api.streamelements.com/kappa/v1)

### Authentication

StreamElements uses the [JWT](https://jwt.io/) standard for authorizing requests to our api.
You can get your very own token right here xd [streamelements.com](https://streamelements.com/dashboard/account/information)

Calling GET /v1/appusers using a jwt
```json
curl https://api.streamelements.com/kappa/v1/users/me \
     -H 'authorization: Bearer YOUR-TOKEN'
```

### Errors

All error responses are in the following format, delivered with the corresponding status code:

```json
{
    "statusCode": 404,
    "error": "Not Found"
}
```


# Ressources

## [Bot](bot.md)

## [Activities](activities.md)

## [Logs](logs.md)

## [Tipping](tipping.md)

## [Tips](tips.md)

## [Uploads](uploads.md)

## [Users](users.md)

## [Loyalties](loyalties.md)

## [Points](points.md)

## [Sessions](sessions.md)

## [Chatstats](chatstats.md)

## songrequests (soon™)
# Loyalties

## `GET /loyalties`
:key: Requires authentication  
  
Returns an object with information about your loyalties.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/loyalties
```

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
  
Returns an object with information about someones loyalties.

### Example Request

```bash
curl -X GET https://api.streamelements.com/kappa/v1/loyalties/streamelements
```

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
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>name</td>
      <td>name of the currency</td>
    </tr>
    <tr>
      <td>enabled</td>
      <td>if it's enabled in the chat</td>
    </tr>
    <tr>
      <td>amount</td>
      <td>amount of points earned every 10 minutes</td>
    </tr>
    <tr>
      <td>subscriberMultiplier</td>
      <td>what subs get extra (<i>amount</i> * X)</td>
    </tr>
    <tr>
      <td>bonuses: cheer</td>
      <td>bonus on cheer</td>
    </tr>
    <tr>
      <td>bonuses: subscriber</td>
      <td>bonus on subscribe</td>
    </tr>
    <tr>
      <td>bonuses: tip</td>
      <td>bonus on tip</td>
    </tr>
    <tr>
      <td>bonuses: follow</td>
      <td>bonus on follow</td>
    </tr>
  </tbody>
</table>

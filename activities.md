# Activities

## `GET /activities`

Returns a list of activities sorted by *createdAt*.

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/activities
```

```json
[
  {
    "_id": "577c1d1b4d85915c2c121592",
    "_username": "streamelements",
    "type": "follow",
    "data": {
     "username": "random"
    },
    "createdAt": "2016-10-10T19:30:30.625Z"
  },
  {
    "_id": "577c1d1b4d85915c2c121593",
    "_username": "streamelements",
    "type": "subscriber",
    "data": {
      "username": "user",
      "amount": 12,
      "message": "HeyGuys"
    },
    "createdAt": "2016-10-07T11:35:37.479Z"
  }
]
```

## `GET /activities/:id`

Returns a single activity

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/activities/:id
```

```json
{
  "_id": "577c1d1b4d85915c2c121593",
  "_username": "streamelements",
  "type": "subscriber",
  "data": {
    "username": "user",
    "amount": 12,
    "message": "HeyGuys"
  },
  "createdAt": "2016-10-07T11:35:37.479Z"
}
```

<table>
  <thead>
    <tr>
      <th>Type</th>
      <th>Description</th>
      <th>More</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>follow</td>
      <td>When someone follows</td>
      <td></td>
    </tr>
    <tr>
      <td>tip</td>
      <td>When someone tips</td>
      <td><code>data</code> also has <code>amount</code>, <code>currency</code> (soon) and the <code>message</code></td>
    </tr>
    <tr>
      <td>host</td>
      <td>When you get hosted</td>
      <td><code>username</code> is hosting you for <code>amount</code> viewers (soon)</td>
    </tr>
    <tr>
      <td>subscriber</td>
      <td>When someone subscribes</td>
      <td><code>data</code> also has <code>amount</code>(in months) and the <code>message</code></td>
    </tr>
    <tr>
      <td>cheer</td>
      <td>When someone cheers</td>
      <td><code>data</code> also has <code>amount</code>(in bits) and the <code>message</code></td>
    </tr>
  </tbody>
</table>

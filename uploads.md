# Uploads

## Overview
|Endpoints|Description|
|----------|----------|
|[`GET /uploads`](#get-uploads)| Returns a list of uploads to your StreamElements account |


## `GET /uploads`
:key: Requires authentication  

Returns a list of uploads to your StreamElements account.

### Example Request  
```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X GET https://api.streamelements.com/kappa/v1/uploads
```
  
  
### Example Response

```json
[
    {
        "_id": "59b94a4c9256c71c2e3051aa",
        "updatedAt": "2017-08-04T23:46:43.850Z",
        "createdAt": "2017-08-04T23:46:43.850Z",
        "uuid": "b1ac76c7-f73a-4a84-babb-4e6ed686d869deed.png",
        "name": "filename1.png",
        "size": 172599,
        "url": "https://cdn.streamelements.com/uploads/b1ac76c7-f73a-4a84-babb-4e6ed686d869deed.png",
        "type": "image/png"
    },
    {
        "_id": "59b94a4ccd2fefa5c22f2bd7",
        "updatedAt": "2017-08-04T23:49:29.852Z",
        "createdAt": "2017-08-04T23:49:29.852Z",
        "uuid": "85b5e41d-64d1-4c60-8f06-6d1deddb3282.png",
        "name": "backgroundfile.png",
        "size": 232967,
        "url": "https://cdn.streamelements.com/uploads/85b5e41d-64d1-4c60-8f06-6d1deddb3282.png",
        "type": "image/png"
    }
]
```
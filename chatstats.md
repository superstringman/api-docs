# Chatstats

## Overview
|Endpoints|Description|
|----------|----------| 
|[`GET /chatstats`](chatstats.md#get-chatstats)|Returns an object with information about your chatstats settings|
|[`PUT /chatstats`](chatstats.md#get-chatstats)|Updates the object about your chatstats settings|
|[`GET /chatstats/search/:channel`](chatstats.mdx#get-chatstatssearchchannel)|Returns a list of channels that match the search|
|[`GET /chatstats/stats/:channel`](chatstats.md#get-chatstatsstatschannel)|Returns an object with information about chatstats for the channel|
|[`GET /chatstats/top/:amount`](chatstats.md#get-chatstatstopamount)|Returns an object with the top rank channels|
|[`GET /chatstats/emotes/:provider/:emote`](chatstats.md#get-chatstatsemotesprovideremote)|Returns an object with a single emote|
|[`GET /chatstats/:channel`](chatstats.md#get-chatstatschannel)|Returns an object with information about the channel chatstats settings|

### Properties

|Fields|Type|Description|
|------|----|-----------|
|_username|String|Channel's name|
|emoteflow|Boolean|Whether the emote flow is enabled ( default: true )|
|total_messages|Boolean|Whether the total messages is enabled ( default: true )|
|messages_per_second|Boolean|Whether the messages per second is enabled ( default: true )|
|twitchchat|Boolean|Whether the twitch chat is enabled ( default: false )|
|ignored_chatters|String|Banned Chatters|
|stats|Object|Contains information about the stats|
|stats.top_chatters|Number|The number of top chatters being displayed ( default 70, minimum 10, maximum 150 )|
|stats.twitch|Number|The number of twitch emotes being displayed ( default 35, minimum 10, maximum 150 )|
|stats.bttv|Number|The number of bttv emotes being displayed ( default 35, minimum 10, maximum 150 )|
|stats.hashtags|Number|The number of hashtags being displayed ( default 35, minimum 10, maximum 150 )|
|stats.commands|Number|The number of commands being displayed ( default 35, minimum 10, maximum 150 )|


## `GET /chatstats`
🔒 Requires authentication  

Returns an object with information about your chatstats settings

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X https://api.streamelements.com/kappa/v1/chatstats
```

### Example Response

```json 
{
  "_id": "580103c2439513086263180a",
  "updatedAt": "2017-01-02T16:31:42.414Z",
  "createdAt": "2016-10-14T16:11:46.097Z",
  "_username": "streamelements",
  "__v": 0,
  "stats": {
    "commands": 25,
    "hashtags": 30,
    "bttv": 30,
    "twitch": 30,
    "top_chatters": 100
  },
  "twitchchat": false,
  "ignored_chatters": [],
  "messages_per_second": true,
  "total_messages": true,
  "emoteflow": true
}
```


### Error

```json
{
  "statusCode": 404,
  "error": "Not Found"
}
```

### Parameters

|Parameter|Type|Required|Description|
|------|------|------|-----------|
|_username|String|Optional|Channel's name|
|emoteflow|Boolean|Optional|Whether the emote flow is enabled ( default: true )|
|total_messages|Boolean|Optional|Whether the total messages is enabled ( default: true )|
|messages_per_second|Boolean|Optional|Whether the messages per second is enabled ( default: true )|
|twitchchat|Boolean|Optional|Whether the twitch chat is enabled ( default: false )|
|ignored_chatters|String|Optional|Banned Chatters ( maximum 30 )|
|stats|Object||Contains information about the stats|
|stats.top_chatters|Number|Optional|The number of top chatters being displayed ( default 70, minimum 10, maximum 150 )|
|stats.twitch|Number|Optional|The number of twitch emotes being displayed ( default 35, minimum 10, maximum 150 )|
|stats.bttv|Number|Optional|The number of bttv emotes being displayed ( default 35, minimum 10, maximum 150 )|
|stats.hashtags|Number|Optional|The number of hashtags being displayed ( default 35, minimum 10, maximum 150 )|
|stats.commands|Number|Optional|The number of commands being displayed ( default 35, minimum 10, maximum 150 )|

## `PUT /chatstats`
🔒 Requires authentication  

Updates the object about your chatstats settings

### Example Request

```bash
curl -H 'Authorization:Bearer JWT-TOKEN' \
-X https://api.streamelements.com/kappa/v1/chatstats \
-D `{ "stats": { "commands": 25, "hashtags": 25, "bttv": 25, "twitch": 25} }`
```

### Example Response

```json 
{
  "_id": "580103c2439513086263180a",
  "updatedAt": "2017-01-02T16:31:42.414Z",
  "createdAt": "2016-10-14T16:11:46.097Z",
  "_username": "streamelements",
  "__v": 0,
  "stats": {
    "commands": 25,
    "hashtags": 25,
    "bttv": 25,
    "twitch": 25,
    "top_chatters": 100
  },
  "twitchchat": false,
  "ignored_chatters": [],
  "messages_per_second": true,
  "total_messages": true,
  "emoteflow": true
}
```

### Error

```json
{
  "statusCode": 404,
  "error": "Not Found"
}
```

## `GET /chatstats/search/:channel`

Returns a list of channels that match the search

### Example Request

```bash
curl https://api.streamelements.com/kappa/v1/chatstats/search/stream
```

### Example Response

```json 
[
  "streamelements",
  "fpmgstreams",
  "silosstreams",
  "pandastreame",
  "rulerstreams",
  "thefearstream",
  "riellstream",
  "streaminc",
  "barcodestreams",
  "seansstream",
  "germenchrestream",
  "mrtuomostream",
  "roustream",
  "ksfstreamer",
  "manostream",
  "streamerhino",
  "elotrixlivestream",
  "brobsonstreams",
  "anynoobstream",
  "agestreaming",
  "phreakstream",
  "ramzay_stream",
  "metalvenomstream",
  "qlowstreamt",
  "guzhestream",
  "kiarastream",
  "krutoy_streamer",
  "thesfwstream",
  "zorsstream",
  "lamastream",
  "totostream",
  "teambrosstream",
  "sissorstream",
  "yolotvstream",
  "streamerhouse",
  "a_couple_streams",
  "laeppastream",
  "streamhouseabq",
  "the_buzz_stream",
  "popebenedictstream",
  "arwyllstream",
  "paragamingstream",
  "disstream",
  "lolinsanitystream",
  "swagybearstream",
  "agar_streamer",
  "gulkostream",
  "killastreamt",
  "adlerstream",
  "thegunstream"
]
```

## `GET /chatstats/stats/:channel`

Returns an object with information about chatstats for the channel

### Example Request

```bash
curl https://api.streamelements.com/kappa/v1/chatstats/stats/streamelements
```

### Example Response

```json
{  
  "status":200,
  "channel":"streamelements",
  "amount":100,
  "chatlines":{  
    "chatters":[  
      {  
        "key":"nuuls",
        "amount":43
      },
      {  
        "key":"streamelements",
        "amount":39
      },
      {  
        "key":"stylerdev",
        "amount":30
      }
    ],
    "total":"160"
  },
  "emotes":{  
    "twitch":[  
      {  
        "key":"133620",
        "amount":15,
        "name":"forsenDeer"
      },
      {  
        "key":"88",
        "amount":12,
        "name":"PogChamp"
      },
      {  
        "key":"25",
        "amount":10,
        "name":"Kappa"
      }
    ],
    "bttv":[  
      {  
        "key":"584b17952b6bd742e58cf072",
        "amount":6,
        "name":"KKona"
      },
      {  
        "key":"567b00c61ddbe1786688a633",
        "amount":6,
        "name":"LUL"
      },
      {  
        "key":"566c9fde65dbbdab32ec053e",
        "amount":4,
        "name":"FeelsGoodMan"
      }
    ]
  },
  "commands":[  
    {  
      "key":"!points",
      "amount":5
    },
    {  
      "key":"!vanish",
      "amount":2
    },
    {  
      "key":"!xd",
      "amount":1
    }
  ],
  "hashtags":[]
}
```

## `GET /chatstats/top/:amount`

Returns an object with the top rank channels

### Example Request

```bash
curl https://api.streamelements.com/kappa/v1/chatstats/top/133620
```

### Example Response

```json 
{  
  "amount":5,
  "channels":[  
    {  
      "key":"#forsenlol",
      "amount":32754459
    },
    {  
      "key":"#sodapoppin",
      "amount":20793501
    },
    {  
      "key":"#reckful",
      "amount":20012253
    },
    {  
      "key":"#twitchplayspokemon",
      "amount":19570558
    },
    {  
      "key":"#nightblue3",
      "amount":18020794
    }
  ]
}
```

## `GET /chatstats/emotes/:provider/:emote`

Returns an object with a single emote


### Parameters

|Provider|Description|
|------|-----------|
|`twitch`|Twitch emotes|
|`bttv`|Better twitch tv emotes|

### Example Request

```bash
curl https://api.streamelements.com/kappa/v1/chatstats/emotes/twitch/88
```

### Example Response

```json 
{
  "id": "88",
  "name": "PogChamp"
}
```

## `GET /chatstats/:channel`

Returns an object with information about the channel chatstats settings

### Example Request

```bash
curl https://api.streamelements.com/kappa/v1/chatstats/streamelements
```

### Example Response

```json 
{  
  "_id":"580103c2439513086263180a",
  "_username":"streamelements",
  "stats":{  
    "commands":25,
    "hashtags":25,
    "bttv":25,
    "twitch":25,
    "top_chatters":100
  },
  "twitchchat":true,
  "ignored_chatters":[],
  "messages_per_second":true,
  "total_messages":true,
  "emoteflow":true
}
```

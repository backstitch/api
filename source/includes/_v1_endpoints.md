# API 1.0 Endpoints

```ruby
require 'rest_client'

response = RestClient.get 'https://api.backstit.ch/v1/topic/details.json', :params => {:token => '9523280292F046269CD4C2F8C'}
```

<!-- ```python
import urllib
import urllib2

url = 'https://api.backstit.ch/v1/topic/details.json'
params = {'token': '9523280292F046269CD4C2F8C'}
data = urllib.urlencode(params)
req = urllib2.Request(url, data)
urllib2.urlopen(req)
``` -->

```shell
# GET https://api.backstit.ch/v1/topic/details.json?token={topic_token}
curl https://api.backstit.ch/v1/topic/details.json \
  -d 'token=9523280292F046269CD4C2F8C'
```
> Make sure to replace `9523280292F046269CD4C2F8C` with your topic's token.

All API 1.0 requests use the base url of `https://api.backstit.ch/v1/topic` and authenticate by passing the topic's token as query a parameter.

<aside class="success">
Try upgrading to latest API 2.0 - now allows for building and maintaing topics through REST!
</aside>

## Get Topic Details

```ruby
require 'rest_client'

response = RestClient.get 'https://api.backstit.ch/v1/topic/details.json', :params => {:token => '9523280292F046269CD4C2F8C'}
```

<!-- ```python
import urllib
import urllib2

url = 'https://api.backstit.ch/v1/topic/details.json'
params = {'token': '9523280292F046269CD4C2F8C'}
data = urllib.urlencode(params)
req = urllib2.Request(url, data)
urllib2.urlopen(req)
``` -->

```shell
curl https://api.backstit.ch/v1/topic/details.json \
  -d 'token=9523280292F046269CD4C2F8C'
```

> The above command returns JSON structured like this:

```json
{
  "uid": 821,
  "name": "Detroit",
  "description": "A topic with stories about Detroit.",
  "banner": {
    "url": "http://backstitch-user-uploads.s3.amazonaws.com/production/topic_banners/16427_1400578046.jpg",
    "width": 650,
    "height" :240
  },
  "api_token": "9523280292F046269CD4C2F8C",
  "filters": [
    {
      "uid":56,
      "phrase":"detroit"
    }
  ],
  "feeds": [
    {
      "uid": 13624,
      "name": "CNN",
      "icon": {
        "url": "http://images-backstitch.s3.amazonaws.com/next/service_catalog/cnn_icon.png",
        "width": "16",
        "height": "16"
      },
      "banner": {
        "url": "http://images-backstitch.s3.amazonaws.com/next/service_catalog/cnn_banner.jpg",
        "width": "650",
        "height": "240"
      },
      "service_name": "RSS"
    },
    {
      "uid": 13666,
      "name": "Tweets tagged detroit",
      "icon": {
        "url": "http://images-backstitch.s3.amazonaws.com/next/service_catalog/twitter_icon.png",
        "width": "16",
        "height": "16"
      },
      "banner": {
        "url": "http://images-backstitch.s3.amazonaws.com/next/service_catalog/twitter_banner.jpg",
        "width": "650",
        "height": "240"
      },
      "service_name": "Twitter"
    }
  ]
}
```

This endpoint retrieves details about a topic.

### HTTP Request

`GET https://api.backstit.ch/v1/topic/details.json`

### Query Parameters

| Parameter | Required | Description |
|---------|:-------:|:-----------|
| token | yes | To obtain a token, you must first log into backstitch and from the topic editor include the API add-on.  This will generate a secure token to identify the topic. |

### Returns

| Field | Data Type | Description |
|---------|:-------:|:-----------|
| uid | integer | A unique identifier for the topic |
| name | string | The name given to the topic |
| description | string | An optional description of the topic |
| banner | object | The topic's displayed banner image if one was uploaded |
| api_token | string | The topic's api token |
| filters | array | A list of global keyword filters set on the topic |
| feeds | array | A list of included feeds |

## Fetch Topic Results

```ruby
require 'rest_client'

response = RestClient.get 'https://api.backstit.ch/v1/topic/fetch.json', :params => {:token => '9523280292F046269CD4C2F8C'}
```

<!-- ```python
import urllib
import urllib2

url = 'https://api.backstit.ch/v1/topic/fetch.json'
params = {'token': '9523280292F046269CD4C2F8C'}
data = urllib.urlencode(params)
req = urllib2.Request(url, data)
urllib2.urlopen(req)
``` -->

```shell
curl https://api.backstit.ch/v1/topic/fetch.json \
  -d "token=9523280292F046269CD4C2F8C"
```

> The above command returns JSON structured like this:

```json
[{
  "id": "2ee995b07cb201323db11aa32735a1a3",
  "type": "article",
  "title": "Renderings Revealed: Glass-Enclosed Restaurant & Patio Planned Downtown",
  "description": "Townhouse already announced plans for a new downtown Detroit location, but Eater Detroit has revealed that the Birmingham-based restaurant aspires to go beyond simply filling an empty storefront. Complete with a retractable roof, Townhouse Detroit plans to build a...",
  "full_text": "<div><p>[McIntosh Poris/Townhouse]  </p><p><strong>Townhouse</strong> already <a href=\"http://detroit.eater.com/2014/11/3/7148533/birminghams-townhouse-restaurant-is-headed-for-detroit\">announced</a> plans for a new downtown Detroit location, but <a href=\"http://detroit.eater.com/2015/1/8/7510471/townhouse-plans-greenhouse-style-dining-room-for-detroit-and-open-air\">Eater Detroit</a> has revealed that the Birmingham-based restaurant aspires to go beyond simply filling an empty storefront. Complete with a retractable roof, Townhouse Detroit plans to build a <strong>greenhouse-like dining room</strong> right next to One Detroit Center with seating for 120.</div>",
  "plain_text": "Townhouse already announced plans for a new downtown Detroit location, but Eater Detroit has revealed that the Birmingham-based restaurant aspires to go beyond simply filling an empty storefront. Complete with a retractable roof, Townhouse Detroit plans to build a greenhouse-like dining room right next to One Detroit Center with seating for 120.",
  "author": {
    "name": "Paul Beshouri"
  },
  "published_at": "2015-01-12T17:42:11Z",
  "images": {
    "thumbnail": {
      "url": null,
      "width": null,
      "height": null
    },
    "full_size": {
      "url": "http://detroit.curbed.com/uploads/townhouse1-thumb.jpg",
      "width": null,
      "height": null
    },
    "other": []
  },
  "source": {
    "id": null,
    "name": null,
    "description": null,
    "url": null,
    "icon": {
      "url": null,
      "width": null,
      "height": null
    }
  },
  "origin": {
    "id": null,
    "name": "Curbed Detroit",
    "url": "http://detroit.curbed.com/archives/2015/01/glassenclosed-restaurant-patio-planned-downtown.php",
    "icon": {
      "url": "http://curbed.com/favicon.ico",
      "width": 16,
      "height": 16
    }
  }
}]
```

This endpoint fetches the latest results from the topic.  All results are in descending order by the date that the content was originally published.

### HTTP Request

`GET https://api.backstit.ch/v1/topic/fetch.json`

### Query Parameters

| Parameter | Required | Default | Description |
|---------|:-------:|:-------:|:-----------|
| token | yes | | To obtain a token, you must first log into backstitch and from the topic editor include the API add-on.  This will generate a secure token to identify the topic. |
| count | no | 20 | The number of results to return per call, up to a maximum of 50. |
| skip | no | 0 | The number of results to skip per call, to be used for paging. |

### Returns

An array of results.  Consult the [Result Type Dictionary](#result-type-dictionary) for field descriptions.

## Filter Topic Results

```ruby
require 'rest_client'

response = RestClient.get 'https://api.backstit.ch/v1/topic/fetch.json', :params => {:token => '9523280292F046269CD4C2F8C', :term => 'restaurants'}
```

<!-- ```python
import urllib
import urllib2

url = 'https://api.backstit.ch/v1/topic/fetch.json'
params = {'token': '9523280292F046269CD4C2F8C', 'term': 'restaurants'}
data = urllib.urlencode(params)
req = urllib2.Request(url, data)
urllib2.urlopen(req)
``` -->

```shell
curl https://api.backstit.ch/v1/topic/fetch.json \
  -d "token=9523280292F046269CD4C2F8C&term=restaurants"
```

> The above command returns JSON structured like this:

```json
[{
  "id": "2ee995b07cb201323db11aa32735a1a3",
  "type": "article",
  "title": "Renderings Revealed: Glass-Enclosed Restaurant & Patio Planned Downtown",
  "description": "Townhouse already announced plans for a new downtown Detroit location, but Eater Detroit has revealed that the Birmingham-based restaurant aspires to go beyond simply filling an empty storefront. Complete with a retractable roof, Townhouse Detroit plans to build a...",
  "full_text": "<div><p>[McIntosh Poris/Townhouse]  </p><p><strong>Townhouse</strong> already <a href=\"http://detroit.eater.com/2014/11/3/7148533/birminghams-townhouse-restaurant-is-headed-for-detroit\">announced</a> plans for a new downtown Detroit location, but <a href=\"http://detroit.eater.com/2015/1/8/7510471/townhouse-plans-greenhouse-style-dining-room-for-detroit-and-open-air\">Eater Detroit</a> has revealed that the Birmingham-based restaurant aspires to go beyond simply filling an empty storefront. Complete with a retractable roof, Townhouse Detroit plans to build a <strong>greenhouse-like dining room</strong> right next to One Detroit Center with seating for 120.</div>",
  "plain_text": "Townhouse already announced plans for a new downtown Detroit location, but Eater Detroit has revealed that the Birmingham-based restaurant aspires to go beyond simply filling an empty storefront. Complete with a retractable roof, Townhouse Detroit plans to build a greenhouse-like dining room right next to One Detroit Center with seating for 120.",
  "author": {
    "name": "Paul Beshouri"
  },
  "published_at": "2015-01-12T17:42:11Z",
  "images": {
    "thumbnail": {
      "url": null,
      "width": null,
      "height": null
    },
    "full_size": {
      "url": "http://detroit.curbed.com/uploads/townhouse1-thumb.jpg",
      "width": null,
      "height": null
    },
    "other": []
  },
  "source": {
    "id": null,
    "name": null,
    "description": null,
    "url": null,
    "icon": {
      "url": null,
      "width": null,
      "height": null
    }
  },
  "origin": {
    "id": null,
    "name": "Curbed Detroit",
    "url": "http://detroit.curbed.com/archives/2015/01/glassenclosed-restaurant-patio-planned-downtown.php",
    "icon": {
      "url": "http://curbed.com/favicon.ico",
      "width": 16,
      "height": 16
    }
  }
}]
```

This endpoint filters the results from the topic based on a passed term.  All results are in descending order with the most relevent match first. 

### HTTP Request

`GET https://api.backstit.ch/v1/topic/filter.json`

### Query Parameters

| Parameter | Required | Default | Description |
|---------|:-------:|:-------:|:-----------|
| token | yes | | To obtain a token, you must first log into backstitch and from the topic editor include the API add-on.  This will generate a secure token to identify the topic. |
| term | yes | | This will return results that are most relevant to the passed term. | 
| count | no | 20 | The number of results to return per call, up to a maximum of 50. |
| skip | no | 0 | The number of results to skip per call, to be used for paging. |

### Returns

An array of results.  Consult the [Result Type Dictionary](/#result-type-dictionary) for field descriptions.
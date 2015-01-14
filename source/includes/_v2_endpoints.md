# API 2.0 Endpoints

The backstitch API 2.0 includes the ability to build and manage topic pages from a RESTful interface along with a
more consistent endpoint schema for working with topics.

All API 2.0 requests use the base url of `https://api.backstit.ch/v2` and most authenticate by passing the topic's token as a url parameter and the organization's key as a query parameter.

<aside class="success">
  It is recommended to use API 2.0 as it will be the version to receive incremental updates.
</aside>

## Get Organization Details

```ruby
require 'rest_client'

response = RestClient.get 'https://api.backstit.ch/v2/organizations/70b5aa707ca6013231ce482a14180728'
```

```python
import urllib2

response = urllib2.urlopen('https://api.backstit.ch/v2/organizations/70b5aa707ca6013231ce482a14180728')
```

```shell
curl https://api.backstit.ch/v2/organizations/70b5aa707ca6013231ce482a14180728
```

> The above command returns JSON structured like this:

```json
{
  "id": 1049,
  "name": "Awesome Rocket Inc.",
  "logo": {
    "url": "http://backstitch-user-uploads.s3.amazonaws.com/production/organization_logos/awesome_rocket_logo.png",
    "width": 181,
    "height": 36
  },
  "highlight_color": "#1ba5ca",
  "key": "70b5aa707ca6013231ce482a14180728"
}
```

This endpoint retrieves basic details about an organization.

### HTTP Request

`GET https://api.backstit.ch/v2/organizations/{ORGANIZATION_KEY}`

### URL Parameters

| Parameter | Required | Description |
|---------|:-------:|:-----------|
| ORGANIZATION_KEY | yes | Your organization's api key is obtained from the organization dashboard under settings. |

### Returns

| Field | Data Type | Description |
|---------|:-------:|:-----------|
| id | integer | A unique identifier for the organization. |
| name | string | The name given to the organization. |
| logo | object | An optional logo uploaded for the organization. |
| highlight_color | string | An optional theme color set for the organization. |
| key | string | The organizations's api key. |

## Get Organization Topics

```ruby
require 'rest_client'

response = RestClient.get 'https://api.backstit.ch/v2/organizations/70b5aa707ca6013231ce482a14180728/topics'
```

```python
import urllib2

response = urllib2.urlopen('https://api.backstit.ch/v2/organizations/70b5aa707ca6013231ce482a14180728/topics')
```

```shell
curl https://api.backstit.ch/v2/organizations/70b5aa707ca6013231ce482a14180728/topics
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 10482,
    "name": "Apple News",
    "description": "The latest news around Apple",
    "banner": {
      "url": "http://backstitch-user-uploads.s3.amazonaws.com/production/topic_banners/18155_1421233959.jpg",
      "width": 912,
      "height": 384
    },
    "token": "700cc690776001326156482a14180728",
    "filters": [
      {
        "id": 20101,
        "value": "Apple",
        "type": "include"
      }
    ],
    "sources":[
      {
        "id": 782,
        "name": "MacRumors",
        "icon": {
          "url": "http://images-backstitch.s3.amazonaws.com/next/service_catalog/macrumors_icon.png",
          "width": "16",
          "height": "16"
        },
        "banner": {
          "url": "http://images-backstitch.s3.amazonaws.com/next/service_catalog/macrumors_banner.jpg",
          "width": "650",
          "height": "240"
        },
        "params": {
          "feed_url": {
            "type": "url",
            "value": "http://feeds.macrumors.com/MacRumors-All"
          }
        },
        "filters": [],
        "service": "rss"
      },
      {
        "id": 345,
        "name": "Technology news - CNNMoney.com",
        "icon":{
          "url": "http://cnn.com/favicon.ie9.ico",
          "width": 32,
          "height": 32
        },
        "banner":{
          "url": "http://i2.cdn.turner.com/money/dam/assets/150113142501-3doodler-thumbnail-620x348.jpg",
          "width": null,
          "height": null
        },
        "params":{
          "feed_url":{
            "type": "url",
            "value": "http://rss.cnn.com/rss/money_technology.rss"
          }
        },
        "filters":[
          {
            "uid": 20102,
            "value": "Android",
            "type": "exclude"
          }
        ],
        "service": "rss"
      }
    ]
  }
]
```

This endpoint retrieves a list of organization owned topics that have the API add-on enabled.

### HTTP Request

`GET https://api.backstit.ch/v2/organizations/{ORGANIZATION_KEY}/topics`

### URL Parameters

| Parameter | Required | Description |
|---------|:-------:|:-----------|
| ORGANIZATION_KEY | yes | Your organization's api key is obtained from the organization dashboard under settings. |

### Returns

| Field | Data Type | Description |
|---------|:-------:|:-----------|
| id | integer | A unique identifier for the topic. |
| name | string | The name given to the topic. |
| description | string | An optional description of the topic. |
| banner | object | The topic's displayed banner image if one was uploaded. |
| token | string | The topic's api token. |
| filters | array | A list of global keyword filters set on the topic. |
| sources | array | A list of sources included in the topic. |

For a more descriptive breakdown of the topic fields reference the [Get Topic Details](/#get-topic-details) section.

## Create Topic

```ruby
require 'rest_client'

response = RestClient.post 'https://api.backstit.ch/v2/topics', :params => {:key => '70b5aa707ca6013231ce482a14180728', :name => 'Local Detroit News'}
```

```python
import urllib
import urllib2

endpoint = 'https://api.backstit.ch/v2/topics'
params = {'key': '70b5aa707ca6013231ce482a14180728', 'name': 'Local Detroit News'}
encoded_params = urllib.urlencode(params)
request = urllib2.Request(endpoint, encoded_params)
response = urllib2.urlopen(request)
```

```shell
curl https://api.backstit.ch/v2/topics \
  -d "?key=70b5aa707ca6013231ce482a14180728&name=Local%20Detroit%20News"
```

> The above command returns JSON structured like this:

```json
{
  "id": 23942,
  "name": "Local Detroit News",
  "description": null,
  "banner": null,
  "token": "9b5d30a07d4001325ede482a14180728",
  "sources": [],  
  "filters": [],
  "errors": null
}
```

This endpoint allows the creation of a new organization owned topic with the API add-on enabled.

### HTTP Request

`POST https://api.backstit.ch/v2/topics`

### Query Parameters

| Parameter | Required | Default | Description |
|---------|:-------:|:-------:|:-----------|
| key | yes | | Your organization's api key is obtained from the organization dashboard under settings. |
| name | yes | | The name of your topic. |
| team | no | Organization (all) | The name of the team that this topic should belong to. |
| sources | no | | A list of sources to include in your topic at the time of creation.  [Detailed Documentation](/#add-topic-sources) |
| filters | no | | A list of global filters to set on your topic at the time of creation. [Detailed Documentation](/#add-topic-filters)|

### Returns

| Field | Data Type | Description |
|---------|:-------:|:-----------|
| id | integer | A unique identifier for the topic. |
| name | string | The name given to the topic. |
| description | string | An optional description of the topic. |
| banner | object | The topic's displayed banner image if one was uploaded. |
| token | string | The topic's api token. |
| sources | array | A list of included sources. |
| filters | array | A list of global keyword filters set on the topic. |
| errors | array | A list of any errors that occured during topic creation. |

## Add Topic Sources

```ruby
require 'rest_client'

response = RestClient.post 'https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728/sources', :params => {:key => '70b5aa707ca6013231ce482a14180728', :data => [{:service => 'facebook_user', :value => 'backstitchapp', :filters => [{:type => 'include', :value => 'detroit'}]}]}
```

```python
import urllib
import urllib2

endpoint = 'https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728/sources'
params = {'key': '70b5aa707ca6013231ce482a14180728', 'data': [{'service': 'facebook_user', 'value': 'backstitchapp', 'filters': [{'type': 'include', 'value': 'detroit'}]}]}
encoded_params = urllib.urlencode(params)
request = urllib2.Request(endpoint, encoded_params)
response = urllib2.urlopen(request)
```

```shell
curl https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728/sources \
  -H "Content-Type: application/json" \
  -d '{"key": "70b5aa707ca6013231ce482a14180728", "data": [{"service": "facebook_user", "value": "backstitchapp", "filters": [{"type": "include", "value": "detroit"}]}]}'
```

> The above command returns JSON structured like this:

```json
{  
  "errors": [],
  "sources": [
    {
      "id": 76,
      "name": "Facebook Posts from backstitchapp",
      "icon": {
        "url": "http://graph.facebook.com/373050736086342/picture",
        "width": 50,
        "height": 50
      },
      "banner": {
        "url": "http://images-backstitch.s3.amazonaws.com/next/service_catalog/facebook_banner.jpg",
        "width": 650,
        "height": 240
      },
      "params": {
        "user": {
          "type": "search_term",
          "value": "backstitchapp"
        }
      },
      "filters": [
        {
          "id": 13414,
          "value": "detroit",
          "type": "include"
        }
      ],
      "service": "facebook_user"
    }
  ]
}
```

This endpoint allows for including new sources into the topic.

<aside class="success">
  Including new sources requires the Topic to be reindexed and may take up to **1 minute** for new results to appear.
</aside>

### HTTP Request

`POST https://api.backstit.ch/v2/topics/{TOPIC_TOKEN}/sources`

### URL Parameters

| Parameter | Required | Description |
|---------|:-------:|:-----------|
| TOPIC_TOKEN | yes | The topic's token generated from adding the API add-on from the topic editor or returned by the [Create Topic](/#create-topic) endpoint. |

### Query Parameters

| Parameter | Required | Default | Description |
|---------|:-------:|:-------:|:-----------|
| key | yes | | Your organization's api key is obtained from the organization dashboard under settings. |
| data | yes| | An array of new sources to add to your topic. |
| url | no | | This will crawl the specified url and add any sources found on the website.  This includes available RSS feeds and listed social media accounts. |

### Data Child Parameters

| Parameter | Required | Default | Description |
|---------|:-------:|:-------:|:-----------|
| service | yes | | The name of the new source's service. |
| value | yes | | The parameter for the new source as required by the service. |
| filters | no | | An array of filters to be set on the source.  [Detailed Documentation](/#add-topic-filters) |

### Available Services

|Value Type| Example |
|:---------|:---------|
| empty | *null* or *""* |
| phrase | *"Internet of Things"* |
| tag | *"InternetOfThings"* |
| username | *"backstitch"* |
| location | *"Detroit, MI"* |
| url | *"http://rss.cnn.com/rss/cnn_topstories.rss"* |

|Requires Linked Account*| Service | Value Type | Description
|:---------:|:---------|:-------:|:-------|
|X| app_dot_net_hashtag | tag | Retrieves public App.net Alpha posts by hashtag. |
|| dealfind_deals | nothing | Retrieves the latest deals from Dealfind. |
|X| facebook_mention | phrase | Retrieves public Facebook posts that mention a phrase. |
|X| facebook_hashtag | tag | Retrieves public Facebook posts by hashtag. |
|X| facebook_user | username | Retrieves public Facebook posts made by a user or a company page. |
|X| flickr_user | username | Retrieves public Flickr photos published by a user. |
|X| flickr_mention | phrase | Retrieves public Flickr photos that mentions the phrase in its description. |
|X| google_plus_user | username | Retrieves public Google+ posts made by a user. |
|| groupon_deals | location | Retrieves Groupon deals for a location. |
|X| instagram_popular | nothing | Retrieves the most popular photos currently on Instagram. |
|X| instagram_hashtag | phrase | Retrieves public Instagram photos by hashtag. |
|X| instagram_user | username | Retrieves public Instagram photos published by a user. |
|X| instagram_area | location | Retrieves public Instagram photos posted around a location. |
|X| linkedin_user | username | Retrieves public LinkedIn posts by a user. |
|| living_social_deals | location | Retrieves the latest Living Social deals. |
|| one_sale_a_day_deals | nothing | Retrieves the latest 1SaleADay deals. |
|| price_plunge_deals | nothing | Retrieves the latest Price Plunge deals. |
|| subreddit | tag | Retrieves Reddit submissions made to a public /r subreddit. |
|| rss | url | Retrieves articles from an RSS feed. |
|| tanga_deals | nothing | Retrieves the latest deals from Tanga. |
|| tee_fury_deals | nothing | Retrieves the latest deals from Tee Fury. |
|X| tumblr_tagged | tag | Retrieves public Tumblr posts by tag. |
|X| twitter_mention | phrase | Retrieves public Tweets that contain a phrase. |
|X| twitter_hashtag | tag | Retrieves public Tweets by hashtag. |
|X| twitter_user | username | Retrieves public Tweets made by a user. |
|| woot_daily_deals | nothing | Retrieves the latest Woot deals. |
|| woot_plus_deals | nothing | Retrieves the latest Woot Plus deals. |
|X| youtube_user | username | Retrieves public videos posted by a YouTube user or account. |

*These services require an associated account to be linked from the organization dashboard. 

### Returns

| Field | Data Type | Description |
|---------|:-------:|:-----------|
| errors | array | A list of errors for sources that were unable to be included for some reason.  |
| sources | array | A list of sources that were successfully added to the topic. |

## Add Topic Filters

```ruby
require 'rest_client'

response = RestClient.post "https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728/filters", :params => {:key => "70b5aa707ca6013231ce482a14180728", :data => [{:type => "include", :value => "Captain America"}]}
```

```python
import urllib
import urllib2

endpoint = 'https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728/filters'
params = {'key': '70b5aa707ca6013231ce482a14180728', 'data': [{'type': 'include', 'value': 'Captain America'}]}
encoded_params = urllib.urlencode(params)
request = urllib2.Request(endpoint, encoded_params)
response = urllib2.urlopen(request)
```

```shell
curl https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728/sources \
  -H "Content-Type: application/json" \
  -d '{"key": "70b5aa707ca6013231ce482a14180728", "data": [{"type": "include", "value": "Captain America"]}}'
```

> The above command returns JSON structured like this:

```json
{
  "errors":[],
  "filters":[
    {
      "id": 3242,
      "phrase": "Captain America",
      "type": "include"
    }
  ]
}
```

This endpoint sets a new global filter on the topic.  All filters are chained using an _OR_ expression and are evaluated based on variations of the phrase's contents. _(example: restaurant also matches restaurants)_

Filters are applied to all [Result Type](/#result-type-dictionary) fields and can be used for full-text searching of content or for even matching specific usernames in the orgin or source objects.

<aside class="success">
  Setting new filters requires the Topic to be reindexed and may take up to **1 minute** for accurate results to appear.
</aside>

### HTTP Request

`POST https://api.backstit.ch/v2/topics/{TOPIC_TOKEN}/filters`

### URL Parameters

| Parameter | Required | Description |
|---------|:-------:|:-----------|
| TOPIC_TOKEN | yes | The topic's token generated from adding the API add-on from the topic editor or returned by the [Create Topic](/#create-topic) endpoint. |

### Query Parameters

| Parameter | Required | Default | Description |
|---------|:-------:|:-------:|:-----------|
| key | yes | | Your organization's api key is obtained from the organization dashboard under settings. |
| data | yes| | An array of new filters to set on the topic. |

### Data Child Parameters

| Parameter | Required | Description |
|---------|:-------:|:-----------|
| type | yes | The type of filter to set. |
| value | yes | The value required by the specific filter type. |

### Available Filters Types

| Type | Value | Description |
|---------|:-------:|:-------|
| include | phrase | Phrase that **must be** included somewhere in the results. |
| exclude | phrase | Phrase that **must not** be included somewhere in the results. |
| nsfw | phrase | Automatically adds a list of Not Safe For Work terms as exclude filters. |

### Returns

| Field | Data Type | Description |
|---------|:-------:|:-----------|
| errors | array | A list of errors for filters that were unable to be set. |
| filters | array | A list of filters that were successfully set on the topic. |

## Clone Topic

```ruby

```

```python

```

```shell

```

> The above command returns JSON structured like this:

```json

```

This endpoint enables cloning of sources and filters from a list of other topics.  This is a great way to setup templates for your topics or to build user-specific streams.

<aside class="success">
  This action requires the Topic to be reindexed and may take up to **1 minute** for accurate results to appear.
</aside>

### HTTP Request

`POST https://api.backstit.ch/v2/topics/{TOPIC_TOKEN}/clone`

### URL Parameters

| Parameter | Required | Description |
|---------|:-------:|:-----------|
| TOPIC_TOKEN | yes | The API token for the topic that you want to modify.  The token generated from adding the API add-on from the topic editor or returned by the [Create Topic](/#create-topic) endpoint. |

### Query Parameters

| Parameter | Required | Default | Description |
|---------|:-------:|:-------:|:-----------|
| key | yes | | Your organization's api key is obtained from the organization dashboard under settings. |
| topic_tokens | yes | | An array of API tokens for the topics to clone sources and filters from.  |

### Returns

## UnClone Topic

```ruby

```

```python

```

```shell

```

> The above command returns JSON structured like this:

```json

```

This endpoint enables removing the sources and filters that were cloned from other topics.  This is a great way to maintain user-specific streams where subtopics can be unsubscribed.

<aside class="warning">
  This will remove any sources or filters that were added outside of the clone method.
</aside>

<aside class="success">
  This action requires the Topic to be reindexed and may take up to **1 minute** for accurate results to appear.
</aside>

### HTTP Request

`POST https://api.backstit.ch/v2/topics/{TOPIC_TOKEN}/unclone`

### URL Parameters

| Parameter | Required | Description |
|---------|:-------:|:-----------|
| TOPIC_TOKEN | yes | The API token for the topic that you want to modify.  The token generated from adding the API add-on from the topic editor or returned by the [Create Topic](/#create-topic) endpoint. |

### Query Parameters

| Parameter | Required | Default | Description |
|---------|:-------:|:-------:|:-----------|
| key | yes | | Your organization's api key is obtained from the organization dashboard under settings. |
| topic_tokens | yes | | An array of API tokens for the topics to **remove** sources and filters from.  |

### Returns


## Delete Topic Sources

```ruby
require 'rest_client'

response = RestClient.delete 'https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728/sources', :params => {:key => '70b5aa707ca6013231ce482a14180728' :data => [{:service => 'facebook_user', :value => 'backstitchapp'}]}
```

```python

```

```shell
curl https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728/sources
```

> The above command returns JSON structured like this:

```json
{
  "errors":[
    {
      "message": "Invalid service",
      "service": "facebook",
      "value": "backstitchapp"
    }
  ],
  "sources":[
    {
      "filters":[],
      "uid": 76,
      "name": "Facebook Posts from backstitchapp",
      "icon":{
        "url": "http://images-backstitch.s3.amazonaws.com/services/icons/facebook.png",
        "width": 64,
        "height": 64
      },
      "banner":{
        "url": "http://images-backstitch.s3.amazonaws.com/next/service_catalog/facebook_banner.jpg",
        "width": 650,
        "height": 240
      },
      "params":{
        "user":{
          "type": "search_term",
          "value": "backstitchapp"
        }
      },
      "service_name": "facebook_user"
    }
  ]
}
```

This endpoint adds new sources to the topic.

### HTTP Request

`DELETE https://api.backstit.ch/v2/topics/{TOPIC_TOKEN}/sources`

### Query Parameters

| Parameter | Required | Default | Description |
|---------|:-------:|:-------:|:-----------|
| key | yes | | Your organization's api key obtained from the organization dashboard. |
| data | yes| | An Array of source to add to your topic. |

### Data Child Parameters

| Parameter | Required | Default | Description |
|---------|:-------:|:-------:|:-----------|
| service | yes | | The name of the source service to add. |
| value | yes | | The value of the service. |

### Available Services

| Service | Value | Description
|---------|:-------:|:-------:|
| rss | url | An rss feed's url |


### Returns

| Field | Data Type | Description |
|---------|:-------:|:-----------|
| errors | array | A list of errors for sources that were not removed |
| sources | array | A list of sources that were removed |

## Delete Topic Filters

```ruby
require 'rest_client'

response = RestClient.delete 'https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728/filters', :params => {:key => '70b5aa707ca6013231ce482a14180728' :data => [{:type => 'include', :value => 'downtown'}]}
```

```python

```

```shell
curl https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728/filters
```

> The above command returns JSON structured like this:

```json
{
  "errors":[
    {
      "message": "Invalid type",
      "type": "included",
      "value": "downtown"
    }
  ],
  "filters":[
    {
      "uid": 345,
      "phrase": "downtown",
      "type": "include"
    }
  ]
}
```

This endpoint adds new sources to the topic.

### HTTP Request

`DELETE https://api.backstit.ch/v2/topics/{TOPIC_TOKEN}/filters`

### Query Parameters

| Parameter | Required | Default | Description |
|---------|:-------:|:-------:|:-----------|
| key | yes | | Your organization's api key obtained from the organization dashboard. |
| data | yes | | The array of filters to add |

### Data Child Parameters

| Parameter | Required | Default | Description |
|---------|:-------:|:-------:|:-----------|
| type | yes | | The filter type. |
| value | yes | | The value of the filter. |

### Available Filters

| Type | Value | Description
|---------|:-------:|:-------:|
| include | phrase | Keywords that have to icluded in the feed |
| exclude | phrase | Keywords that have to excluded from the feed |


### Returns

| Field | Data Type | Description |
|---------|:-------:|:-----------|
| errors | array | A lits of error for filters that were not removed |
| filters | array | A list of global keyword filters that were removed |

## Delete Topic

```ruby
require 'rest_client'

response = RestClient.delete 'https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728', :params => {:key => '70b5aa707ca6013231ce482a14180728'}
```

```python

```

```shell
curl https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728
```

> The above command returns JSON structured like this:

```json
{
  "uid": 13,
  "name": "Detroit",
  "description": "",
  "banner": {
    "url": "http://images-backstitch.s3.amazonzws.com/next/logos/backstitch_purple_icon.png",
    "width": 300,
    "height": 300
  },
  "token": "9b5d30a07d4001325ede482a14180728",
  "filters": [],
  "sources":[]
}
```

This endpoint adds new sources to the topic.

### HTTP Request

`DELETE https://api.backstit.ch/v2/topics/{TOPIC_TOKEN}`

### Query Parameters

| Parameter | Required | Default | Description |
|---------|:-------:|:-------:|:-----------|
| key | yes | | Your organization's api key obtained from the organization dashboard. |


### Returns

| Field | Data Type | Description |
|---------|:-------:|:-----------|
| uid | integer | A unique identifier for the topic |
| name | string | The name given to the topic |
| description | string | An optional description of the topic |
| banner | object | The topic's displayed banner image if one was uploaded |
| token | string | The topic's api token |
| filters | array | A list of global keyword filters set on the topic |
| sources | array | A list of included sources |

## Get Topic Details

```ruby
require 'rest_client'

response = RestClient.get 'https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728'
```

```python
import urllib2

response = urllib2.urlopen('https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728')
```

```shell
curl https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728
```

> The above command returns JSON structured like this:

```json
{
  "uid": 13,
  "name": "Detroit",
  "description": "",
  "banner": {
    "url": "http://images-backstitch.s3.amazonzws.com/next/logos/backstitch_purple_icon.png",
    "width": 300,
    "height": 300
  },
  "token": "9b5d30a07d4001325ede482a14180728",
  "filters": [
    {
      "uid": 345,
      "phrase": "downtown",
      "type": "include"
    }
  ],
  "sources": [
    {
      "filters":[],
      "uid": 76,
      "name": "Facebook Posts from backstitchapp",
      "icon":{
        "url": "http://images-backstitch.s3.amazonaws.com/services/icons/facebook.png",
        "width": 64,
        "height": 64
      },
      "banner":{
        "url": "http://images-backstitch.s3.amazonaws.com/next/service_catalog/facebook_banner.jpg",
        "width": 650,
        "height": 240
      },
      "params":{
        "user":{
          "type": "search_term",
          "value": "backstitchapp"
        }
      },
      "service_name": "facebook_user"
    }
  ]
}
```

This endpoint retrieves details about a topic.

### HTTP Request

`GET https://api.backstit.ch/v2/topics/{TOPIC_TOKEN}`

### Returns

| Field | Data Type | Description |
|---------|:-------:|:-----------|
| uid | integer | A unique identifier for the topic |
| name | string | The name given to the topic |
| description | string | An optional description of the topic |
| banner | object | The topic's displayed banner image if one was uploaded |
| token | string | The topic's api token |
| filters | array | A list of global keyword filters set on the topic |
| feeds | array | A list of included feeds |

## Retrieve Topic Results

```ruby
require 'rest_client'

# Retrieve latest results
response = RestClient.get 'https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728/results'

# Retrieve second page of latest results
response = RestClient.get 'https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728/results', :params => {:skip => 20} 

# Search Results
response = RestClient.get 'https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728/results', :params => {:query => 'restaurants'} 
```

```python
import urllib
import urllib2

endpoint = 'https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728/results'

# Retrieve latest results
response = urllib2.urlopen(endpoint)

# Retrieve second page of latest results
params = {'skip': 20}
data = urllib.urlencode(params)
req = urllib2.Request(endpoint, data)
response = urllib2.urlopen(req)

# Search Results
params = {'query': 'restaurants'}
data = urllib.urlencode(params)
req = urllib2.Request(endpoint, data)
response = urllib2.urlopen(req)
```

```shell
# Retrieve latest results
curl https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728/results

# Retrieve second page of latest results
curl https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728/results \
  -d "skip=20"
  
# Search Results
curl https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728/results \
  -d "query=restaurants"
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

This endpoint retrieves results from the topic.  By default all results are returned in descending order by the date that the content was originally published.  If a query is passed then the order is based on the most relevent match to
the query.

### HTTP Request

`GET https://api.backstit.ch/v2/topics/{TOPIC_TOKEN}/results`

### Query Parameters

| Parameter | Required | Default | Description |
|---------|:-------:|:-------:|:-----------|
| count | no | 20 | The number of results to return per call, up to a maximum of 50. |
| skip | no | 0 | The number of results to skip per call, to be used for paging. |
| query | no | | This will return results that are most relevant to the passed term. | 

### Returns

An array of results.  Consult the [Result Type Dictionary](/#result-type-dictionary) for field descriptions.
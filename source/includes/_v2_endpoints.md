# API 2.0 Endpoints

The backstitch API 2.0 includes the ability to build and manage topic pages from a RESTful interface along with a
more consistent endpoint schema for consuming content from topics.

All API 2.0 requests use the base url of `https://api.backstit.ch/v2` and authenticate by passing the topic's token as
a url parameter and the organization's key as a query parameter.

<aside class="success">
  It is recommended to use API 2.0 as it will be the version to receive incremental updates.
</aside>

## Get Organization Details

```ruby
require 'rest_client'

response = RestClient.get 'https://api.backstit.ch/v2/organization/57DF8832C59E420E80B1DF4F9'
```

```python
import urllib2

response = urllib2.urlopen('https://api.backstit.ch/v2/organization/57DF8832C59E420E80B1DF4F9')
```

```shell
curl https://api.backstit.ch/v2/organization/57DF8832C59E420E80B1DF4F9
```

> The above command returns JSON structured like this:

```json
<!-- TODO -->
```

This endpoint retrieves details about an organization.

### HTTP Request

`GET https://api.backstit.ch/v2/organization/{ORGANIZATION_KEY}`

### URL Parameters

| Parameter | Description |
|---------|:-----------|
| organization_key | If you are an organization admin you can obtain your key from the organization dashboard found under settings on backstitch |

## Get Organization Topics

```ruby
require 'rest_client'

response = RestClient.get 'https://api.backstit.ch/v2/organization/57DF8832C59E420E80B1DF4F9/topics'
```

```python
import urllib2

response = urllib2.urlopen('https://api.backstit.ch/v2/organization/57DF8832C59E420E80B1DF4F9/topics')
```

```shell
curl https://api.backstit.ch/v2/organization/57DF8832C59E420E80B1DF4F9/topics
```

> The above command returns JSON structured like this:

```json
<!-- TODO -->
```

This endpoint retrieves a list of organization owned topics.

### HTTP Request

`GET https://api.backstit.ch/v2/organization/{ORGANIZATION_KEY}/topics`

### URL Parameters

| Parameter | Description |
|---------|:-----------|
| organization_key | If you are an organization admin you can obtain your key from the organization dashboard found under settings on backstitch |

### Returns

TODO

## Create Topic

```ruby
require 'rest_client'

# Create a new topic called 'News Around Detroit'
response = RestClient.post 'https://api.backstit.ch/v2/topic', :params => {:key => '57DF8832C59E420E80B1DF4F9', :name => 'News around Detroit'}
```

```python
import urllib
import urllib2

url = 'https://api.backstit.ch/v2/topic/'
response = urllib2.urlopen(endpoint)
params = {'skip': 20}
data = urllib.urlencode(params)
req = urllib2.Request(endpoint, data)
response = urllib2.urlopen(req)
```

```shell
curl https://api.backstit.ch/v2/organization/57DF8832C59E420E80B1DF4F9/topics
```

> The above command returns JSON structured like this:

```json
<!-- TODO -->
```

This endpoint allows the creation of a new organization owned topic that has API support.

### HTTP Request

`POST https://api.backstit.ch/v2/topic`

### Query Parameters

| Parameter | Required | Default | Description |
|---------|:-------:|:-------:|:-----------|
| key | yes | | Your organization's api key obtained from the organization dashboard. |
| name | yes | | The name of your topic. |

### Returns

TODO

## Add Topic Sources

```ruby
require 'rest_client'

response = RestClient.post 'https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/source', :params => {:key => '57DF8832C59E420E80B1DF4F9' :service => 'twitter_user', :value => 'backstitch'}

response = RestClient.post 'https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/source', :params => {:key => '57DF8832C59E420E80B1DF4F9', :service => 'twitter_user', :value => 'backstitch', :filters => [{:type => 'include_term', :value => 'detroit'}]}
```

```python
import urllib
import urllib2

url = 'https://api.backstit.ch/v2/topic/'
response = urllib2.urlopen(endpoint)
params = {'skip': 20}
data = urllib.urlencode(params)
req = urllib2.Request(endpoint, data)
response = urllib2.urlopen(req)
```

```shell
curl https://api.backstit.ch/v2/organization/57DF8832C59E420E80B1DF4F9/topics
```

> The above command returns JSON structured like this:

```json
<!-- TODO -->
```

This endpoint adds new sources to the topic.

### HTTP Request

`POST https://api.backstit.ch/v2/topic/{TOPIC_TOKEN}/sources`

### Query Parameters

| Parameter | Required | Default | Description |
|---------|:-------:|:-------:|:-----------|
| key | yes | | Your organization's api key obtained from the organization dashboard. |
| service | yes | | The name of the source service to add |
| value | yes | | The value of the service |
| filters | no | | Optional filters |

### Available Services

| Service | Value | Description
|---------|:-------:|:-------:|
| rss | url | | An rss feed's url |

### Available Filters

| Type | Value | Description
|---------|:-------:|:-------:|
| rss | url | | An rss feed's url |


### Returns

TODO

## Add Topic Filters

```ruby
require 'rest_client'

response = RestClient.post 'https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/filters', :params => {:key => '57DF8832C59E420E80B1DF4F9' :filters => [{}])

response = RestClient.post 'https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/filters', :params => {:key => '57DF8832C59E420E80B1DF4F9', :service => 'twitter_user', :value => 'backstitch', :filters => [{:type => 'include_term', :value => 'detroit'}]}
```

```python
import urllib
import urllib2

url = 'https://api.backstit.ch/v2/topic/'
response = urllib2.urlopen(endpoint)
params = {'skip': 20}
data = urllib.urlencode(params)
req = urllib2.Request(endpoint, data)
response = urllib2.urlopen(req)
```

```shell
curl https://api.backstit.ch/v2/organization/57DF8832C59E420E80B1DF4F9/topics
```

> The above command returns JSON structured like this:

```json
<!-- TODO -->
```

This endpoint adds new sources to the topic.

### HTTP Request

`POST https://api.backstit.ch/v2/topic/{TOPIC_TOKEN}/filters`

### Query Parameters

| Parameter | Required | Default | Description |
|---------|:-------:|:-------:|:-----------|
| key | yes | | Your organization's api key obtained from the organization dashboard. |
| data | yes | | The array of filters to add |

### Available Filters

| Type | Value | Description
|---------|:-------:|:-------:|
| rss | url | | An rss feed's url |


### Returns

TODO

## Delete Topic Sources

```ruby
require 'rest_client'

response = RestClient.post 'https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/filters', :params => {:key => '57DF8832C59E420E80B1DF4F9' :filters => [{}])

response = RestClient.post 'https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/filters', :params => {:key => '57DF8832C59E420E80B1DF4F9', :service => 'twitter_user', :value => 'backstitch', :filters => [{:type => 'include_term', :value => 'detroit'}]}
```

```python
import urllib
import urllib2

url = 'https://api.backstit.ch/v2/topic/'
response = urllib2.urlopen(endpoint)
params = {'skip': 20}
data = urllib.urlencode(params)
req = urllib2.Request(endpoint, data)
response = urllib2.urlopen(req)
```

```shell
curl https://api.backstit.ch/v2/organization/57DF8832C59E420E80B1DF4F9/topics
```

> The above command returns JSON structured like this:

```json
<!-- TODO -->
```

This endpoint adds new sources to the topic.

### HTTP Request

`DELETE https://api.backstit.ch/v2/topic/{TOPIC_TOKEN}/sources`

### Query Parameters

| Parameter | Required | Default | Description |
|---------|:-------:|:-------:|:-----------|
| key | yes | | Your organization's api key obtained from the organization dashboard. |
| data | yes | | The array of filters to add |

### Available Filters

| Type | Value | Description
|---------|:-------:|:-------:|
| rss | url | | An rss feed's url |


### Returns

TODO

## Delete Topic Filters

```ruby
require 'rest_client'

response = RestClient.post 'https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/filters', :params => {:key => '57DF8832C59E420E80B1DF4F9' :filters => [{}])

response = RestClient.post 'https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/filters', :params => {:key => '57DF8832C59E420E80B1DF4F9', :service => 'twitter_user', :value => 'backstitch', :filters => [{:type => 'include_term', :value => 'detroit'}]}
```

```python
import urllib
import urllib2

url = 'https://api.backstit.ch/v2/topic/'
response = urllib2.urlopen(endpoint)
params = {'skip': 20}
data = urllib.urlencode(params)
req = urllib2.Request(endpoint, data)
response = urllib2.urlopen(req)
```

```shell
curl https://api.backstit.ch/v2/organization/57DF8832C59E420E80B1DF4F9/topics
```

> The above command returns JSON structured like this:

```json
<!-- TODO -->
```

This endpoint adds new sources to the topic.

### HTTP Request

`DELETE https://api.backstit.ch/v2/topic/{TOPIC_TOKEN}/filters`

### Query Parameters

| Parameter | Required | Default | Description |
|---------|:-------:|:-------:|:-----------|
| key | yes | | Your organization's api key obtained from the organization dashboard. |
| data | yes | | The array of filters to add |

### Available Filters

| Type | Value | Description
|---------|:-------:|:-------:|
| rss | url | | An rss feed's url |


### Returns

TODO

## Delete Topic

```ruby
require 'rest_client'

response = RestClient.post 'https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/filters', :params => {:key => '57DF8832C59E420E80B1DF4F9' :filters => [{}])

response = RestClient.post 'https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/filters', :params => {:key => '57DF8832C59E420E80B1DF4F9', :service => 'twitter_user', :value => 'backstitch', :filters => [{:type => 'include_term', :value => 'detroit'}]}
```

```python
import urllib
import urllib2

url = 'https://api.backstit.ch/v2/topic/'
response = urllib2.urlopen(endpoint)
params = {'skip': 20}
data = urllib.urlencode(params)
req = urllib2.Request(endpoint, data)
response = urllib2.urlopen(req)
```

```shell
curl https://api.backstit.ch/v2/organization/57DF8832C59E420E80B1DF4F9/topics
```

> The above command returns JSON structured like this:

```json
<!-- TODO -->
```

This endpoint adds new sources to the topic.

### HTTP Request

`DELETE https://api.backstit.ch/v2/topic/{TOPIC_TOKEN}`

### Query Parameters

| Parameter | Required | Default | Description |
|---------|:-------:|:-------:|:-----------|
| key | yes | | Your organization's api key obtained from the organization dashboard. |
| data | yes | | The array of filters to add |

### Available Filters

| Type | Value | Description
|---------|:-------:|:-------:|
| rss | url | | An rss feed's url |


### Returns

TODO

## Get Topic Details

```ruby
require 'rest_client'

response = RestClient.get 'https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C'
```

```python
import urllib2

response = urllib2.urlopen('https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C')
```

```shell
curl https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C
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

`GET https://api.backstit.ch/v2/topic/{TOPIC_TOKEN}`

### URL Parameters

| Parameter | Description |
|---------|:-----------|
| token | To obtain a token, you must first log into backstitch and from the topic editor include the API add-on.  This will generate a secure token to identify the topic. |

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

## Retrieve Topic Results

```ruby
require 'rest_client'

# Retrieve latest results
response = RestClient.get 'https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/results'

# Retrieve second page of latest results
response = RestClient.get 'https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/results', :params => {:skip => 20} 

# Search Results
response = RestClient.get 'https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/results', :params => {:query => 'restaurants'} 
```

```python
import urllib
import urllib2

endpoint = 'https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/results'

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
curl https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/results

# Retrieve second page of latest results
curl https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/results \
  -d "skip=20"
  
# Search Results
curl https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/results \
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

`GET https://api.backstit.ch/v2/topic/{TOPIC_TOKEN}/results`

### URL Parameters

| Parameter | Description |
|---------|:-----------|
| token | To obtain a token, you must first log into backstitch and from the topic editor include the API add-on.  This will generate a secure token to identify the topic. |

### Query Parameters

| Parameter | Required | Default | Description |
|---------|:-------:|:-------:|:-----------|
| count | no | 20 | The number of results to return per call, up to a maximum of 50. |
| skip | no | 0 | The number of results to skip per call, to be used for paging. |
| query | no | | This will return results that are most relevant to the passed term. | 

### Returns

An array of results.  Consult the [Result Type Dictionary](/#result-type-dictionary) for field descriptions.
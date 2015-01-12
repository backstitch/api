---
title: API Reference

language_tabs:
  - shell: cURL
  - ruby
  - python

toc_footers:
  - <a href='mailto:team@backstit.ch?subject=Request for Developer Key'>Contact Us For A Developer Key</a>
  - <a href='http://backstit.ch'>Visit backstitch</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the backstitch API!  You can use our API to build and access backstitch topic pages to leverage our content curation engine for your app.

Currently access to our API is on a request basis for a small monthly charge.  To request access you can email us at
[team@backstit.ch](mailto:team@backstit.ch?subject=Request for Developer Key).

# Authentication

```ruby
require 'rest_client'

# Modification requires both an organization's key and a topic's token
RestClient.post 'https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/source', {:key => '57DF8832C59E420E80B1DF4F9'}

# Read-Only request only requires a topic's token
response = RestClient.get 'https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/source'
```

```python
import urllib
import urllib2

# Modification requires both an organization's key and a topic's token
url = 'https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/source'
values = {'key': '57DF8832C59E420E80B1DF4F9'}
data = urllib.urlencode(values)
req = urllib2.Request(url, data)
urllib2.urlopen(req)

# Read-Only request only requires a topic's token
response = urllib2.urlopen('https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/source')
html = response.read()
```

```shell
# Modification requires both an organization's key and a topic's token
# POST https://api.backstit.ch/v2/topic/{topic_token}/source?key={organization_key}
curl https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/source \
  -d "key=57DF8832C59E420E80B1DF4F9"



# Read-Only request only requires a topic's token
# GET https://api.backstit.ch/v2/topic/{topic_token}/details
curl https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/details

```
> Make sure to replace `57DF8832C59E420E80B1DF4F9` with your organization's key and `9523280292F046269CD4C2F8C` with your topic's token.

backstitch uses API keys and tokens to allow access to the API.  For all actions that create or modify topic pages
the organization's key must be passed.  For reading results from a topic page only the topic's token is required.

| Action | Organization Key | Topic Token|
|---------|:-------:|:-----------:|
CREATE | X | X* |
READ   |  |  X  |
UPDATE | X | X |
DELETE | X | X |

<aside class="notice">*Unless a new topic is being created.</aside>

# API 2.0 Endpoints

All API requests use the base url of `https://api.backstit.ch/v1/`

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Isis",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/3"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Isis",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">If you're not using an administrator API key, note that some kittens will return 403 Forbidden if they are hidden for admins only.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the cat to retrieve


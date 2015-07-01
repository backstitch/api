---
title: backstitch API Reference

language_tabs:
  - shell: cURL
  - ruby

toc_footers:
  - <a href='http://backstit.ch', target="_blank">Visit backstitch</a>
  - <a href='http://backstit.ch/tour/api', target="_blank">Register For A Developer Key</a>
  - <a href='http://github.com/tripit/slate', target="_blank">Documentation Powered by Slate</a>

includes:
  - widget
  - v2_endpoints
  - v1_endpoints
  - result_type_dictionary

search: true
---

# Introduction

Welcome to the backstitch API!  You can use our API to build and access backstitch topic pages to leverage our content curation engine for your app.

Information regarding limits and pricing can be found here [http://backstit.ch/pricing]http://backstit.ch/pricing

# Authentication

```ruby
require 'rest_client'

# Modification requires both an organization's key and a topic's token
response = RestClient.post 'https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728/sources', :params => {:key => '70b5aa707ca6013231ce482a14180728', :data => [{:service => 'twitter_user', :value => 'backstitch'}]}

# Read-Only request only requires a topic's token
response = RestClient.get 'https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728'
```

<!-- ```python
import urllib
import urllib2

# Modification requires both an organization's key and a topic's token
endpoint = 'https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728/sources'
params = {'key': '70b5aa707ca6013231ce482a14180728', 'data': [{'service': 'twitter_user', 'value': 'backstitch'}]}
encoded_params = urllib.urlencode(params)
request = urllib2.Request(endpoint, encoded_params)
response = urllib2.urlopen(request)

# Read-Only request only requires a topic's token
response = urllib2.urlopen('https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728')
``` -->

```shell
# Modification requires both an organization's key and a topic's token
curl https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728/sources \
  -H "Content-Type: application/json" \
  -d '{"key": "70b5aa707ca6013231ce482a14180728", "data": [{"service": "twitter_user", "value": "backstitch"}]}'
  
# Read-Only request only requires a topic's token
curl https://api.backstit.ch/v2/topics/9b5d30a07d4001325ede482a14180728
```
> Make sure to replace `70b5aa707ca6013231ce482a14180728` with your organization's key and `9b5d30a07d4001325ede482a14180728` with your topic's token.

backstitch uses API keys and tokens to allow access to the API.  For all actions that create or modify topic pages
the organization's key must be passed.  For reading results from a topic page only the topic's token is required.

| Action | Organization Key | Topic Token|
|---------|:-------:|:-----------:|
CREATE | X | X* |
READ   |  |  X  |
UPDATE | X | X |
DELETE | X | X |

<aside class="notice">*Unless a new topic is being created.</aside>
<aside class="warning">
If you're using API 1.0 consult the authentication documentation in that section or consider upgrading to API 2.0
</aside>



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
  - v2_endpoints
  - v1_endpoints
  - result_type_dictionary

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
RestClient.post 'https://api.backstit.ch/v2/topic/9523280292F046269CD4C2F8C/source', :params => {:key => '57DF8832C59E420E80B1DF4F9'}

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
<aside class="warning">
If you're using API 1.0 consult the authentication documentation in that section or consider upgrading to API 2.0
</aside>

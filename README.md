#backstitch API Documention
- - -

## Base url: api.backstit.ch

- - -


### fetch topic
	GET /v1/topic/fetch.json

##### Parameters
* * * 
###### token
_required_

To obtain a token, you must first log in to the backstitch and set the topic to allow api calls in the topic editor.  This will generate the token that will identify the topic.

* * *
###### count
_optional_

The number of results to return per call, up to a maximum of 50. Defaults to 20.

* * *
###### skip
_optional_

The number of results to skip per call, to be used for paging. Defaults to 0.

- - -

### filter topic
	GET /v1/topic/filter

##### Parameters
* * * 
###### token
_required_

To obtain a token, you must first log in to the backstitch and set the topic to allow api calls in the topic editor.  This will generate the token that will identify the topic.

* * * 
###### term
_required_

This behaves similar to a Google like search and will returns results that are most relevant to the term you entered.

* * *
###### count
_optional_

The number of results to return per call, up to a maximum of 50. Defaults to 20.

* * *
###### skip
_optional_

The number of results to skip per call, to be used for paging. Defaults to 0.

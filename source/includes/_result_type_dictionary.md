# Result Type Dictionary

Topic results follow a standard schema based on type regardless of the original source of the content.

## Article

```json
{
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
}
```

An article most likely from an RSS feed or posted on social media.  Contains the full content in both plain text and
HTML formatted.

| Field | Data Type | Description |
|---------|:-------:|:-----------|
| id | string | A unique identifier for the result |
| type | string | The type of the result |
| title | string | The article's title |
| description | string | An article summary or lede paragraph which may end with an ellipsis |
| full_text | string | If available the main contents of the article with HTML formatting and embedded media |
| plain_text | string | If available the main contents of the article without any tags or media |
| comments_url | string | If available a link to this article's comments |
| author | object | If available the name of the article's author |
| published_at | string | The date that the article was originally published in UTC |
| images | array | If available the article's main images |
| source | object | If the article came from social media this contains the information about the user that posted it |
| origin | object | Details about the website that hosts this article |

## Status

```json
{
  "id": "70f56ca07ccf01328e7156f4f15407e1",
  "type": "status",
  "description": "What are your plans for the New Year? #NYE2015",
   "published_at": "2014-31-12T17:42:11Z",
  "location": {
    "lat_lon": null,
    "street_address": null,
    "city": null,
    "region_name": null,
    "zipcode": null,
    "country": null,
    "country_code": null,
    "woeid": null,
    "latitude": null,
    "longitude": null
  },
  "source": {
    "id": "23213213",
    "name": "backstitch",
    "description": null,
    "url": "http://twitter.com/backstitch",
    "icon": {
      "url": "https://pbs.twimg.com/profile_images/488756158694318080/6BiMMFOf_400x400.png",
      "width": 400,
      "height": 400
    }
  },
  "origin": {
    "id": "2423423",
    "name": "Twitter",
    "url": "http://twitter.com",
    "icon": {
      "url": "http://images-backstitch.s3.amazonaws.com/next/service_catalog/twitter_icon.png",
      "width": 16,
      "height": 16
    }
  }
}
```

A short form user-generated message most likely posted on social media.

| Field | Data Type | Description |
|---------|:-------:|:-----------|
| id | string | A unique identifier for the result |
| type | string | The type of the result |
| description | string | The contents of the status message |
| published_at | string | The date that the status was originally posted in UTC |
| location | object | If available the geolocation of where the post was made |
| source | object | Details about the user that posted the message |
| origin | object | Details about the website that the user posted on |

## Photo

A photo most likely from a hosted service such as Flickr or posted to social media.

| Field | Data Type | Description |
|---------|:-------:|:-----------|
| id | string | A unique identifier for the result |
| type | string | The type of the result |
| description | string | A description or caption of the photo |
| published_at | string | The date that the photo was originally published in UTC |
| images | object | Different sizes of the photo available |
| location | object | If available the geolocation of where the photo was published from |
| comments_url | string | If available a link to this photo's comments |
| source | object | If available details about the user that posted the photo |
| origin | object | Details about the website that hosts this photo |

## Video

A video most likely from a hosted service such as YouTube or posted to social media.

| Field | Data Type | Description |
|---------|:-------:|:-----------|
| id | string | A unique identifier for the result |
| type | string | The type of the result |
| title | string | The title of the video |
| description | string | A longer description of the video |
| published_at | string | The date that the video was originally published in UTC |
| url | string | The direct url of the video |
| embed_code | string | Code to directly embed this video |
| images | array | If available preview images for the video |
| location | object | If available the geolocation of where the video was published from |
| comments_url | string | If available a link to this video's comments |
| source | object | If available details about the user that posted the video |
| origin | object | Details about the website that hosts this video |

## Product

A physical product most likely from an ecommerce or daily deal site.

| Field | Data Type | Description |
|---------|:-------:|:-----------|
| id | string | A unique identifier for the result |
| type | string | The type of the result |
| title | object | Contains both a short and long product name |
| description | object | Contains both a short and long product description |
| published_at | string | The date that the product was originally published in UTC |
| urls | object | Direct links to product information, reviews, and direct purchasing |
| images | array | A list of product images |
| price | object | The cost of the product |
| shipping_cost_ | object | If available the shipping cost of the product |
| fine_print | string | If available any additional fine-print details |
| model | string | If available the product model |
| manufacturer | object | If available the name the manufacturer and the url of their website |
| sku | string | If available the product's SKU |
| condition | string | If available whether or not the product is new or used |
| source | object | If available details about the user that posted this product |
| origin | object | Details about the website that is selling this product |

## Service

A professional service such as a restaurant.

| Field | Data Type | Description |
|---------|:-------:|:-----------|
| id | string | A unique identifier for the result |
| type | string | The type of the result |
| title | object | Contains both a short and long service name |
| description | object | Contains both a short and long service description |
| published_at | string | The date that this service was originally published in UTC |
| urls | object | Direct links to service information, reviews, and direct purchasing |
| images | array | A list of service images |
| location | object | If available the geolocation of where the service is available |
| price | object | The cost of the service |
| fine_print | string | If available any additional fine-print details |
| merchant | object | If available the name the merchant, their phone number, and the url of their website |
| source | object | If available details about the user that posted this service |
| origin | object | Details about the website that is selling this service |

## Hotel

A place that offers paid lodging.

| Field | Data Type | Description |
|---------|:-------:|:-----------|
| id | string | A unique identifier for the result |
| type | string | The type of the result |
| title | object | Contains both a short and long hotel name |
| description | object | Contains both a short and long hotel description |
| published_at | string | The date that this hotel was originally published in UTC |
| urls | object | Direct links to hotel information, reviews, and direct purchasing |
| images | array | A list of hotel images |
| location | object | If available the geolocation of where the hotel is available |
| price | object | The cost of the hotel |
| fine_print | string | If available any additional fine-print details |
| merchant | object | If available the name the hotel, their phone number, and the url of their website |
| source | object | If available details about the user that posted this hotel |
| origin | object | Details about the website that is selling lodging at this hotel |

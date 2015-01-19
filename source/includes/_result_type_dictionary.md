# Result Type Dictionary

Topic results follow a standard schema based on type regardless of the original source of the content.

<aside class="warning">
  API 2.0 changed the unique identifier to **id** from **uid** in API 1.0
</aside>


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

```json
{
  "id": "63dc7a6082460132f50d1aa7948f105d",
  "type": "photo",
  "description": "#MadCatz L.Y.N.X. 9 – a #transforming #controller for your #Android #devicesSee here- http://in.gamerekon.com/?p=3824",
  "published_at": "2015-01-19T12:49:25+00:00",
  "images": {
    "thumbnail": {
      "url": "http://scontent-a.cdninstagram.com/hphotos-xaf1/t51.2885-15/s150x150/e15/10903762_787557491324190_1049615505_n.jpg",
      "width": 150,
      "height": 150
    },
    "full_size": {
      "url": "http://scontent-a.cdninstagram.com/hphotos-xaf1/t51.2885-15/e15/10903762_787557491324190_1049615505_n.jpg",
      "width": 640,
      "height": 640
    },
    "other": []
  },
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
    "id": "1596774574",
    "name": "gamerekonindia",
    "description": null,
    "url": "www.instagram.com/gamerekonindia",
    "icon": {
      "url": "https://igcdn-photos-h-a.akamaihd.net/hphotos-ak-xaf1/t51.2885-19/10852941_1570019279899463_61316027_a.jpg",
      "width": 150,
      "height": 150
    }
  },
  "origin": {
    "id": "901370557046947610_1596774574",
    "name": "instagram",
    "url": "http://instagram.com/p/yCT773x38a/",
    "icon": {
      "url": "http://images-backstitch.s3.amazonaws.com/next/service_catalog/instagram_icon.png",
      "width": "64",
      "height": "64"
    }
  },
  "comments_url": null
}
```

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

```json
{
  "id": "b322fa407d7c0132ccb81a238d96d9fe",
  "type": "video",
  "title": "Honest Trailers - Gone Girl",
  "description": "Screen Junkies approved! Watch feature-length movies for free on Break ►► <a href=\"http://brk.cm/MoviesonBreak\">http://brk.cm/MoviesonBreak</a>\nBecome a Screen Junkie! ►► <a href=\"http://bit.ly/sjsubscr\">http://bit.ly/sjsubscr</a>\nWatch more Honest Trailers ►► <a href=\"http://bit.ly/HonestTrailerPlaylist\">http://bit.ly/HonestTrailerPlaylist</a>\n\nGet ready to cower in terror as you relive David Fincher's married-people version of Fatal Attraction: Gone Girl.\n\nGot a tip? Email us ► <a href=\"mailto:tips@screenjunkies.com\">tips@screenjunkies.com</a>\nFollow us on Twitter ► <a href=\"http://twitter.com/screenjunkies\">http://twitter.com/screenjunkies</a>\nLike us on Facebook ► <a href=\"http://www.fb.com/screenjunkies\">http://www.fb.com/screenjunkies</a>\n\nVoiceover Narration by Jon: <a href=\"http://youtube.com/jon3pnt0\">http://youtube.com/jon3pnt0</a>\n\nTitle design by Robert Holtby\n\nOriginal music by Sean Motley\n\nSeries Created by Andy Signore <a href=\"http://twitter.com/andysignore\">http://twitter.com/andysignore</a> & Brett Weiner\nWritten by Dan Murrell, Spencer Gilbert, and Andy Signore\nEdited by Dan Murrell\n---\n\nLet us know in the comments below what movie or TV show you want to see next!"
  "published_at": "2015-01-13T17:53:20Z",
  "url": "http://www.youtube.com/watch?v=l-1wldsq8_8",
  "embed_code": "<iframe type='text/html' src='http://www.youtube.com/embed/l-1wldsq8_8' width='640' height='360' frameborder='0' allowfullscreen='true'/>",
  "images": {
    "thumbnail": {
      "url": "https://i.ytimg.com/vi/l-1wldsq8_8/default.jpg",
        "width": 88,
        "height": 88
    },
    "full_size": {
      "url": "https://i.ytimg.com/vi/l-1wldsq8_8/hqdefault.jpg",
      "width": 480,
      "height": 360
    },
    "other": []
  },
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
    "id": "UCOpcACMWblDls9Z6GERVi1A",
    "name": "Screen Junkies",
    "description": "In a world full of movies and television, only one channel is keeping them honest every Tuesday and Thursday - SCREEN JUNKIES! \n\nHome of the epic Honest Trailers and The ScreenJunkies Show...it's the ScreenJunkies YouTube channel!  Enjoy our warped take on film & TV with a steady stream of pop-culture parody, original series, thoughtful commentary, and whatever we can think of next.\n\nTuesdays: Honest Trailers\nThursdays: Screen Junkies Show\nSundays: Movie Fights, Powered by Schmoes Know Network",
    "url": "http://www.youtube.com/channel/UCOpcACMWblDls9Z6GERVi1A",
    "icon": {
      "url": "https://yt3.ggpht.com/-YmAo2aa3-nM/AAAAAAAAAAI/AAAAAAAAAAA/WqpO7AUlJUM/s88-c-k-no/photo.jpg",
      "width": 88,
      "height": 88
    }
  },
  "origin": {
    "id": "l-1wldsq8_8",
    "name": "YouTube",
    "url": "http://www.youtube.com/watch?v=l-1wldsq8_8",
    "icon": {
      "url": "http://images-backstitch.s3.amazonaws.com/next/service_catalog/youtube_icon.png",
      "width": "16",
      "height": "16"
    }
  },
  "comments_url": null
}
```

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

```json
{
  "id": "ae2365d081f00132c59f72a99ca73d0a",
  "type": "product",
  "title": {
    "long": "$19 for the Batman Gotham Rising Fleece Blanket - Shipping Included",
    "short": null
  },
  "description": {
    "long": "<p>Batman is a favorite for both children and adults! What better way to express your love of the cartoon and film than with this warm fleece blanket. It measures 46&quot; x 60&quot; in size, and is made of 100% polyester. The blanket is an officially licensed product manufactured with superior quality by The Northwest Company. Get your warm and comfy blanket today <b>for $19, shipping included.</b></p>",
    "short": "Batman is a favorite for both children and adults! What better way to express your love of the cartoon and film than with this warm fleece blanket. It measures 46\" x 60\" in size, and is made of 100% polyester. The blanket is an officially licensed product manufactured with superior quality by The Northwest Company."
  },
  "published_at": "2015-01-19T09:00:00+00:00",
  "urls": {
    "info": "http://www.ncrowd.com/national/46484-avi-mfg-corp",
    "reviews": null,
    "purchase": null
  },
  "images": {
    "thumbnail": {
      "url": null,
      "width": null,
      "height": null
    },
    "full_size": {
      "url": "http://www.ncrowd.com/images/dynamic/deal/4/6/4/8/4/46484_lyMntF.png",
      "width": null,
      "height": null
    },
    "other": []
  },
  "price": {
    "value": "19",
    "display_value": null,
    "comparison_value": null,
    "iso_code": null,
    "name": null,
    "symbol": null
  },
  "fine_print": null,
  "model": null,
  "manufacturer": {
    "name": null,
    "url": null
  },
  "sku": null,
  "condition": null,
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
    "name": "Deal Find",
    "url": "http://www.ncrowd.com/national/46484-avi-mfg-corp",
    "icon": {
      "url": "http://images-backstitch.s3.amazonaws.com/next/service_catalog/dealfind_icon.png",
      "width": "16",
      "height": "16"
    }
  }
}
```

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

```json
{
  "id": "04e90fb07d1d0132aff626915c07c83a",
  "type": "service",
  "title": {
    "long": "$35 for $70 Toward Custom Dress Shirts from EPIC Shirtmakers ",
    "short": "50% Off Custom Dress Shirts"
  },
  "description": {
    "long": "<p></p>\n\n<h4>The Deal</h4>\n\n<ul>\n  <li>\n    <p>$35 for $70 toward <a href=\"http://epicshirtmakers.com/custom-tailored-dress-shirts\">custom dress shirts</a></p>\n  </li>\n  <li>\n    <p>Shirts start as low as $70 each.</p>\n  </li>\n</ul>",
    "short": "The Deal Shirts start as low as $70 each."
  },
  "full_text": null,
  "published_at": "2015-01-13T05:00:00Z",
  "urls": {
    "info": "http://www.groupon.com/deals/epic-shirtmakers-ann-arbor",
    "reviews": null,
    "purchase": "https://www.groupon.com/deals/epic-shirtmakers-ann-arbor/confirmation?pledge_id=12286850"
  },
  "images": {
    "thumbnail": {
      "url": "https://img.grouponcdn.com/deal/mXWCbsetzqqpp8gwBbUu/6Y-1500x900/v1/t50x50.jpg",
      "width": 50,
      "height": 50
    },
    "full_size": {
      "url": "https://img.grouponcdn.com/deal/mXWCbsetzqqpp8gwBbUu/6Y-1500x900/v1/t440x300.jpg",
      "width": 440,
      "height": 300
    },
    "other": []
  },
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
  "price": {
    "value": 35,
    "display_value": null,
    "comparison_value": null,
    "iso_code": null,
    "name": null,
    "symbol": null
  },
  "fine_print": "Limit 1 per person, may buy 2 additional as gifts. Limit 1 per order. Online only. $12.99 shipping fee for single shirt orders. <b>Free shipping on orders of two or more shirts.</b>",
  "merchant": {
    "name": "EPIC Shirtmakers",
    "phone_number": null,
    "url": "http://epicshirtmakers.com"
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
    "id": "epic-shirtmakers-ann-arbor",
    "name": "Groupon",
    "url": "http://www.groupon.com/deals/epic-shirtmakers-ann-arbor",
    "icon": {
      "url": "http://images-backstitch.s3.amazonaws.com/next/service_catalog/groupon_icon.png",
      "width": "16",
      "height": "16"
    }
  }
}
```

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

```json
{
  "id": "04996b507d300132ef4b32a97471a3dd",
  "type": "hotel",
  "title": {
    "long": "3-, 4-, or 7-Night Stay for Two in a One-Bedroom Villa at Acanto Boutique Hotel in Playa del Carmen, Mexico",
    "short": "4-Star Boutique Villas in Playa del Carmen"
  },
  "description": {
      "long": "<p></p>\n\n<h4>Four-Star Boutique Hotel Steps from Caribbean Sea</h4>\n\n<p>You won't see a car driving down Playa del Carmen's main thoroughfare, Quinta Avenida (or Fifth Avenue in English). Cars are off-limits here. Instead, live marimba musicians, pedestrians, fire-breathers, and vendors hawking handmade goods and Cuban cigars flood the cobblestone street. Less than a block from this lively main drag, the four-star Acanto Boutique Hotel puts you in prime position for exploring Playa del Carmen's Mayan architecture, checking out its hip nightlife, and kicking back on the Caribbean beaches that are just steps away.</p>\n\n<p>Tropical trees shade the hotel, which resembles a hacienda with wrought-iron terraces, arched windows, and an adobe façade. Walk down to the grotto-like courtyard to take a dip in a swimming pool surrounded by palm trees and stone siding, or head up to a rooftop hot tub to find ocean views. A marble bathroom, a terrace, and a full kitchen make each of the hotel's artfully designed one-bedroom villas feel luxurious and contemporary.</p>\n\n<p>If you want to pick up the pace, the concierge can set up eco-tours. Go scuba-diving along Playa del Carmen's massive barrier reef or swim with dolphins and teach them to whistle Creedence Clearwater Revival songs through their blowholes. You can also opt for horseback riding, ziplining through the jungle, or a day trip to the Mayan pyramid at Chichén Itzá.</p>\n\n<h4>Playa del Carmen, Mexico: Trendy Beach Area and Diving Destination</h4>\n\n<p>Just across the sea from the island of Cozumel, Playa del Carmen has been called \"the hippest city in all of the Yucatán Peninsula\" by Lonely Planet. The laid-back beach bars and cafés have a way of converting vacationers into expats, but Playa's most compelling draw might be its cenotes—cavernous sinkholes filled with turquoise pools. The water in the cenotes is crystal clear, particularly at the lily-pad-dotted Xlacah cenote, where you can snorkel among schools of colorful fish.</p>\n\n<p>To the south, you'll find preserved ruins of pre-Columbian cities. <a href=\"http://www.groupon.com/articles/tulum-mexico-swim-next-to-ancient-mayan-ruins-ga\">Tulum's</a> crumbling temples are situated above a dramatic ocean bluff, and Coba's enormous pyramid rises between two lagoons. For a fun day trip, hop aboard the ferry to Cozumel, which docks about a 15-minute walk from the hotel at the pier east of Calle 1. There are about a dozen dive shops on Cozumel, and they offer trips offshore to the reefs that Jacques Cousteau declared some of the world's most beautiful.</p>\n\n<hr />\n\n<h3>Frequently Asked Questions</h3>\n\n<p><strong>1. What is the best way to travel to the hotel from the airport?</strong> A shuttle from Cancún International Airport (CUN) is available for $140 roundtrip for up to six people.<br /></p>\n\n<p><strong>2. Is there an additional occupancy fee, or do I have to purchase another Groupon?</strong> The Groupon covers two guests. Adding an occupant above standard is $75 per night for an additional guest 13 or older; $55 per night for an additional guest 3–12; a kid 2 or younger stays free.<br /></p>\n\n<p><strong>3. Will I be approached to attend a timeshare sales presentation?</strong> Groupon customers are never obligated to attend a sales presentation. If you are approached and decline a presentation, you will not lose the value of your Groupon or have to pay additional fees.<br /></p>\n\n<p><strong>4. Which activities and amenities are included in the resort credits?</strong> Resort credits are not included with the Groupon.<br /></p>\n\n<p><strong>5. Are dinner reservations required for restaurants? Is there a dress code?</strong> For information regarding your dining options, please click <a href=\"http://www.acantohotels.com/dining/playa-del-carmen-dining-overview.htm\">here</a> or call 888-331-2177.<br /></p>\n\n<p><em>Love to travel? Follow us on <a href=\"http://gr.pn/17RUxNX\">Facebook</a> and <a href=\"http://gr.pn/1e9KPhk\">Twitter</a> for travel tips, inspiration, and photos from around the world.</em></p>",
      "short": "You won't see a car driving down Playa del Carmen's main thoroughfare, Quinta Avenida (or Fifth Avenue in English). Cars are off-limits here. Instead, live marimba musicians, pedestrians, fire-breathers, and vendors hawking handmade goods and Cuban cigars flood the cobblestone street. Less than a block from this lively main drag, the four-star Acanto Boutique Hotel puts you in prime position for exploring Playa del Carmen's Mayan architecture, checking out its hip nightlife, and kicking back on the Caribbean beaches that are just steps away."
  },
  "published_at": "2015-01-13T06:00:00Z",
  "urls": {
    "info": "http://www.groupon.com/deals/ga-acanto-boutique-hotel-9",
    "reviews": "http://www.tripadvisor.com/Hotel_Review-g150812-d535230-Reviews-Acanto_Boutique_Hotel-Playa_del_Carmen_Yucatan_Peninsula.html#REVIEWS",
    "purchase": "https://www.groupon.com/deals/ga-acanto-boutique-hotel-9/confirmation?pledge_id=12223065"
  },
  "images": {
    "thumbnail": {
      "url": "https://img.grouponcdn.com/deal/YYeRx1sMmgiooQoWUBu/Hv-960x582/v1/t50x50.jpg",
      "width": 50,
      "height": 50
    },
    "full_size": {
      "url": "https://img.grouponcdn.com/deal/YYeRx1sMmgiooQoWUBu/Hv-960x582/v1/t440x300.jpg",
      "width": 440,
      "height": 300
    },
    "other": []
  },
  "location": {
    "lat_lon": [
        20.6285958,
        -87.0695653
    ],
    "street_address": "  ",
    "city": "",
    "region_name": "",
    "zipcode": "",
    "country": "Mexico",
    "country_code": null,
    "woeid": null,
    "latitude": 20.6285958,
    "longitude": -87.0695653
  },
  "price": {
    "value": 599,
    "display_value": null,
    "comparison_value": null,
    "iso_code": null,
    "name": null,
    "symbol": null
  },
  "fine_print": "Must book by 3/13/15 or promotional value expires. Travel 1/18/15–3/31/15 or 4/1/15–8/31/15. Limit 1 per person, may buy 2 additional as gifts. Limit 1 per visit. Valid only for option purchased. Reservation required, subject to availability. 30-day cancellation notice required or fee up to the Groupon price applies. Must be 21+ to check in. Credit card required at booking and check-in. Must use promotional value in 1 visit. Not valid with reward points. $250 refundable credit card authorization required as security deposit at check-in. 19% tax not included.\n",
  "merchant": {
    "name": "Acanto Boutique Hotel",
    "phone_number": "888-331-2177",
    "url": "http://www.acantohotels.com/"
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
    "id": "ga-acanto-boutique-hotel-9",
    "name": "Groupon Getaway",
    "url": "http://www.groupon.com/deals/ga-acanto-boutique-hotel-9",
    "icon": {
      "url": "http://images-backstitch.s3.amazonaws.com/next/service_catalog/groupon_icon.png",
      "width": "16",
      "height": "16"
    }
  }
}
```

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

#backstitch API Documention

## Base url: api.backstit.ch


### details
	GET /v1/topic/details.json

##### Parameters
* * * 
###### token
_required_

To obtain a token, you must first log into backstitch and from with inisde the topic editor set the topic to allow api calls.  This will generate a secure token to identify the topic.

#### Detail Example
	{
		uid: 821,
		name: "feed test",
		description: null,
		banner: {
			url: "http://images-backstitch.s3.amazonaws.com/next/defaults/banner_3.jpg",
			width: 650,
			height: 240
		},
		api_token: "dsjhafjksahdfkjsadfshdfjs786",
		filters: [
			{
				uid: 56,
				phrase: "test"
			}
		],
		feeds: [
			{
				uid: 13624,
				name: "CNN",
				icon: {
					url: "http://images-backstitch.s3.amazonaws.com/next/service_catalog/cnn_icon.png",
					width: "16",
					height: "16"
				},
				banner: {
					url: "http://images-backstitch.s3.amazonaws.com/next/service_catalog/cnn_banner.jpg",
					width: "650",
					height: "240"
				},
				service_name: "RSS",
			},
			{
				uid: 13666,
				name: "Tweets tagged test",
				icon: {
					url: "http://images-backstitch.s3.amazonaws.com/next/service_catalog/twitter_icon.png",
					width: "16",
					height: "16"
				},
				banner: {
					url: "http://images-backstitch.s3.amazonaws.com/next/service_catalog/twitter_banner.jpg",
					width: "650",
					height: "240"
				},
				service_name: "Twitter",
			}
		]
	}


- - -

### fetch topic
	GET /v1/topic/fetch.json

##### Parameters
* * * 
###### token
_required_

To obtain a token, you must first log into backstitch and from with inisde the topic editor set the topic to allow api calls.  This will generate a secure token to identify the topic.

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
	GET /v1/topic/filter.json

##### Parameters
* * * 
###### token
_required_

To obtain a token, you must first log into backstitch and from with inisde the topic editor set the topic to allow api calls.  This will generate a secure token to identify the topic.

* * * 
###### term
_required_

This will return results that are most relevant to the passed term.  A "quoted term" will filter only results that match the phrase completely.

* * *
###### count
_optional_

The number of results to return per call, up to a maximum of 50. Defaults to 20.

* * *
###### skip
_optional_

The number of results to skip per call, to be used for paging. Defaults to 0.


## Result Examples

### article

	{
		id: "sdjfhsakjdhfuewfbjdsf843857349857",
		type: "article",
		title: "Eidetic Helps You Remember Anything Through Repetition",
		description: "iOS: Remembering random tidbits of information like a new phone number, a dictionary definition, or a quote is tough for a lot of us.",
		full_text: "<p>iOS: Remembering random tidbits of information like a new phone number, a dictionary definition, or a quote is tough for a lot of us.</p> <p><a href='http://eideticapp.com/'>Eidetic</a> is an app that makes remembering a little easier by repeatedly sending notifications at specific intervals.</p>",
		plain_text: "iOS: Remembering random tidbits of information like a new phone number, a dictionary definition, or a quote is tough for a lot of us. Eidetic is an app that makes remembering a little easier by repeatedly sending notifications at specific intervals.",
		author: {
			name: "Thorin Klosowski"
		},
		published_at: "2014-01-14T00:00:00Z",
		images: {
			thumbnail: {
				url: null,
				width: null,
				height: null
			},
			full_size: {
				url: "http://imgskljfsjdf.jpg",
				width: null,
				height: null
			},
			other: [ ]
		},
		source: {
			id: null,
			name: null,
			description: null,
			url: null,
			icon: {
				url: null,
				width: null,
				height: null
			}
		},
		origin: {
			id: null,
			name: "Life Hacker",
			url: "http://lifehacker.com",
			icon: {
				url: "http://images-backstitch.s3.amazonaws.com/next/service_catalog/lifehacker_icon.png",
				width: "16",
				height: "16"
			}
		}				
	}
	
### status

	{
		id: "3984756jfdkgh3q48ytjf",
		type: "status",
		description: "On the plane to JFK",
		published_at: "2014-01-13T20:17:11Z",
		location: {
			lat_lon: null,
			street_address: null,
			city: null,
			region_name: null,
			zipcode: null,
			country: null,
			country_code: null,
			woeid: null,
			latitude: null,
			longitude: null
		},
		source: {
			id: 34857384975,
			name: "Tammy",
			description: null,
			url: "http://facebook.com",
			icon: {
				url: "http://graph.facebook.com",
				width: 50,
				height: 50
			}
		},
		origin: {
			id: "djfsgh9384jdfgh8",
			name: "facebook",
			url: "http://facebook.com",
			icon: {
				url: "http://images-backstitch.s3.amazonaws.com/next/service_catalog/facebook_icon.png",
				width: "16",
				height: "16"
			}
		}
	}
	
### video

	{
		id: "sdncjkfh3487ryjsdfh9834ry",
		type: "video",
		title: "FASTER HORSES FESTIVAL",
		description: "",
		published_at: "2014-01-14T14:11:58Z",
		url: "https://www.youtube.com",
		embed_code: null,
		images: {
			thumbnail: {
				url: null,
				width: null,
				height: null
			},
			full_size: {
				url: "https:efgtdfger4534245.jpg",
				width: null,
				height: null
			},
			other: [ ]
		},
		location: {
			lat_lon: null,
			street_address: null,
			city: null,
			region_name: null,
			zipcode: null,
			country: null,
			country_code: null,
			woeid: null,
			latitude: null,
			longitude: null
		},
		source: {
			id: 4563456,
			name: "Natalie",
			description: null,
			url: "http://facebook.com",
			icon: {
				url: "http://graph.facebook.com",
				width: 50,
				height: 50
			}
		},
		origin: {
			id: "103300185_708917023474",
			name: "facebook",
			url: "https://www.youtube.com",
			icon: {
				url: "http://images-backstitch.s3.amazonaws.com/next/service_catalog/facebook_icon.png",
				width: "16",
				height: "16"
			}
		}
	}
	
### product

	{
		id: "jdsfh38945jkshdf983q4yr",
		type: "product",
		title: {
			long: "Kerafiber Hair Building Product",
			short: "Kerafiber Hair Building Product"
		},
		description: {
			long: "Kerafiber Hair Building Product Gives thinning hair a thicker appearance 100% natural organic keratin protein Adds volume Indistinguishable from natural hair, except to Superman",
			short: " Kerafiber Hair Building Product. Multiple Colors Available."
		},
		published_at: "2014-01-14T06:00:00Z",
		urls: {
			info: "http://www.groupon.com",
			reviews: null,
			purchase: "https://www.groupon.com"
		},
		images: {
			thumbnail: {
				url: "https://sjdhkf98q3yrkjsdhf.jpg",
				width: 50,
				height: 50
			},
			full_size: {
				url: "https://kdvjbhera8tyjksdhf.jpg",
				width: 440,
				height: 300
			},
			other: [ ]
		},
		price: {
			value: 12.99,
			display_value: null,
			comparison_value: null,
			iso_code: null,
			name: null,
			symbol: null
		},
		shiping_cost: {
			value: 12.99,
			display_value: null,
			comparison_value: null,
			iso_code: null,
			name: null,
			symbol: null
		},
		fine_print: "Limit 3 per person, may buy 2 more as gifts",
		model: null,
		manufacturer: {
			name: "Kerafiber Hair Building Product",
			url: ""
		},
		sku: null,
		condition: "new",
		source: {
			id: null,
			name: null,
			description: null,
			url: null,
			icon: {
				url: null,
				width: null,
				height: null
			}
		},
		origin: {
			id: "jdvnsldkfjhg-sdfkjhs",
			name: "Groupon Goods",
			url: "http://www.groupon.com",
			icon: {
				url: "http://images-backstitch.s3.amazonaws.com/next/service_catalog/groupon_icon.png",
				width: "16",
				height: "16"
			}
		}
	}
	
### service

	{
		id: "40a5a2a05f60013126cc60f8471fd7c2",
		type: "service",
		title: {
			long: "One or Three Self-Service Dog-Washing Sessions",
			short: "Up to 53% Off Self-Service Dog Washing"
		},		
		description: {
			long: "Although some dogs earn accolades by saving their owners' lives, others earn them by leaving muddy tracks leading to their evil owners' lairs. Clean up the trail with this Groupon. Choose Between Two Options $8 for one self-service dog-washing session (up to $17 value) $24 for three Groupons.",
			short: "Although some dogs earn accolades by saving their owners' lives, others earn them by leaving muddy tracks leading to their evil owners' lairs."
		},
		published_at: "2014-01-12T05:00:00Z",
		urls: {
			info: "http://www.groupon.com",
			reviews: "http://www.yelp.com",
			purchase: "https://www.groupon.com"
		},
		images: {
			thumbnail: {
				url: "https://jhsdf89y4.jpg",
				width: 50,
				height: 50
			},
			full_size: {
				url: "https://ijkxhcvjzxhcvjkzx.jpg",
				width: 440,
				height: 300
			},
			other: [ ]
		},
		location: {
			lat_lon: [
				null,
				null
			],
			street_address: " ",
			city: null,
			region_name: null,
			zipcode: null,
			country: null,
			country_code: null,
			woeid: null,
			latitude: null,
			longitude: null,
			lat_log: [
				42.5106195,
				-83.1787334
			]
		},
		price: {
			value: 8,
			display_value: null,
			comparison_value: null,
			iso_code: null,
			name: null,
			symbol: null
		},
		fine_print: "Limit 2 per person, may buy 1 additional as gift.",
		merchant: {
			name: "Scrubbers Self-Serve Dog Wash & Grooming",
			phone_number: "723-345-2345",
			url: "http://www.scrubbersdogwash.com/"
		}
		source: {
			id: null,
			name: null,
			description: null,
			url: null,
			icon: {
				url: null,
				width: null,
				height: null
			}
		},
		origin: {
			id: "hfgasdf-sadjkfhsdajk",
			name: "Groupon",
			url: "http://www.groupon.com",
			icon: {
				url: "http://images-backstitch.s3.amazonaws.com/next/service_catalog/groupon_icon.png",
				width: "16",
				height: "16"
			}
		}
	}
	
### hotel

	{
		id: "sdfhjwiuqery23jsdhf",
		type: "hotel",
		title: {
			long: "1-Night Stay with Dining Credit at The Capri Hotel in Ojai, CA",
			short: "Retro-Chic Hotel amid SoCal Mountains"
		},
		description: {
			long: "<h4>Top Reasons to Stay at The Capri Hotel</h4> <ul> <li>The chic hotel resides in the Ojai Valley, amid views of the Topa Topa Mountains and a short drive from the Pacific Ocean. </li> <li>From the retro sign outside to the lobby’s button-back white sofas, this boutique hotel exudes vintage style. But its recently overhauled <a href="http://www.hotelojai.com/gues_rooms.php">guest rooms</a> still have plenty of modern comforts, including 42-inch plasma TVs and iPod docking stations. Each room has a patio or balcony with expansive vistas of the mountains or the landscaped garden. </li> <li>Guests can access The Capri’s extensive DVD library of more than 400 titles. </li> <li>With this getaway, you get a $15 credit to use toward a meal at the nearby <a href="http://hotelojai.com/index.php/dining">Deer Lodge</a>, an Ojai standby since 1932.</li> <li>For a bit of R & R, indulge in a hot-stone <a href="http://hotelojai.com/index.php/spa-services">massage</a> or, weather permitting, take a dip in the outdoor pool. </li> <li>Less than five minutes away, downtown Ojai is lined with teahouses, boutiques, and art galleries. <p></li> </ul>",
			short: "The chic hotel resides in the Ojai Valley, amid views of the Topa Topa Mountains and a short drive from the Pacific Ocean."
		},
		published_at: "2014-01-07T08:00:00Z",
		urls: {
			info: "http://www.groupon.com",
			reviews: "http://www.expedia.com"
		},
		images: {
			thumbnail: {
				url: "https://skjdhfas84.jpg",
				width: 50,
				height: 50
			},
			full_size: {
				url: "https://kjzhgfea978ytjhdfjpg",
				width: 440,
				height: 300
			},
			other: [ ]
		},
		location: {
			lat_lon: null,
			street_address: "1180 East Ojai Avenue",
			city: null,
			region_name: null,
			zipcode: null,
			country: null,
			country_code: null,
			woeid: null,
			latitude: null,
			longitude: null,
			lat_log: [
				34.449057,
				-119.232622
			]
		},
		fine_print: "Must book by 3/7/14 or promotional value expires. Must complete travel by 4/30/14.",
		price: {
			value: 79,
			display_value: null,
			comparison_value: null,
			iso_code: null,
			name: null,
			symbol: null
		},
		merchant: {
			name: "The Capri Hotel",
			phone_number: "987-234-3456",
			url: "http://www.hotelojai.com/"
		}
		source: {
			id: null,
			name: null,
			description: null,
			url: null,
			icon: {
				url: null,
				width: null,
				height: null
			}
		},
		origin: {
			id: "kjdfhg-dfgkjh",
			name: "Groupon Getaway",
			url: "http://www.groupon.com",
			icon: {
				url: "http://images-backstitch.s3.amazonaws.com/next/service_catalog/groupon_icon.png",
				width: "16",
				height: "16"
			}
		}
	}

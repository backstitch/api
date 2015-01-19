# Widget 

The backstitch widget allows you to easily embed content on your blog or website. Using our lightweight widget, your topic's results can be displayed responsively anywhere that JavaScript is embeddable.  

Since the widget is responsive it will fit to the width of its container (and will expand from one column to two or three).

<aside class="notice">The widget is built on top of the API 1.0 spec and each page view will count as a single API call according to your subscription plan.</aside>

## Using the Widget

To use simply paste the following code wherever your want your widget to appear.  

`<script async type="text/javascript" src="https://api.backstit.ch/v1/topic/widget.js?count=10&token={TOPIC_TOKEN}&ref=encodeURIComponent(window.location.href)"></script>`

If you prefer to place the script tag in your page's `HEAD` section or if you are building the widget dynamically and appending to the DOM using Javscript reference the `container_id` parameter in the table below.

<aside class="success">This code works as a bootstrapper so it won't conflict with the loading of the rest of your page and will always load the latest version of the 1.0 widget.</aside>

### Widget URL Parameters

| Parameter | Required | Description |
|---------|:-------:|:-----------|
| token | Yes |The topic’s api token. |
| count | Yes | How many topic results to desplay. |
| ref | Yes | The url of the page loading the widget.  This is used so backstitch can provide you metrics on user engagement. |
| container_id | No | The id of the container to load the widget.  If not provided the widget will render wherever you place the bootstrap script. |




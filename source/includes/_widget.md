# Widget 

The backstitch widget allows you to easily embed content on your blog or website. Using our lightweight widget, your topic's results can be displayed responsively anywhere that JavaScript is embeddable.  

Since the widget is responsive it will fit to the width of its container (and will expand from one column to two or three).

<div class="widget-example">
  <script async type='text/javascript' src='https://api.backstit.ch/v1/topic/widget.js?count=4&token=cee55090c591013233444a64a6b89653&ref=encodeURIComponent(window.location.href)'>
  </script>
</div>

<aside class="notice">The widget is built on top of the API 1.0 spec and each page view will count as a single API call according to your subscription plan.</aside>

## Using the Widget

To use simply paste the following code wherever your want your widget to appear.  

`<script async type="text/javascript" src="https://api.backstit.ch/v1/topic/widget.js?count=10&token={TOPIC_TOKEN}&ref=encodeURIComponent(window.location.href)"></script>`

If you prefer to place the script tag in your page's `HEAD` section or if you are building the widget dynamically and appending to the DOM using Javscript reference the `container_id` parameter in the table below.

<aside class="success">This code works as a bootstrapper so it won't conflict with the loading of the rest of your page and will always load the latest version of the 1.0 widget.</aside>


### Opening Results 

Clicking on a result by default will open the link in a new window or tab (depending on your browser). Passing the "open_in_widget=true" parameter will cause results to open in a pop-up modal, never taking the user off your page where the widget is embedded. 

To close this modal once opened, the user can either press the escape key, click off the modal, or click the "X" in the upper-right corner of the modal. 

This modal can also be custom-styled by passing the "content_theme=none" parameter. 

### Widget URL Parameters

| Parameter | Required | Description |
|---------|:-------:|:-----------|
| token | Yes |The topic’s api token. |
| count | Yes | How many topic results to desplay. |
| ref | Yes | The url of the page loading the widget.  This is used so backstitch can provide you metrics on user engagement. |
| container_id | No | The id of the container to load the widget.  If not provided the widget will render wherever you place the bootstrap script. |
| on_click | No | A JavaScript method name that will be called when a result is clicked from the widget on your page. Method will be passed the result ID, result URL, result reference ID, result type, and a boolean telling whether the result has been scraped or not (in that order). |
| open_in_widget | No | Passing true will open results from the widget in a content viewer on the page rather than opening a new window. |
| card_theme='none' | No | Disables loading of the default style for the result cards, letting you supply your own. |
| content_theme="none" | No | Disables loading of the default stype for the content viewer, letting you supply your own. |
| theme="none" | No | Disables loading of the default style for both the cards and the content viewer, letting you supply your own. |

## Styling the Widget

By default the widget loads a responsive card layout similar to the native interface found on the [backstitch web app](http://backstit.ch).

### If you want to override this with your own styles you can either:

- Declare your styles using [!important](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity) 

- Turn off the default theme by passing the `theme="none"` URL parameter and supply your own styles.  You can download a sample blank [SASS](http://sass-lang.com/) template to [get you started](http://assets-api.s3.amazonaws.com/v1/custom_widget.scss).

### Source-Specific Styling

Each result in the widget also has an extra class at its root that denotes where it originally came from.  

While the default theme doesn't provide any style rules for these they are available if you wanted to style results different based on source.

| Root Classes |
|--------------|
| backstitch-twitter-result |
| backstitch-facebook-result |
| backstitch-instagram-result |
| backstitch-youtube-result |
| backstitch-linkedin-result |
| backstitch-news-result |
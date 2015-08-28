# jq-smart-banner
Custom global Smart App Banner with deeplink support for IOS and Android

[Smart App Banners](http://smartappbanners.com/) provides a uniformed way of promoting mobile apps when viewed in a mobile browser. This jquery plugin is owned by [jasny](https://github.com/jasny/jquery.smartbanner) and was modified a bit to cater a unified smart app banner UI and UX for both IOS and Android.

This plugin should be blended with a deeplink url to open a desired screen inside an app. For deeplink functionality, we will leverage on [hampusohlsson](http://github.com/hampusohlsson/browser-deeplink) deeplink and inject it when a user clicks the button to view or download the app inside the smart app banner

### Requirements:
* JQuery
* Slightly modified Smart App Banner JS by jasny
* Slightly modified Smart App Banner CSS by jasny
* hampusohlsson's browser-deeplink

## Usage:
```html
<html>
  <head>
    <title>Smart App Demo</title>
    <meta name="author" content="YOUR_COMPANY">
    <meta name="google-play-app" content="app-id=YOUR_GOOGLE_PLAY_APPID">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
	  <link rel="stylesheet" href="jquery.smartbanner.css" type="text/css" media="screen">
  </head>
  <body>
    Welcome to my Site
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.8/jquery.min.js"></script>
    <script src="jquery.smartbanner.js"></script>
	  <script src="browser-deeplink.js"></script>
	
    <script type="text/javascript">
        $(function () {
          if( /Android|webOS|iPhone|iPad|iPod/i.test(navigator.userAgent) ) {
        			deeplink.setup({
        						iOS: {
        							appName: "YOUR_APP_NAME",
        							appId: "XXXXXXX",
        						},
        						android: {
        							appId: "YOUR_ANDROID_PACKAGE"
        						}
        			});
        			$.smartbanner({ 
        				title:'YOUR_APP_NAME',
        				force:'android', //always force to use 
        				daysHidden: 0,
        				daysReminder: 0,
        				button: 'View in the <YOUR_APP_NAME> app',
        				inGooglePlay: '',
        				price: '',
        				url: '#',
        				icon: "URL_OF_YOUR_APP_ICON",
        				onInstall: function() {
        					deeplink.open("CUSTOM_SCHEME_URL_OF_YOUR_APP");
        			  },
        			});
      	  }
		});
    </script>
  </body>
</html>
```
### Demo

Download and open index.html





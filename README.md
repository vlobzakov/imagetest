# Signup Widget

<img align="right" width="100" height="100" src="http://www.fillmurray.com/100/100">
Following this guide you can create a one-click signup widget for your Jelastic PaaS platform and easily add it to any website.    

The widget is based on the standard HTML, JS, and CSS (available by default in all modern browsers), so it does not require any additional dependencies. Moreover, to avoid impacting the performance (i.e. page load speed), the initialization of the widget is performed in the background.   

In the image, you can check the default view of the widget during all of the stages: email address provisioning by a user, request processing, and operation success. The look and texts can be fully customized.   


# Widget Installation

Insert this code anywhere on the page, where you want to display the widget
```html
  <div class="jlc-wrapper"></div>
```

Get `jlcwidget.css` and `jlcwidget.js` files in the `dist` folder and put it in your template folder on the server.

Replace `PATH_TO_TEMPLATE` in the example below with your theme template path and insert it after `<head>` and before `</body>` tag anywhere in your theme template.

```html
  <script async src="PATH_TO_TEMPLATE/jlcwidget.js"></script>
  <link rel="stylesheet" href="PATH_TO_TEMPLATE/jlcwidget.css" media="none" onload="if(media!='all')media='all'">
```

# Widget Customisation

You can customize default button label or registration hoster.

To do this, add to `<div class="jlc-wrapper"></div>` next attributes:

- `data-text` - main button label
- `data-tx-success` - succes text
- `data-tx-error` - error text
- `data-key` - hoster domain

```html
  <div class="jlc-wrapper" data-text="GET STARTED FOR FREE" data-tx-success="CHECK YOUR EMAIL" data-tx-error="An error has occurred, please try again later" data-key="jelastichosting.nl"></div>
```

Also you can edit default label and hoster in the `assets/js/jlcwidget.js` file in "main variables" part

```JavaScript
  // main variables
  const jlc_button_text = jlcWrapper.getAttribute('data-text') || 'GET STARTED FOR FREE',
  jlc_text_error = jlcWrapper.getAttribute('data-tx-error') || 'An error has occurred, please try again later',
  jlc_text_success = jlcWrapper.getAttribute('data-tx-success') || 'CHECK YOUR EMAIL',
  jlc_hoster_domain = jlcWrapper.getAttribute('data-key') || 'jelastichosting.nl';
```

You can customise this widget with build system based on Gulp with [SCSS](https://sass-lang.com) preprocessor

### How to Build

Requires [Node.js](https://nodejs.org/) v6+ and [Gulp](https://gulpjs.com/) v4+ to run.

- Install Gulp: `npm install gulp --global`
- [Clone localy](https://confluence.atlassian.com/bitbucket/clone-a-repository-223217891.html) `git clone git@github.com:VitaliiAntoniukM/jelastic-widget.git`
- Go to project folder `cd jelastic-widget`
- Install dependencies `npm install -d`
- Run `gulp serve` to start the server and watch for changes
- Run `gulp default` to build for production environments

You can change CSS in the `assets/css/jlcwidget.scss` file, for example default variables

```scss
$color-blue : #0088fb; // default color (blue)
$color-green : #00bea7; // default color for green button
$color-gray : #efefef;
$color-medium : #6b758a;
$color-dark : #5e6981;
$color-red : red; // default error color

$bdrs: 10px; // button border radius
$width: 280px; // default button size (if you change it, pay attention to font-size of the `.jlc-btn` and `.jlc-input` selectors)
$font-family: 'Open Sans', sans-serif;
```

After build in the `dist` folder you will have

- `index.html` example with widget initialization selector
- `jlcwidget.js` minified JavaScript
- `jlcwidget.css` minified CSS

#### Change images

For the best performance all images saved in the SVG format, optimized with [svgomg service](https://jakearchibald.github.io/svgomg/) and included to the CSS/SCSS with BASE64 technology via [base64encode.org](https://www.base64encode.org/)

Non converted images you can find in `assets/img/` folder

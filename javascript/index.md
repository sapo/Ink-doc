---
layout: js-documentation
title: Javascript-powered UI Components
description: Create interactive pages, no javascript required!
site_root:  ../../
---

{% capture IframeHead %}
<head>
    <meta charset="utf-8">
    <script type="text/javascript" src="http://fastly.ink.sapo.pt/{{ site.version }}/js/ink-all.min.js"></script>
    <script type="text/javascript" src="http://fastly.ink.sapo.pt/{{ site.version }}/js/autoload.js"></script>
    <link rel="stylesheet" href="http://fastly.ink.sapo.pt/{{ site.version }}/css/ink-flex.css">
</head>
{% endcapture %}

Ink's vast array of UI components can be used in combination to create rich, interactive pages. They are many, and are very flexible. Javascript is not required for a lot of cases, but if you want to do more advanced stuff, you have to write some of it.

To get started, include the following JS files in the *bottom* of your HTML:

{% highlight html %}
<!-- Load the js files -->
<script type="text/javascript" src="http://fastly.ink.sapo.pt/{{ site.version }}/js/ink-all.js"></script>
<!-- Autoload is required for the examples on this page. Read more below. -->
<script type="text/javascript" src="http://fastly.ink.sapo.pt/{{ site.version }}/js/autoload.js"></script>
{% endhighlight %}


## Autoload

Although this is a page for Javascript-powered components, You will only find pure HTML elements on this page. That is because, thanks to Autoload (the `autoload.js` file you loaded above) you don't need to write any Javascript to do most things.

`autoload.js` is a small Javascript file that avoids a lot of boilerplate javascript to create the UI components on this page. It does so by initializing these elements automatically (`new Component(componentElement, options)`) based on their CSS class, so you don't have to.

If you want, you can disable this behaviour. Just add `data-autoload="false"` to elements without autoload, or don't include `autoload.js` at all to disable it completely.


## A note on option names (`data-option-name` vs `optionName`)

All configuration options, except callback functions, are available as data-attributes but are prefixed with `data-` and are written in lowercase and hyphen separated: `someOption` is the same as `data-some-option`.


## Using these components with Javascript instead of autoload

In this page, you see a lot of javascript-powered components created only with HTML, but sometimes you need the extra edge -- The power to create and destroy components any time you like, or to pass callbacks and arbitrary objects.

{% highlight javascript %}
// This is a simple example for Toggle.
// For other components, you can replace "Toggle" below with the component name.
Ink.requireModules(['Ink.UI.Toggle_1'], function (Toggle) {
    // Every component is a plain old Javascript class. Its constructor takes two arguments:
    // an element on the page and a set of options.
    new Toggle('#my-toggle', {
        target: '#toggled-element'  // This is the same as data-target="#toggled-element"
    });
});
{% endhighlight %}


<h2 id="Ink.UI.Carousel_1">
    Carousel
    <a class="fa fa-paragraph para-link" href="#Ink.UI.Carousel_1"></a>
</h2>

A responsive carousel with one or more slides per page. Cycle back and forth between slides with any content you can put in. You can also swipe back and forth with your finger if your device supports touch.

Most of the time, you will use this in conjunction with [Pagination](#Ink.UI.Pagination_1), because you want some sort of way to change pages!

### Carousel Examples

#### Basic example:

This example shows you how to create a basic Carousel, use it together with a basic [Pagination](#Ink.UI.Pagination_1). It's touch-enabled (touch support is on by default) and responsive (because it uses Ink's [CSS grid classes](/ui-elements/grid/#multiple-screen-sizes)). As you switch to smaller devices, you'll see that you get less slides per page to better use the viewport space.


{% capture Carousel %}
<div id="my-carousel-1" class="ink-carousel" data-pagination="#my-carousel-1-pagination">
    <ul class="stage column-group half-gutters">
        <li class="slide xlarge-33 all-50 small-100 tiny-100">
            <img class="quarter-bottom-space" src="http://lorempixel.com/400/200/sports/1">
            <div class="description">
                <h4>Title</h4>
                <p>Description paragraph</p>
            </div>
        </li>

        <li class="slide xlarge-33 all-50 small-100 tiny-100">
            <img class="quarter-bottom-space" src="http://lorempixel.com/400/200/sports/2">
            <div class="description">
                <h4>Title</h4>
                <p>Description paragraph</p>
            </div>
        </li>

        <li class="slide xlarge-33 all-50 small-100 tiny-100">
            <h4 class="vertical-space">Hello world!</h4>
            <p>Here is a form inside a Carousel:</p>
            <form class="ink-form">
                <input type="text" placeholder="just because!" />
                <button class="ink-button">Go!</button>
            </form>
        </li>

        <li class="slide xlarge-33 all-50 small-100 tiny-100">
            <img class="quarter-bottom-space" src="http://lorempixel.com/400/200/sports/3">
            <div class="description">
                <h4>Title</h4>
                <p>Description paragraph</p>
            </div>
        </li>
    </ul>
</div>

<nav id="my-carousel-1-pagination" class="ink-navigation">
    <ul class="pagination black">
    </ul>
</nav>
{% endcapture %}

<p class="example-title">Demo</p>
{{ Carousel }}

<p class="example-title">Code</p>
{% highlight html %}
{{ Carousel }}
{% endhighlight %}


#### Carousel with chevrons example

This is how you create a Carousel with chevron pagination.

To use a chevron [Pagination](#Ink.UI.Pagination_1) with it, embed the `.ink-pagination` element inside the `.ink-carousel` element and add the `chevron` class to its `ul`.

{% capture Carousel %}
<div id="my-carousel-2" class="ink-carousel" data-pagination="#my-carousel-2-pagination">
    <ul class="stage column-group half-gutters">
        <li class="slide all-50 small-100 tiny-100">
            <img class="quarter-bottom-space" src="http://lorempixel.com/400/200/sports/1">
            <div class="description">
                <h4>This is slide 1</h4>
            </div>
        </li>

        <li class="slide all-50 small-100 tiny-100">
            <img class="quarter-bottom-space" src="http://lorempixel.com/400/200/sports/2">
            <div class="description">
                <h4>This is slide 2</h4>
            </div>
        </li>

        <li class="slide all-50 small-100 tiny-100">
            <img class="quarter-bottom-space" src="http://lorempixel.com/400/200/sports/3">
            <div class="description">
                <h4>This is slide 3</h4>
            </div>
        </li>
    </ul>
    <nav id="my-carousel-2-pagination" class="ink-navigation">
        <ul class="pagination chevron">
        </ul>
    </nav>
</div>
{% endcapture %}

<p class="example-title">Demo</p>
{{ Carousel }}

<p class="example-title">Code</p>
{% highlight html %}
{{ Carousel }}
{% endhighlight %}


### Carousel options

Add the following attributes to your `.ink-carousel` element to configure your Carousel.

 * `data-pagination="<selector>"`: [Pagination](#Ink.UI.Pagination_1) element to use with this Carousel. *Don't forget this!*
 * `data-initial-page="<page>"`: Carousel starts in `page`. First page is 0.
 * `data-space-after-last-slide="false"`: Don't leave blank space after the last slide.
 * `data-swipe="false"`: Disable touch support.
 * `data-auto-advance="<time>"`: Auto-advance pages every `time` milliseconds.

You can read the list of options to create the Carousel with JS [here](/javascript/Ink.UI.Carousel/).


### Advanced Carousel stuff:

You can visit [the Carousel API docs](/javascript/Ink.UI.Carousel/) to find out about Javascript-only options, javascript methods, and how to create Carousels using Javascript


-------------


<h2 id="Ink.UI.Close_1">
    Close
    <a class="fa fa-paragraph para-link" href="#Ink.UI.Close_1"></a>
</h2>

Dismiss things.

Add the `ink-close` or `ink-dismiss` to elements. Those elements, when clicked, will be removed. Plays well with the [Alert UI Element](/ui-elements/alerts/).

### Close Example

Here's an example. Click the &times; sign to close the alert. When you do, the element will be removed from the page.

{% capture Close %}
<div class="ink-alert basic" role="alert">
    <button class="ink-dismiss">&times;</button>
    <p>Click the X to close this!</p>
</div>
{% endcapture %}

<p class="example-title">Demo</p>
{{ Close }}

<p class="example-title">Code</p>
{% highlight html %}
{{ Close }}
{% endhighlight %}


### Close options

(Close has no options)


### Advanced Close stuff:

There's not much to know about Close, but here are [the Close JS API docs](/javascript/Ink.UI.Close/).



-------------



<h2 id="Ink.UI.DatePicker_1">
    DatePicker
    <a class="fa fa-paragraph para-link" href="#Ink.UI.DatePicker_1"></a>
</h2>


DatePicker is a component for picking dates. You use it together with an input box, and it gets filled with the date in a certain format. The user may change the date by navigating the calendar or by typing in the input box using the correct format.

The date's format is given in the `data-format` option, where you pass a date format string in the syntax of [PHP's `date()` function](http://php.net/manual/en/function.date.php#refsect1-function.date-parameters).


### DatePicker Examples

#### Basic example

This is a simple DatePicker, mostly using the default options. It writes the dates in DD-MM-YYYY format.

{% capture DatePicker %}
<div class="ink-form">
    <div class="control-group column-group no-margin">
        <div class="control all-30">
            <input type="text" class="ink-datepicker" data-format="d-m-Y" />
        </div>
    </div>
</div>
{% endcapture %}

<p class="example-title">Demo</p>
{{ DatePicker }}

<p class="example-title">Code</p>
{% highlight html %}
{{ DatePicker }}
{% endhighlight %}


#### Ranged example

A DatePicker which only accepts dates between the birth of [Aníbal Cavaco Silva](https://en.wikipedia.org/wiki/An%C3%ADbal_Cavaco_Silva) and today.

{% capture DatePicker %}
<p>Pick a day in the life of Aníbal Cavaco Silva:</p>
<div class="ink-form">
    <div class="control-group column-group no-margin">
        <div class="control all-30">
            <input
                type="text"
                class="ink-datepicker"
                data-format="d-m-Y"
                data-date-range="1939-07-15:NOW" />
        </div>
    </div>
</div>
{% endcapture %}

<p class="example-title">Demo</p>
{{ DatePicker }}

<p class="example-title">Code</p>
{% highlight html %}
{{ DatePicker }}
{% endhighlight %}


#### Always-open example

This is a DatePicker that never closes. To do this, we set it to not be "shy" (that is, don't close automatically), and we told it to open automatically.

We also need to hide the "close" button so it doesn't close on us, and add some CSS so that it doesn't have `position: absolute`.

{% capture DatePicker %}
<div class="ink-form">
    <div class="control-group column-group no-margin">
        <div class="control all-30">
            <input
                type="text"
                class="ink-datepicker"
                data-css-class="ink-calendar my-never-closing-datepicker"
                data-format="d-m-Y"
                data-shy="false"
                data-auto-open="true"
                data-show-clean="false"
                data-show-close="false" />
        </div>
    </div>
</div>

<style>
.my-never-closing-datepicker {
    position: static;
    display: inline-block;
    overflow: hidden;
}
</style>
{% endcapture %}

<p class="example-title">Demo</p>
{{ DatePicker }}

<p class="example-title">Code</p>
{% highlight html %}
{{ DatePicker }}
{% endhighlight %}



### DatePicker options

Add the following attributes to your `.ink-datepicker` input element to configure your DatePicker.

#### Date options

 * `data-start-date="<yyyy>-<mm>-<dd>"`: Start with a certain date. Defaults to today.
 * `data-date-range="<start>:<end>"`: Only allow dates between `start` and `end`. Don't forget the `:` :).
 * `data-format="d-m-Y"`: Date format string. Uses the same syntax as [PHP's `date()` function](http://php.net/manual/en/function.date.php#refsect1-function.date-parameters). Let's see how they format the date "15th July of 1939":
   * `data-format="d-m-Y"` - "15-07-1939"
   * `data-format="Y/d/m"` - "1939/15/07"
   * `data-format="Y-m-d"` - "1939-07-15"

#### Text and formatting options:

 * `data-clean-text="<word>"`: Text for the "Clear" button.
 * `data-close-text="<word>"`: Text for the "Close" button.
 * `data-of-text="<of>"`: Text to show between month and year. Defaults to ' of '.
 * `data-next-link-text="<text>"`: Text for the next button. Defaults to '»'.
 * `data-prev-link-text="<text>"`: Text for the previous button. Defaults to '«'.
 * `data-start-week-day="<day>"`: First day of the week. Sunday is zero. Defaults to 1 (Monday).


#### Misc options

 * `data-show-clean="false"`: Hide the "Clear" button.
 * `data-show-close="false"`: Hide the "Close" button.
 * `data-auto-open="true"`: The DatePicker will be initially opened
 * `data-shy="false"`: Stop the DatePicker from closing itself automatically.
 * `data-css-class="ink-calendar <my classes>"`: Add classes to the DatePicker.
 * `data-on-focus="false"`: Add this if you don't want the DatePicker to open itself when you click the input.
 * `data-picker-field="<selector>"`: (if not using in an input[type="text"]) Element which displays the DatePicker when clicked. Defaults to an "open" link.
 * `data-position="right"`: Float the DatePicker to the right.


#### Options for using `<select>` elements instead of an `<input>` element.

Options to use DatePicker with `<select>` elements. They require `data-display-in-select="true"`.

 * `data-display-in-select="true"`: Enable this first.
 * `data-day-field="<selector>"`: `<select>` field with the days.
 * `data-month-field="<selector>"`: `<select>` field with the months.
 * `data-year-field="<selector>"`: `<select>` field with the years.


You can read the list of options to create the DatePicker with JS [here](/javascript/Ink.UI.DatePicker/).


### Advanced DatePicker stuff:

You can visit [the DatePicker API docs](/javascript/Ink.UI.DatePicker/) to find out about Javascript-only options, javascript methods, and how to create DatePickers using Javascript



-------------



## Draggable
TODO do Draggable docs



-------------



<h2 id="Ink.UI.Drawer_1">
    Drawer
    <a class="fa fa-paragraph para-link" href="#Ink.UI.Drawer_1"></a>
</h2>


Drawer is a component showing off-canvas menus which slide in when their toggle is clicked or touched. It's useful for saving precious screen real estate on devices with small screens.

It slides in from one of the sides, either pushing or going over (this is configurable) the page's content.

You need to place your entire page's content inside an element with the class `content-drawer`, so that it may be pushed aside.


### Drawer Examples

#### Basic example

This is a simple Drawer coming in from the left.

{% capture DrawerLeft %}
<body class="ink-drawer">
    <div class="left-drawer">
        Left drawer content...
    </div>
    <div id="main-content" class="content-drawer ink-grid">
        <a class="left-drawer-trigger" href="#">Open drawer</a>

        <h1>My page</h1>
        <p>
            Content of my page...
        </p>
    </div>
</body>
{% endcapture %}

<p class="example-title">Demo</p>
<iframe width="400" height="215" frameborder="0" scrolling="no" class="full-document-example-iframe highlight">
    {{ IframeHead }}
    {{ DrawerLeft }}
</iframe>

<p class="example-title">Code</p>
{% highlight html %}
{{ DrawerLeft }}
{% endhighlight %}


#### Two drawers example

This is an example of two drawers, one coming from the right and one from the left.

{% capture DrawerBoth %}
<body class="ink-drawer">
    <div class="left-drawer">
        Left drawer content...
    </div>
    <div class="right-drawer">
        Right drawer content...
    </div>
    <div id="main-content" class="content-drawer ink-grid">
        <a class="left-drawer-trigger" href="#">Open left drawer</a>
        <a class="right-drawer-trigger push-right" href="#">Open right drawer</a>

        <h1>My page</h1>
        <p>
            Content of my page...
        </p>
    </div>
</body>
{% endcapture %}

<p class="example-title">Demo</p>
<iframe width="400" height="215" frameborder="0" scrolling="no" class="full-document-example-iframe highlight">
    {{ IframeHead }}
    {{ DrawerBoth }}
</iframe>

<p class="example-title">Code</p>
{% highlight html %}
{{ DrawerBoth }}
{% endhighlight %}


#### `'over'` mode

This drawer goes over the page content, instead of pushing it.

{% capture DrawerOver %}
<body class="ink-drawer" data-mode="over">
    <div class="left-drawer" style="background:gray">
        <p>Left drawer content...</p>
        <p>I am over the main page content!</p>
    </div>
    <div id="main-content" class="content-drawer ink-grid">
        <a class="left-drawer-trigger" href="#">Open drawer</a>

        <h1>My page</h1>
        <p>
            Content of my page...
        </p>
    </div>
</body>
{% endcapture %}

<p class="example-title">Demo</p>
<iframe width="400" height="215" frameborder="0" scrolling="no" class="full-document-example-iframe highlight">
    {{ IframeHead }}
    {{ DrawerOver }}
</iframe>

<p class="example-title">Code</p>
{% highlight html %}
{{ DrawerOver }}
{% endhighlight %}


### Drawer options

 * `data-mode="over"` - Make the drawer go over the body instead of pushing it.
 * `data-sides="<side>"` - Make a drawer that comes in from this `side`. Can be 'left', 'right', or 'both'.
 * `data-content-drawer="#my-content-div"` - Your main page container.
 * `data-left-drawer=".my-left-drawer"` - Left drawer (the element that is placed offcanvas). This should be a sibling of your `data-content-drawer` element.
 * `data-left-trigger=".my-left-trigger"` - Left drawer trigger(s). When you click this trigger, the `leftDrawer` is shown.
 * `data-right-drawer=".my-right-drawer"` - Right drawer (the element that is placed offcanvas). This should be a sibling of your `data-content-drawer` element.
 * `data-right-trigger=".my-right-trigger"` - Right drawer trigger(s). When you click this trigger, the `rightDrawer` is shown.

### Advanced Drawer stuff:

You can visit [the Drawer API docs](/javascript/Ink.UI.Drawer/) to find out about Javascript-only options, javascript methods, and how to create Drawers using Javascript



-------------



## Dropdown
TODO do Dropdown docs


## Droppable
TODO do Droppable docs



-------------



<h2 id="Ink.UI.FormValidator_2">
    FormValidator_2
    <a class="fa fa-paragraph para-link" href="#Ink.UI.FormValidator_2"></a>
</h2>


FormValidator is a component which validates forms interactively on the client side before any data is sent to the server. By doing this, it provides a less waiting time, and a better experience to the user.

To use FormValidator, add the `.ink-formvalidator` class to a `<form>` element. Ink won't let the user submit until the data is valid.

You will probably need to read the [Forms UI Element](http://ink.sapo.pt/ui-elements/forms/) documentation to get to grips with the classes used. TL;DR: `.ink-form` goes outside, `.control-group` is nestable and groups similar controls, and `.control` wraps the inputs.

### FormValidator_2 Examples

#### Basic example

Here is a simple example of a user registration field:

{% capture FormValidator_2 %}
<form class="ink-form ink-formvalidator" method="post" action="#">
    <div class="control-group required">
        <label for="name">Name:</label>
        <div class="control">
            <input type="text" data-rules="required|text[true,false]" name="name" id="name" />
        </div>
    </div>
    <div class="control-group required">
        <label for="e-mail">Email:</label>
        <div class="control">
            <input type="text" name="e-mail" id="e-mail" data-rules="required|email" />
        </div>
    </div>
    <div class="control-group required">
        <label for="pass">Password: </label>
        <div class="control">
            <input type="password" name="password" id="pass" data-rules="required|min_length[8]" />
        </div>
    </div>
    <div class="control-group required">
        <label for="confpass">Confirm Password:</label>
        <div class="control">
            <input type="password" name="confpass" id="confpass" data-rules="matches[pass]" data-label="password confirmation" />
        </div>
    </div>
    <input type="submit" name="sub" value="Submit" class="ink-button success" />
</form>
{% endcapture %}

<p class="example-title">Demo</p>
{{ FormValidator_2 }}

**Note: The `required` class is related to the [Form UI Element](http://ink.sapo.pt/ui-elements/forms/). it doesn't affect the FormValidator's behaviour.**

<p class="example-title">Code</p>
{% highlight html %}
{{ FormValidator_2 }}
{% endhighlight %}


#### Required radio buttons and checkboxes

Here's how FormValidator deals with `<input type="radio">` and `<input type="checkbox">` inputs.

{% capture FormValidator_2 %}
<form class="ink-form ink-formvalidator column-group" method="post" action="#">
    <div class="all-50 small-100 tiny-100">
        <div class="control-group required">
            <p class="label">An offer you cannot refuse.</p>
            <ul class="control unstyled">
                <li>
                    <input type="radio" name="accept-offer" id="accept-offer-id" value="1" data-rules="required" data-label="Accept Offer" />
                    <label for="accept-offer-id">Okay!</label>
                </li>
                <li>
                    <input type="radio" name="accept-offer" id="refuse-offer-id" value="2" />
                    <label for="refuse-offer-id">No, thanks.</label>
                </li>
            </ul>
        </div>
    </div>
    <div class="all-50 small-100 tiny-100">
        <div class="control-group required">
            <p class="label">Here's a box you must absolutely check.</p>
            <ul class="control unstyled">
                <li>
                    <input type="checkbox" name="accept-tos" id="accept-tos-id" value="1" data-rules="required" data-label="Accept the TOS" />
                    <label for="accept-tos-id">I accept the Terms of Service of this website.</label>
                </li>
            </ul>
        </div>
    </div>
    <input type="submit" name="sub" value="Submit" class="ink-button success" />
</form>
{% endcapture %}

<p class="example-title">Demo</p>
{{ FormValidator_2 }}

**Note: The `required` class is related to the [Form UI Element](http://ink.sapo.pt/ui-elements/forms/). it doesn't affect the FormValidator's behaviour.**

<p class="example-title">Code</p>
{% highlight html %}
{{ FormValidator_2 }}
{% endhighlight %}


### FormValidator_2 options for each input

After adding the `.ink-formvalidator` class to your FormValidator, add these data-attributes to your form inputs (input, select, textarea...) to configure how they are validated.

Each field (`<input>`, `<select>`, `<textarea>`, etc.) which you want to validate in your form needs to have "rules". These rules define what can go and what can't go on this element. Read more on them in "Validation rules", below.

 * `data-rules="Field name in human-readable form"` - Rules for this field. Read more in the "Validation rules" section, below.
 * `data-label="Field name text"` - The name of this field. It is used to show in error messages. By default the label is the `name` attribute of your field.

### Validation rules

This is what you put in `data-rules` for each element. Here are a few examples of what you can do:

 * `data-rules="required"` - Must be filled in.
 * `data-rules="alpha"` - Just alphabetic characters (A to Z), lower case or upper case.
 * `data-rules="alpha_numeric"` - Like `alpha` but accepts numbers too!
 * `data-rules="credit_card"` - A credit card number.
 * `data-rules="email"` - A valid e-mail.
 * `data-rules="range[0,10]"` - Numbers (not exactly integers) between 0 and 10.
 * `data-rules="numeric[.]"` - A numeric field, using the `.` as a decimal separator. (Ex: "1.5")
 * `data-rules="numeric[.,2]"` - A numeric field with at most 2 decimal places. ("1.23" is okay but "1.234" is not)
 * `data-rules="numeric[.,2,4]"` - A numeric field with at most 2 decimal places and at most 4 digits on the left. ("1234.56" is okay but "12345.6" and "1234.567" are not)
 * `data-rules="integer"` - Only whole numbers.

You can combine these rules, like this:

 * `data-rules="required|number"` - A required number.
 * `data-rules="required|email"` - A required email.
 * `data-rules="integer|range[0,10]"` - A whole number between 0 and 10.

Some assorted rules which are useful in combination with other rules:

 * `data-rules="min_length[4]"` - Must have at least 4 characters.
 * `data-rules="max_length[4]"` - Can't have more than 4 characters.
 * `data-rules="exact_length[4]"` - Must have exactly 4 characters.

Random rules you might need:

 * `data-rules="color"` - A color in `#hex`, `rgb()`, `rgba()`, `hsl()`, `hsla()` format.
 * `data-rules="date[<format>]"` - A date. `format` is a date format string in the syntax of [PHP's `date()` function](http://php.net/manual/en/function.date.php#refsect1-function.date-parameters)
 * `data-rules="decimal[...]"` - Exactly like `numeric` but only decimal numbers are allowed.
 * `data-rules="ip[ipv6]"` - An IP address.
 * `data-rules="ip[ipv4]"` - A legacy IP address.
 * `data-rules="phone[PT]"` - A Portuguese phone number.
 * `data-rules="phone[CV]"` - A Cape Verde phone number.
 * `data-rules="phone[AO]"` - An Angolan phone number.
 * `data-rules="phone[MZ]"` - A Mozambique phone number.
 * `data-rules="phone[TL]"` - A Timor phone number.
 * `data-rules="phone"` - Any of the above types of phone number.
 * `data-rules="url"` - A URL. (Ex: `"/foo/bar"`, `"http://example.com/foo/bar"`, etc.)
 * `data-rules="url[true]"` - Just like `url` but only if it contains the "http://" part.

You can see more validation rules, as well as a more in-depth description of each one of them, in [the JS documentation for `FormValidator.validationFunctions`](/javascript/Ink.UI.FormValidator.2/#Ink_UI_FormValidator_2-FormValidator_validationFunctions)

### Advanced FormValidator_2 stuff:

You can visit [the FormValidator_2 API docs](/javascript/Ink.UI.FormValidator.2/) to find out about Javascript-only options, javascript methods, and how to use FormValidator using Javascript.



-------------



## ImageQuery
TODO do ImageQuery docs



-------------



<h2 id="Ink.UI.LazyLoad_1">
    LazyLoad
    <a class="fa fa-paragraph para-link" href="#Ink.UI.LazyLoad_1"></a>
</h2>



LazyLoad delays the downloading of images, showing them only when they get to the viewport. This is useful in optimizing image-heavy websites.

You can use the more advanced [Javascript API](/javascript/Ink.UI.LazyLoad) to load things other than images, such as widgets, videos, active content, etc.

While the images are loading or offscreen, their appearance will be a simple, more lightweight, placeholder. You can define what this placeholder using the `data-placeholder` option of the LazyLoad, about which you can learn about below, in "LazyLoad options for the container".

A LazyLoad is comprised of a *container* element, which can be your `<body>` if you like, with the class `.ink-lazyload`, and the *LazyLoad items*, with the class `.lazyload-item`, and with a `data-src` attribute instead of a `src` attribute.

It is recommended that you make sure, using CSS, that the images will take as much space after they loaded as before loading. In other words, reserve space for your images! This avoids weird scrolling issues.

### LazyLoad Examples

#### Load a few images

The images below will only load when you scroll

{% capture LazyLoad %}
<!-- the "data-delta" below is just so you can see the effect in the demo -->
<div class="ink-lazyload" data-delta="-150" data-placeholder="/assets/img/loading.gif">
    <p><img class="lazyload-item my-lazyloaded-image" data-src="/assets/img/meomusic.jpg"></p>
    <p><img class="lazyload-item my-lazyloaded-image" data-src="/assets/img/pessoa.jpg"></p>
    <p><img class="lazyload-item my-lazyloaded-image" data-src="/assets/img/codebits.jpg"></p>
    <p><img class="lazyload-item my-lazyloaded-image" data-src="/assets/img/sobre.jpg"></p>
    <p><img class="lazyload-item my-lazyloaded-image" data-src="/assets/img/videos.jpg"></p>
</div>
<style>
    .ink-lazyload .my-lazyloaded-image {
        height: 180px;  /* Reserve height to avoid weird scrolling issues */
        width: auto;
    }
</style>
{% endcapture %}

<p class="example-title">Demo</p>
{{ LazyLoad }}

<p class="example-title">Code</p>
{% highlight html %}
{{ LazyLoad }}
{% endhighlight %}



#### Add a CSS class to loaded images

When images are loaded, they will get a new CSS class and have a pretty fade-in!

{% capture LazyLoad %}
<!-- the "data-delta" below is just so you can see the effect in the demo -->
<div class="ink-lazyload" data-delta="-150" data-placeholder="/assets/img/loading.gif" data-loaded-class="loaded">
    <p><img class="lazyload-item loaded-class-example" data-src="/assets/img/meomusic.jpg"></p>
    <p><img class="lazyload-item loaded-class-example" data-src="/assets/img/pessoa.jpg"></p>
</div>
<style>
    .ink-lazyload .loaded-class-example {
        height: 180px;  /* Reserve height to avoid weird scrolling issues */
        width: auto;
        transition: opacity 2s ease;
        opacity: 0.2;
    }
    .ink-lazyload .loaded-class-example.loaded {
        opacity: 1;
    }
</style>
{% endcapture %}

<p class="example-title">Demo</p>
{{ LazyLoad }}

<p class="example-title">Code</p>
{% highlight html %}
{{ LazyLoad }}
{% endhighlight %}



### LazyLoad options for each lazily loaded item

 * `data-src="/my/image.png"` - The real source of the image, only loaded when the image is on screen.


### LazyLoad options for the container

 * `data-placeholder="/my-loading-spinner.gif"` - Placeholder value for items which are not 'visible', in case they don't already have a value set.
 * `data-loaded-class="loaded"` - Add the "loaded" class to the images when they're loaded.
 * `data-delta="100"` - Start loading the images 100px before they are on the screen.
 * `data-delta="-100"` - Start loading the images 100px *after* they are on the screen.
 * `data-delay="1000"` - Wait 1000 milliseconds (1 second) before showing the image.
 * `data-item=".my-crazy-selector"` - Find images by `.my-crazy-selector` instead of finding images with the `.lazyload-item` class.


### Advanced LazyLoad stuff:

You can visit [the LazyLoad API docs](/javascript/Ink.UI.LazyLoad/) to find out about Javascript-only options, javascript methods, and how to use LazyLoaders with Javascript. There's more advanced stuff that isn't covered here, like loading non-image elements with callbacks.



-------------



<h2 id="Ink.UI.Modal_1">
    Modal
    <a class="fa fa-paragraph para-link" href="#Ink.UI.Modal_1"></a>
</h2>



The Modal component allows you to overlay something on the entire page, possibly an error message that refers to the whole page, or a follow-up form or dialog to a submission process.



### Modal Examples

#### Open a simple modal

TODO examples

The images below will only load when you scroll

{% capture Modal %}
<div class="ink-shade fade">
    <div id="myModal" class="ink-modal fade" data-trigger="#myModalTrigger1" data-width="80%" data-height="80%" role="dialog" aria-hidden="true" aria-labelled-by="modal-title">
        <div class="modal-body" id="modalContent">
            <h3>This is the modal content</h3>
            <figure class="ink-image">
                <img src="http://lorempixel.com/1200/675/sports/1" alt="" class="ink-image">
            </figure>
        </div>
    </div>
</div>
<a href="#" id="myModalTrigger1" class="ink-button">Open example modal</a>
{% endcapture %}

<p class="example-title">Demo</p>
{{ Modal }}

<p class="example-title">Code</p>
{% highlight html %}
{{ Modal }}
{% endhighlight %}


#### A modal with a dismiss button, header, footer

Besides the content, this modal has a dismiss button, a header and a footer, besides the content.

{% capture Modal %}
<div class="ink-shade fade">
    <div id="myModal" class="ink-modal fade" data-trigger="#myModalTrigger2" data-width="80%" data-height="80%" role="dialog" aria-hidden="true" aria-labelled-by="modal-title">
        <div class="modal-header">
            <button class="modal-close ink-dismiss"></button>
            <h2 id="modal-title">This is the modal header</h2>
        </div>
        <div class="modal-body" id="modalContent">
            <h3>This is the modal content</h3>
            <figure class="ink-image">
                <img src="http://lorempixel.com/1200/675/sports/1" alt="" class="ink-image">
            </figure>
        </div>
        <div class="modal-footer">
            <div class="push-right">
                <!-- Anything with the ink-dismiss class will close the modal -->
                <button class="ink-button caution ink-dismiss">Close</button>
            </div>
        </div>
    </div>
</div>
<a href="#" id="myModalTrigger2" class="ink-button">Open example modal</a>
{% endcapture %}

<p class="example-title">Demo</p>
{{ Modal }}

<p class="example-title">Code</p>
{% highlight html %}
{{ Modal }}
{% endhighlight %}


#### An automatically opened modal

To automatically open the modal, add the `data-autodisplay="true"`.

{% capture Modal %}
<div class="ink-shade fade">
    <div id="myModal" class="ink-modal fade" data-auto-display="true" data-trigger="#myModalTrigger3" data-width="80%" data-height="80%" role="dialog" aria-hidden="true" aria-labelled-by="modal-title">
        <div class="modal-body" id="modalContent">
            <h3>This is the modal content</h3>
            <figure class="ink-image">
                <img src="http://lorempixel.com/1200/675/sports/1" alt="" class="ink-image">
            </figure>
        </div>
    </div>
</div>
<a href="#" id="myModalTrigger3" class="ink-button">Open example modal</a>
{% endcapture %}

<p class="example-title">Demo</p>
<iframe width="400" height="215" frameborder="0" scrolling="no" class="full-document-example-iframe highlight">
    {{ IframeHead }}
    <body>
        {{ Modal }}
    </body>
</iframe>

<p class="example-title">Code</p>
{% highlight html %}
{{ Modal }}
{% endhighlight %}



### Modal options

 * `data-trigger="#my-button"` - The modal will open when `#my-button` is clicked.
 * `data-width="600px"` - Make the modal 600px wide.
 * `data-height="400px"` - Make the modal 400px tall.
 * `data-width="40%"` - Make the modal width be 40% of the screen width.
 * `data-height="20%"` - Make the modal's height be 20% of the screen height.
 * `data-auto-display="true"` - Displays the Modal automatically when constructed.
 * `data-close-on-click="false"` - Don't close when the user clicks outside the modal.
 * `data-close-on-escape="false"` - Don't close the modal when <kbd>ESC</kbd> is pressed.
 * `data-responsive="false"` - Don't resize the modal when the screen is resized.


### Advanced Modal stuff:

You can visit [the Modal API docs](/javascript/Ink.UI.Modal/) to find out about Javascript-only options, javascript methods, and how to use Modals with Javascript and subscribe to their events.



-------------



## Pagination
TODO do Pagination docs


## ProgressBar
TODO do ProgressBar docs


## SmoothScroller
TODO do SmoothScroller docs


## SortableList
TODO do SortableList docs


## Spy
TODO do Spy docs


## Stacker
TODO do Stacker docs


## Sticky
TODO do Sticky docs


## Swipe
TODO do Swipe docs


## Table
TODO do Table docs


## Tabs
TODO do Tabs docs


## Toggle
TODO do Toggle docs


## Tooltip
TODO do Tooltip docs


## TreeView
TODO do TreeView docs


<script>
window.AUTOLOAD_CREATE_SMOOTH_SCROLLER = false;

Ink.requireModules(['Ink.UI.SmoothScroller_1', 'Ink.Dom.Css_1'], function (SmoothScroller, Css) {
    var paragraphs = Ink.ss('.para-link');
    for (var i = 0; i < paragraphs.length; i++) {
        paragraphs[i].setAttribute('data-margin', '48');  // 45 is the width of the top bar
        Css.addClassName(paragraphs[i], 'ink-smooth-scroll');
    }

    var iframes = Ink.ss('.full-document-example-iframe');
    for (var i = 0; i < iframes.length; i++) {
        iframes[i].setAttribute('src', 'data:text/html,' + iframes[i].textContent);
        iframes[i].setAttribute('frameBorder', '0');
        iframes[i].setAttribute('scrolling', 'no');
    }
});
</script>

<style>
.full-document-example-iframe {
    border: 0;
}
* > .para-link {
    display: none;
}
*:hover > .para-link {
    display: inline;
}
</style>

<!-- This is the only page in the docs that needs autoload -->
<script type="text/javascript" src="http://fastly.ink.sapo.pt/{{ site.version }}/js/autoload.js"></script>


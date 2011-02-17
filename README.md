# betterflow.js
This jQuery UI widget plugin provides (imho) a better implementation of the _coverflow_ effect, with the following features:

* Not bound on showing images. Any content can be _coverflowed_ (e.g., videos, arbitrary HTML);
* Ability to show a _back cover_ for each item;
* Simple HTML setup, with zero markup overhead;
* Supports mouse and keyboard events;
* Fully customisable (styling, events);
* 100% pure HTML+CSS (uses CSS3 transitions when possible);
* Fast;
* Small (5K, uncompressed).

**See a live example** with some [music album covers](http://ruidlopes.github.com/betterflow.js/).

# Setup

Add jQuery and jQuery UI to your HTML, e.g.:

	<script src="jquery.min.js" type="text/javascript" charset="utf-8"></script>
	<script src="jquery-ui.min.js" type="text/javascript" charset="utf-8"></script>

If you want mouse wheel (horizontal) interaction, add (Brandon Aaron's jQuery mousewheel plugin)[https://github.com/brandonaaron/jquery-mousewheel]:

	<script src="jquery.mousewheel.js" type="text/javascript" charset="utf-8"></script>

Afterwards, add the `betterflow.js` script and CSS:

	<script src="betterflow.js" type="text/javascript" charset="utf-8"></script>
	<link href="betterflow.css" type="text/css" rel="stylesheet" charset="utf-8">

# Usage

First, create your HTML structure with a wrapper element containing the class `betterflow`, and respective children that form the list of items to be displayed. Each child must contain two elements, one for its respective _front_ cover tagged with the `betterflow-front` class, and another for the _back_ cover with the `betterflow-back` class. All content must be contained inside these two elements. Example:

	<ul class="betterflow" id="example">
		<li>
			<div class="betterflow-front"><img src="http://userserve-ak.last.fm/serve/300x300/40625357.png"></div>
			<div class="betterflow-back">content item #1</div>
		</li>
		<li>
			<div class="betterflow-front"><img src="http://userserve-ak.last.fm/serve/300x300/47226415.png"></div>
			<div class="betterflow-back">content item #2</div>
		</li>
	</ul>

Afterwards, make the wrapper element become a `betterflow` widget, e.g.:

	$("#example").betterflow();

> **Note:** do not forget to properly set the dimension of your HTML elements.

## Dynamic content

If, for any reason, you manipulate the content of the wrapper element (e.g., adding and/or deleting children), you need to _destroy_ and _recreate_ the widget. Example:

	$("#example").betterflow("destroy").betterflow();

## Events

Interacting with a `betterflow` widget is made through jQuery's event publishing and subscription.

### betterflow-selected

This event is triggered by a `betterflow` widget when a new item is selected. The current position is passed to the event. It is 1-index based. Example:

	$("#example").bind("betterflow-selected", function(e, i) {
		console.log("selected position " + i);
	});

### betterflow-select

This event can be triggered to make a `betterflow` widget select a specific item by position. The position must be passed as an array parameter to the jQuery `trigger` function. Example:

	$("#example").trigger("betterflow-select", [1]);

### betterflow-prev

This event can be triggered to make a `betterflow` widget move to the previous item. Example:

	$("#example").trigger("betterflow-prev");

### betterflow-next

This event can be triggered to make a `betterflow` widget move to the next item. Example:

	$("#example").trigger("betterflow-next");

### betterflow-flip

This event can be triggered to make a `betterflow` widget flip the current item. Example:

	$("#example").trigger("betterflow-flip");

# Customisation

The `betterflow` widget can be customised in two fronts: _options_, and _styling_:

## Options

The following options are available:

* `childSelector`: a CSS selector for `betterflow` children (defaults to `> *`)
* `position`: the initial child to be presented as selected (defaults to `1`)
* `scaleFactor`: a value to determine the scaling of non-selected children (defaults to `10`)
* `marginFactor`: a value to determine the hiding value for non-selected children (defaults to `3`)

## Styling

You can override the `.betterflow`, `.betterflow > *`, `.betterflow-front`, `.betterflow-back`, and `.betterflow-flipped` to implement your own custom styling. Check the `betterflow.css` stylesheet for details.

# License (MIT)

Copyright (C) 2011 by Rui Lopes

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
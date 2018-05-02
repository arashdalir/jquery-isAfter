# Introduction
this small jquery plugin helps you to find which element comes first in the whole DOM tree. It compares elements' parents and can determine the location regardless of how deep the elements are.


## Why This Plugin?
There are some other solutions like [this one](https://stackoverflow.com/questions/7208624/check-if-element-is-before-or-after-another-element-in-jquery) which is prevAll() and nextAll() functions provided by jquery. The **problem is** that this functions work properly only if the 2 elements belong to the same parent:
```html
<!-- prevAll() works fine with:-->
<div class="test1">
	<p class="first">I'm first</p>
	<p class="second">I'm second</p>
</div>

<!-- prevAll() won't work with: -->

<div class="test2">
	<p>some irrelevant text 1</p>
	<p>some irrelevant text 2</p>
	<p class="first">I'm first</p>
	<div>
		<p class="second">I'm second</p>
		<p>some irrelevant text outside 1</p>
		<p>some irrelevant text outside 2</p>
	</div>
</div>
```

This plugin on the other hand checks the HTML tree of given elements, finds a common parent and then finds out which element or element's parent comes first in that common parent.

# Installation

## Dependencies
* jQuery (tested and developed with v 1.10.2)

## HowT
Download the package and extract it. the Copy the `isafter.query.js` *(and `jquery` if you don't already have jquery library installed)* and put it in your `js` scripts directory!

## Usage
Add script tags to `jQuery` and `isafter.jquery.js` to your HTML page:
```html
<html>
<head>
	<style type="text/css">
		.tests div,
		.tests p {
			margin:  2px 10px;
			padding: 5px;
			border:  1px solid #6699FF;
		}
	</style>
</head>
<body>
<script src="./js/jquery.1.10.2.js" type="text/javascript"></script>
<script src="./js/isafter.jquery.js" type="text/javascript"></script>
<script type="text/javascript">
	$(document)
		.ready(
			function (){
				var $elm1 = $(".test2 p.second");
				var $elm2 = $(".test2 p.first");
				console.log("isAfter: " + $elm1.isAfter($elm2) + ", prevAll: " + ($elm1.prevAll($elm2).length !== 0));
				// shows "isAfter: true, prevAll: false" in console
			}
		);
</script>
<div class="tests test2">
	<p>some irrelevant text 1</p>
	<p>some irrelevant text 2</p>
	<p class="first">I'm first</p>
	<div>
		<p class="second">I'm second</p>
		<p>some irrelevant text outside 1</p>
		<p>some irrelevant text outside 2</p>
	</div>
</div>
</body>
</html>
```

# Examples
There is an example file in the package, accessible under `/examples/index.html`.

# Licence
You are free to use this plugin in any application you like. I would appreciate it if a link to the source was included in your app, but well, if you don't want to, I cannot force you to do so.
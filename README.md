# rjs-jade

Provides the jade js api into a RequireJS environment.

**Jade version**: 0.8.0

## Installing (Bower)
```js
bower install --save rjs-jade
```

## Configuration
```js
	requirejs.config({
		'paths': {
			'jade': 'lib/jade'
		}
	});
```

## Example 1
```js
define(function (require, exports, module) {
	var jade = require('jade');
	var angular = require('angular');
	var headerTitle = require('./config').headerTitle;

	var tpl = jade.compile('h1 #{title}');
	var html = tpl({
		title: headerTitle
	});

	var myElement = angular.element('<div>');
	myElement.html(html);

	angular.element(document.body).append(myElement);
});
```

## Example 2
```js
require(['jade', './index-template.jade'], function (jade, indexTemplate) {
	var html = jade.render(indexTemplate);

	$(document.body).html(html);
});
```
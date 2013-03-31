# OneDollar-CoffeeScript

Implementation of the [$1 Gesture Recognizer](http://depts.washington.edu/aimgroup/proj/dollar/), a two-dimensional template based gesture recognition, for [jQuery](http://jquery.com/).


## About

The [$1 Gesture Recognizer](http://depts.washington.edu/aimgroup/proj/dollar/) is a research project by Wobbrock, Wilson and Li of the University of Washington and Microsoft Research. It describes a simple algorithm for accurate and fast recognition of drawn gestures.

Gestures can be recognised at any position, scale, and under any rotation. The system requires little training, achieving a 97% recognition rate with only one template for each gesture.

> Wobbrock, J.O., Wilson, A.D. and Li, Y. (2007). [Gestures without libraries, toolkits or training: A $1 recognizer for user interface prototypes](http://faculty.washington.edu/wobbrock/pubs/uist-07.1.pdf). Proceedings of the ACM Symposium on User Interface Software and Technology (UIST '07). Newport, Rhode Island (October 7-10, 2007). New York: ACM Press, pp. 159-168.


## Usage

### Plain-JavaScript

```html
<script src="onedollar.js"></script>	
```

```javascript
var one = new OneDollar();

one.add('triangle', [[137,139], [135,141], [154,160], [148,155] /* , ... */ ]);
one.add('circle', [[127,141] ,[124,140], [129,136], [126,139] /* , ... */ ]);
// one.remove('circle');

one.on('triangle', function(result){
	console.log(result);
});
one.on('circle', function(result){
	console.log(result);
});
// one.off('circle');

one.check([[99,231],[108,232], ... ,[153,232],[160,233]]);
```

### jQuery

The plugin works only with *touchstart*, *touchmove* and *touchend* events, so mobile touch devices.

```html
<script src="jquery.min.js"></script>
<script src="onedollar.js"></script>
<script src="jquery.onedollar.js"></script>
```

```javascript
$('#element').onedollar([
	['circle', [[127,141] ,[124,140], [129,136], [126,139] /* , ... */ ], function(result){
		alert('circle');
	}],
	['triangle', [[137,139], [135,141], [154,160], [148,155] /* , ... */ ], function(result){
		alert('triangle');
	}]
]);
```

I recommend you to use it with [Modernizr](https://github.com/Modernizr/Modernizr) and [RequireJS](https://github.com/jrburke/requirejs):

```javascript
if(Modernizr.touch===true){
	require(["jquery.min.js", "onedollar.min.js", "jquery.onedollar.min.js"], function($){
		$('#element').onedollar( /* ... */ );
	}
}
```

## License

The library is Open Source Software released under the [MIT License](https://raw.github.com/voidplus/onedollar-coffeescript/master/MIT-LICENSE.txt). It's developed by [Darius Morawiec](http://voidplus.de).
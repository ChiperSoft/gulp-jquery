gulp-jquery
===

A gulp plugin for creating custom jQuery builds via [jquery-custom](https://www.npmjs.com/package/jquery-custom).

##Installation

NPM: `npm install gulp-jquery`

##Usage

There are two ways to use `gulp-jquery`.  The first is to source the jQuery src folder from a local jquery install, such as from npm. This will build jQuery using exactly the version you have installed.

```js
var jquery = require('gulp-jquery');
gulp.task('jquery', function () {
	return gulp.src('./node_modules/jquery/src')
		.pipe(jquery({
			flags: ['-deprecated', '-event/alias', '-ajax/script', '-ajax/jsonp', '-exports/global']
		}))
		.pipe(gulp.dest('./public/vendor/'));
	// creates ./public/vendor/jquery.custom.js
});
```

The second is to use `gulp-jquery` as a file source itself. `jquery-custom` includes whatever the latest versions of jQuery 1 and 2 are at the time of install.

```js
var jquery = require('gulp-jquery');
gulp.task('jquery', function () {
	return jquery.src({
		release: 2, //jQuery 2
		flags: ['-deprecated', '-event/alias', '-ajax/script', '-ajax/jsonp', '-exports/global']
	})
	.pipe(gulp.dest('./public/vendor/'));
	// creates ./public/vendor/jquery.custom.js
});
```
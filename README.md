# [gulp](https://github.com/wearefractal/gulp)-cachebust

> Generates checksums and renames references to files


![Travis build status](https://travis-ci.org/jhuesos/gulp-cachebust.svg?branch=master)
![Dependency status](https://david-dm.org/jhuesos/gulp-cachebust.svg)
![MIT Licence](https://badges.frapsoft.com/os/mit/mit.svg?v=103)

Useful for cachebusting

*This plugin is only compatible with files that contain a stream, it only works in buffer mode.*

**This is the new repository for gulp-cachebust plugin**. The plugin was originaly created by Josiah Truasheim and it
has been transfered to this new repository ([link](https://github.com/Josiah/gulp-cachebust) to the previous one). 
Development will continue in this repository. 

## Install

Install with [npm](https://npmjs.org/package/gulp-cachebust)

```
npm install --save-dev gulp-cachebust
```

## Example

```js
var gulp = require('gulp');
var CacheBuster = require('gulp-cachebust');

var cachebust = new CacheBuster();

gulp.task('build-css', function () {
    return gulp.src('styles/*.css')
        // Awesome css stuff
        .pipe(cachebust.resources())
        .pipe(gulp.dest('dist/css'));
});

gulp.task('build-html', ['build-css'], function () {
    return gulp.src('templates/*')
        // Awesome html stuff
        .pipe(cachebust.references())
        .pipe(gulp.dest('dist'));
});
```


## API

### new CacheBuster(options)

#### options.checksumLength

*Optional*

Type: `Number`
Default: 8

#### options.random

Generates the checksum based on a random sha1 hash and not on the file contents.  
Useful for changing the file names on each deploy regardless if the content was changed or not.  

*Optional*  

Type: `Boolean`
Default: false

#### options.pathFormatter

Specify a custom formatting function for busted paths. The default will output
filenames like `/path/to/basename.[hash].ext`.

*Optional*

Type: `Function`
Default: null

An example for outputing a custom hash prefix:

```js
{
    pathFormatter: function(dirname, basename, extname, checksum) {
        return require('path').join(dirname, basename + '._v' + checksum + extname);
    }
}
```

### CacheBuster.resources()

Renames and collects resources according to their MD5 checksum.

### CacheBuster.references()

Rewrites references to resources which have been renamed according to their MD5
checksum.

## License

MIT © [Josiah Truasheim](//github.com/Josiah)

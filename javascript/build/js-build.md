#JS Build

##gulp + browserify

1. gulp는 grunt와 유사한 javascript 빌드 도구
2. browserify는 node.js에서 쓰던 모듈화 방식을 client side에서도 쓸 수 있도록 도와주는 도구
3. gulp와 browserify를 이용하면, browser에서 동작하는 javascript를 node.js 스타일의 모듈화 방식으로 작설할 수 있고, 흩어진 파일을 하나의 파일로 만들 수 있다.
4. browserify를 사용할 때, uglify를 이용하여 js파일을 minify 할 수 있다.
5. 또한, es6ify를 이용하여 traceur compile 단계를 추가해 es6 기능을 사용할 수 있다.
6. minify, es6ify 기능을 사용할 때, source map을 생성해서 browser에서는 원래의 js파일을 디버깅할 수 있다.
6. watchfy 기능을 이용하면, 개발 중에 파일이 변하면 자동으로 browserify가 동작하도록 한다.

### gulpfile.js 작성에 필요한 의존성
```sh
npm install bower lodash browserify gulp gulp-uglify gulp-sourcemaps gulp-clean bower-resolve resolve es6ify browserify vinyl-source-stream vinyl-buffer watchify --save-dev
```

### bower를 통해 필요한 library 추가
```sh
bower install jquery underscore --save
```

### gulpfile.js 작성
```js
'use strict';

var _ = require('lodash');
var fs = require('fs');
var gulp = require('gulp');
var browserify = require('browserify');
var source = require('vinyl-source-stream');
var buffer = require('vinyl-buffer');
var uglify = require('gulp-uglify');
var sourcemaps = require('gulp-sourcemaps');
var bowerResolve = require('bower-resolve');
var nodeResolve = require('resolve');
var es6ify = require('es6ify');

gulp.task('default', ['build-vendor', 'build-app']);

gulp.task('build-vendor', function () {

  var b = browserify({ debug: true });

  getBowerPackageIds().forEach(function (id) {
    var resolvedPath = bowerResolve.fastReadSync(id);
    b.require(resolvedPath, { expose: id });
  });

  return b.bundle().pipe(source('vendor.js'))
  .pipe(buffer())
  .pipe(sourcemaps.init({loadMaps: true}))
  .pipe(uglify())
  .pipe(sourcemaps.write())
  .pipe(gulp.dest('./public/dist'));
});

gulp.task('build-app', function () {
  es6ify.traceurOverrides = { blockBinding: true };
//  var b = browserify({ debug: true });
  var b = browserify({ debug: false });

  b.add(es6ify.runtime);
  b.add('./public/src/app/app.js');
  b.transform(es6ify);

  getBowerPackageIds().forEach(function (lib) {
    b.external(lib);
  });

  return b.bundle()
    .pipe(source('app.js'))
    .pipe(buffer())
    .pipe(sourcemaps.init({loadMaps: true}))
    .pipe(uglify())
    .pipe(sourcemaps.write())
   .pipe(gulp.dest('./public/dist'))

});

function getBowerPackageIds() {
  var bowerManifest = {};
  try {
    bowerManifest = require('./bower.json');
  } catch (e) {
  }
  return _.keys(bowerManifest.dependencies) || [];

}
```

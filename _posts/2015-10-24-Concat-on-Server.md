---
layout: post
title: Gulp to Concat and Uglify with Heroku Github Integration
---

Imagine you have set up Github integration on Heroku.  You'd like to concat and uglify your js files but you don't want those files showing up on Github.

First we will set up a Gulp task to concat and minify your javascript.  Be sure to include gulp, gulp-concat, gulp-uglify, and gulp-run in your package.json and require them in your code.

Make a task called gulp build that takes all your files in an array.  Use .pipe to concat them into a file with a name of your choice then pipe that into uglify.  We then pipe it to our destination folder.  Include that destination folder in .gitignore and refer to it in your index.js instead of your list of files.

We also need to create a task to run the server.  We use gulp-run to run this command: node index.js.  This will start our server.

{% highlight javascript %}
var gulp = require('gulp');
var concat = require('gulp-concat');
var uglify = require('gulp-uglify');
var run = require('gulp-run');

gulp.task('build', function() {
  return gulp.src(['file0.js', 'file1.js', 'file2.js'])
    .pipe(concat('starvingall.js'))
    .pipe(uglify({mangle: false}))
    .pipe(gulp.dest('./client/dist/'));
});

gulp.task('start', function() {
  run('node index.js').exec();
});

gulp.task('serve', ['build', 'start']);

{% endhighlight %}

Lastly, change your procfile to run gulp serve which will build and start your server.

web: node node_modules/gulp/bin/gulp serve

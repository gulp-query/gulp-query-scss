## gulp-query-scss
SCSS plugin for [gulp-query](https://github.com/gulp-query/gulp-query)

Uses [cssnano](http://cssnano.co/) with autoprefixer for optimization

This plugin provides automatic source maps, compiling Sass into CSS, autoprefixing and minification.
Write your CSS rules without vendor prefixes — autoprefixer will do everything itself

```
npm install gulp-query gulp-query-scss
```

### Example
Paste the code into your `gulpfile.js` and configure it
```javascript
let build = require('gulp-query')
  , scss = require('gulp-query-scss')
;
build((query) => {
    query.plugins([scss])
      .scss('src/scss/app.scss','css/','app')

      .scss('src/scss/admin.scss','css/undercover.css',{
        includePaths: [
          ...
        ]
      })

      .scss({
        from: 'src/scss/main.scss',
        to: 'css/',
        name: 'main'
      })
      ;
});
```
And feel the freedom
```
gulp
gulp --production // For production
gulp watch // Watching change
gulp scss // Only for scss
gulp scss:app // Only for app.scss
gulp scss:admin scss:main watch // Watching change only for admin.scss and main.scss
...
```

### Options
```javascript
.scss({
    name: "task_name", // For gulp scss:task_name 
    from: "scss/app.scss",
    to: "css/",
    source_map: true,
    source_map_type: 'inline',
    full: false, // if set true is without compress in prod
    includePaths: [
        //'../node_modules/compass-mixins/lib/', // relative path from gulpfile.js 
    ],
    autoprefixer: {
      browsers: ["> 1%", "last 2 versions"],
    }
})
```
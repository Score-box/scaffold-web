revInjector task
===

```javascript
grunt.registerTask('revInjector', function (target) {

  if (target == 'dist') {
    var obj = JSON.parse(require('fs').readFileSync('dist/assets.json'));
    var code = '';
    for (var key in obj) {
      code += ['rev[\'', key, '\']=\'', obj[key], '\';'].join('');
    }
    grunt.revInjector = code;
    console.log(grunt.revInjector);
  }
});

```

This task gets the assets.json file created by [grunt-filerev-assets](https://github.com/richardbolt/grunt-filerev-assets)

It creates a small javascript snippet injecting a revision converter accessible as a global getter ```R()```

example :

```javascript
R('/apple-touch-icon.png')			// '/apple-touch-icon.9727d3c2.png'
```

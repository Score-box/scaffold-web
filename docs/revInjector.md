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

#usage:

The object definition generated with revInjector is injected in the html file with [grunt-string-replace](https://github.com/eruizdechavez/grunt-string-replace)
It targets a certain string pattern : ```/*@@RINJECTION@@*/```

The code string injected only adds properties to a previously defined ```rev = {};``` object.

Copy paste this snippet to use the ```R()``` feature in js :

```html
<script type="text/javascript">
  !function(env) {
    'use strict';
    if (typeof module != "undefined" && module !== null && module.exports) module.exports = R();
    else if (typeof define === "function" && define.amd) define(R);
    else env.R = R();
    var rev={};/*@@RINJECTION@@*/
    function R () {
      return function (target) {
        if (rev[target])
          return rev[target];
        else
          return target;
      };
    }
  }(this);
</script>
```

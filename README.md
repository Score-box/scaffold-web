# scaffold-web

# installation :

```git clone https://github.com/score-box/scaffold-web```  
```cd scaffold-web```  
```git clone https://github.com/score-box/showcase-app app```

# development usage :

Unfortunately, watchify and grunt-contrib-watch don't get along...
So, launch both concurrently :

start watchify :
```npm run serve``` (verbose) or ```grunt browserify:alive```

start grunt serve :
```grunt serve```

# react

react files have to be named ```*.jsx``` in the folder ```app/scripts/react/```, the entrypoint is ```app.jsx``` and compiles to ```app.js```

Each react component must be exported, etc.

@TODO tuts [@showcase-app](https://github.com/Score-box/showcase-app)

# revision control

Revision of static assets, ie css, js and image files is handled by grunt plugins distributed with the default yeoman scaffold:

[usemin]()
[filerev]()

We added another plugin to create a revision table summary as a json file : assets.json, in the dist root.
[filerev_assets]()

We created a small untested and undebugged task to inject the content of this json in a html inline script: [see here](/docs/revInjector.md)
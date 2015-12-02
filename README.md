# scaffold-web

# revision control

Revision of static assets, ie css, js and image files is handled by grunt plugins distributed with the default yeoman scaffold:

[usemin]()
[filerev]()

We added another plugin to create a revision table summary as a json file : assets.json, in the dist root.
[filerev_assets]()

We created a small untested and undebugged task to inject the content of this json in a html inline script: [see here](/docs/revInjector.md)
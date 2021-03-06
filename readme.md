# Planet Maps

Custom builds of OpenLayers 3.

## Use

Install `planet-maps` as a dependency with [`npm`](http://nodejs.org/).

    npm install planet-maps --save-dev

Use [Browserify](http://browserify.org/) to `require` OpenLayers 3.

```js
// see below for a list of custom builds
var ol = require('planet-maps/dist/ol-base');
```

You'll also want to import the stylesheet:

```css
/* Make sure to use the path to your node_modules */
@import url('./node_modules/planet-maps/dist/ol.css');
```

## Builds

### `ol-base`

Support for vector and raster sources.  See `config/ol-base.json` for details on what is included.

### `ol-debug`

This is a debug build that should never be used in production.

## Publishing a new release

Edit the `config` files to include what you need exported and commit the changes.  Then you'll want to bump the version number in `package.json`, commit this change, and create a tag.  This should be done with the `npm version` command (choose one of `patch`, `minor`, or `major`).  E.g.

    npm version minor

Next you'll want to push your commits (and the tag) and publish your changes to npmjs.org.

    git push --tags origin master
    npm publish

Before publishing, the `prepublish` step will run `make`.  This will create builds in the `dist` directory that are *not* tracked by `git` but that are pushed to the npmjs.org repository for use by consuming packages.

Note the new version number in `package.json` and use it in packages that depend on this one.

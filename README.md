# favicons-plugin
Generate favicons with webpack!

# ![bootpack](thumbnail.png) &middot; [![GitHub release](https://img.shields.io/github/release/bootpack/favicons-plugin.svg)](https://GitHub.com/bootpack/favicons-plugin/releases/) [![Build Status](https://travis-ci.com/bootpack/favicons-plugin.svg?branch=master)](https://travis-ci.com/bootpack/favicons-plugin) [![GitHub license](https://img.shields.io/github/license/bootpack/favicons-plugin.svg)](https://github.com/bootpack/favicons-plugin/blob/master/LICENSE) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](https://github.com/bootpack/favicons-plugin/blob/master/.github/CONTRIBUTING.md) [![GitHub stars](https://img.shields.io/github/stars/bootpack/favicons-plugin.svg?style=social&label=Star&maxAge=2592000)](https://GitHub.com/bootpack/favicons-plugin/stargazers/)

Allows to use the [favicons](https://github.com/haydenbleasel/favicons) generator with webpack

Installation
------------

Install the plugin with npm:
```shell
$ npm i -D favicons-plugin
```

Basic Usage
-----------
Add the plugin to your webpack config as follows:

```javascript
let FaviconsPlugin = require('favicons-plugin')

...

plugins: [
  new FaviconsPlugin('my-logo.png')
]
```

This basic configuration will generate [37 different icons](https://github.com/bootpack/favicons-plugin/tree/master/test/fixtures/expected/default/icons-366a3768de05f9e78c392fa62b8fbb80) for iOS devices, Android devices and the Desktop browser out of your `my-logo.png` file.
It can optionally also generate a [JSON file with all information about the icons](https://github.com/bootpack/favicons-plugin/blob/master/test/fixtures/expected/generate-html/iconstats.json) for you.

If you are using with [html-webpack-plugin](https://github.com/ampedandwired/html-webpack-plugin) it will also inject the necessary html for you:

https://github.com/bootpack/favicons-plugin/blob/master/test/fixtures/expected/default-with-html/index.html

```html
  <link rel="apple-touch-icon" sizes="57x57" href="icons-366a3768de05f9e78c392fa62b8fbb80/apple-touch-icon-57x57.png">
  <link rel="apple-touch-icon" sizes="60x60" href="icons-366a3768de05f9e78c392fa62b8fbb80/apple-touch-icon-60x60.png">
  <link rel="apple-touch-icon" sizes="72x72" href="icons-366a3768de05f9e78c392fa62b8fbb80/apple-touch-icon-72x72.png">
  ...
  ...
  <link rel="apple-touch-startup-image" media="(device-width: 768px) and (device-height: 1024px) and (orientation: portrait) and (-webkit-device-pixel-ratio: 2)" href="icons-366a3768de05f9e78c392fa62b8fbb80/apple-touch-startup-image-1536x2008.png">
```


Advanced Usage
-----------

```javascript
plugins: [
  new FaviconsPlugin({
    // Your source logo
    logo: 'my-logo.png',
    // The prefix for all image files (might be a folder or a name)
    prefix: 'icons-[hash]/',
    // Emit all stats of the generated icons
    emitStats: false,
    // The name of the json containing all favicon information
    statsFilename: 'iconstats-[hash].json',
    // Generate a cache file with control hashes and
    // don't rebuild the favicons until those hashes change
    persistentCache: true,
    // Inject the html into the html-webpack-plugin
    inject: true,
    // favicon background color (see https://github.com/haydenbleasel/favicons#usage)
    background: '#fff',
    // favicon app title (see https://github.com/haydenbleasel/favicons#usage)
    title: 'Webpack App',

    // which icons should be generated (see https://github.com/haydenbleasel/favicons#usage)
    icons: {
      android: true,
      appleIcon: true,
      appleStartup: true,
      coast: false,
      favicons: true,
      firefox: true,
      opengraph: false,
      twitter: false,
      yandex: false,
      windows: false
    }
  })
]
```

## Contributing
Please contribute using [Gitflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow). Create a feature branch, add commits, and [open a pull request](https://github.com/bootpack/favicons-plugin/compare/).


## Support
Please [open an issue](https://github.com/bootpack/favicons-plugin/issues/new) for support.

## Special Thanks
This package was forked from [favicons-webpack-plugin (v0.0.9)](https://www.npmjs.com/package/favicons-webpack-plugin). I would like to extend thanks to the original maintainers for creating the package for which this one is based.

# Frequently Asked Questions

### Does this tool require that I use Laravel?

No. It has a few optimizations for Laravel, but it can be used for any project.

### My code isn't being minified.

Minification will only be performed, when your `NODE_ENV` is set to production. Not only will this speed up your compilation time, but it's also unnecessary during development. Here's an example of running Webpack for production.

```bash
export NODE_ENV=production && webpack --progress --hide-modules
```

It's highly recommended that you add the following NPM scripts to your `package.json` file.

```js
  "scripts": {
    "webpack": "cross-env NODE_ENV=development webpack --progress --hide-modules",
    "dev": "cross-env NODE_ENV=development webpack --watch --progress --hide-modules",
    "hmr": "cross-env NODE_ENV=development webpack-dev-server --inline --hot",
    "production": "cross-env NODE_ENV=production webpack --progress --hide-modules"
  },
```


### I'm using a VM, and Webpack isn't picking up my file changes.

If you're running `npm run dev` through a VM, you may find that file changes are not picked up by Webpack. If that's the case, update your NPM script to use the `--watch-poll` flag, rather than `--watch`. Like this:

```js
"scripts": {
    "dev": "NODE_ENV=development webpack --watch --watch-poll",
  }
```

### My manifest.json file shouldn't be in the project root.

If you're not using Laravel, your `manifest.json` file will be dumped into the project root. If you need to change this, call `mix.setPublicPath('dist/');`, and your manifest file will now be saved in that base directory.

### My project throws errors that it can't find `cross-env` or `webpack`

If you haven't already, install `webpack@2.2.0-rc3` and/or `cross-env@3.1.3` or higher, globally.

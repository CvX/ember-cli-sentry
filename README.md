ember-cli-sentry
================

An ember-cli addon adding [Sentry](https://www.getsentry.com) support.

Docs are available [here](http://damiencaselli.github.io/ember-cli-sentry/).

## Compatibility

- Node.js 6 or higher is required to use this addon
- Ember CLI 2.13 or higher is required to use this addon


## Install

```
ember install ember-cli-sentry
```

_Note: Since **v3.0.0**, `raven-js` package is automatically included by this addon._

## Configuration

### TLDR

```js
// config/environment.js

module.exports = function(environment) {
  var ENV = {

    /* config */

    sentry: {
      dsn: 'https://<dummykey>@app.getsentry.com/<dummyproject>'
    }
  }
}
```

### Complete config

```js
// config/environment.js

module.exports = function(environment) {
  var ENV = {

    /* config */

    sentry: {
      /**
       * The only mandatory parameter.
       *
       * @type {String}
       */
      dsn: 'https://<dummykey>@app.getsentry.com/<dummyproject>',

      /**
       * Sets Raven.debug property when running `Raven.config`.
       *
       * @type {Boolean}
       * @default true
       */
      debug: true,

      /**
       * If set to true, it will prevent Raven.js from being initialized.
       * Errors and logs will be logged to the console (default) instead of
       * being reported by Raven.
       *
       * @type {Boolean}
       * @default undefined
       */
      development: false,

      /**
       * If set to true, addon will try to have Ember.onerror
       * and Ember.RSVP.on('error') captured by Raven.
       *
       * @type {Boolean}
       * @default true
       */
      globalErrorCatching: true,

      /**
       * Raven.js option.
       *
       * @type {Array}
       * @default []
       */
      includePaths: [],

      /**
       * Raven.js option.
       *
       * @type {Array}
       * @default []
       */
      whitelistUrls: [],

      /**
       * Options to pass directly to Raven.js. Note: whitelistUrls and
       * includePaths in this will take precedence
       * over the above.
       *
       * @default {}
       */
      ravenOptions: {},
    }
  }
}
```

## Content Security Policy

To allow Ravenjs to work properly, you need to add a couple of thing to the content security policy rules:

```
'script-src': "'self' 'unsafe-inline' 'unsafe-eval'",
'img-src': "data: app.getsentry.com",
'connect-src': "'self' app.getsentry.com"
```

## Meaningless stack traces?

See [this issue](https://github.com/damiencaselli/ember-cli-sentry/issues/28).

## Example

The dummy application in tests is a working example with a couple of logging here and there, and a default logger.

## Dependencies

[Raven.js](https://github.com/getsentry/raven-js)

## Licence

[MIT](https://raw.githubusercontent.com/damiencaselli/ember-cli-sentry/master/LICENSE.md)

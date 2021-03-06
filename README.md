# Ember-cli-responsive

Ember CLI addon for using ember-responsive

[![Build Status](https://travis-ci.org/AVCEngineering/ember-cli-responsive.svg?branch=master)](https://travis-ci.org/AVCEngineering/ember-cli-responsive)

This README outlines the details of collaborating on this Ember addon. All contributions welcome!

## Usage

* `ember install ember-cli-responsive`

Import ember-cli-responsive module into your app.js and add responsive break points as below.

```js
import Ember from 'ember';
import Resolver from 'ember/resolver';
import loadInitializers from 'ember/load-initializers';
import config from './config/environment';
import 'ember-cli-responsive/responsive';

let App;

Ember.MODEL_FACTORY_INJECTIONS = true;

App = Ember.Application.extend({
  modulePrefix: config.modulePrefix,
  podModulePrefix: config.podModulePrefix,
  Resolver
});

App.responsive({
  media: {
    mobile:  '(max-width: 768px)',
    tablet:  '(min-width: 769px) and (max-width: 992px)',
    desktop: '(min-width: 993px) and (max-width: 1200px)',
    jumbo:   '(min-width: 1201px)'
  }
});

loadInitializers(App, config.modulePrefix);

export default App;
```

You can then query those breakpoints in your controllers, components, routes, and views:

```js
  this.get('media.isMobile'); // => true
```

The same is true in templates:

```
  {{#if media.isDesktop}}
    Desktop view!
  {{/if}}
```

## Polyfill with matchMedia

After running the above generator you can simply import via your project's ember-cli-build.js

```js
//ember-cli-build.js
app.import('bower_components/matchMedia/matchMedia.js');
```

## Installation

* `git clone` this repository
* `npm install`
* `bower install`

## Running

* `ember server`
* Visit your app at http://localhost:4200.

## Running Tests

* `npm test`

## Building

* `ember build`

For more information on using ember-cli, visit [http://www.ember-cli.com/](http://www.ember-cli.com/).

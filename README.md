# Archived

It was fun while it lasted, but we have to stop maintaining these repositories. We haven't used these projects for quite some time and maintaining them is becoming harder to do.

You deserve better, and for that reason we've decided to archive some repositories, which includes this one.

Feel free to fork and alter the repositories, and go forth making awesome stuff.

# aurelia-datatable

[![Build Status](https://travis-ci.org/SpoonX/aurelia-datatable.svg)](https://travis-ci.org/SpoonX/aurelia-datatable)
[![Gitter](https://img.shields.io/gitter/room/nwjs/nw.js.svg?maxAge=2592000?style=plastic)](https://gitter.im/SpoonX/Dev)

A data-table using [aurelia-orm](https://github.com/SpoonX/aurelia-orm) and [aurelia-pager](https://github.com/SpoonX/aurelia-pager)

Features:

* Pagination
* Sorting
* Integrated ORM
* Search
* Custom columns
* Custom button actions
* Custom valueConverters
* Expand data to view additional data
* And more

## Uses

Aurelia-datatable needs following plugins installed and configured:

* [aurelia-view-manager](https://www.npmjs.com/package/aurelia-view-manager)
* [aurelia-pager](https://www.npmjs.com/package/aurelia-pager)
* [aurelia-orm](https://www.npmjs.com/package/aurelia-orm).

## Documentation

You can find usage examples and the documentation [here](http://aurelia-datatable.spoonx.org/).

The [changelog](doc/changelog.md) provides you with information about important changes.

## Example
Here's a snippet to give you an idea of what this module supports.
### Online mode
```js
this.repository = entityManager.getRepository('users');
```

```html
  <datatable
      destroy.call="myEventCallback($event)"
      edit.call="myEditImplementation($event)"
      columns="id,name as 'username', user.id as 'User id'"
      repository.bind="repository"
      searchable
      sortable
      actions.bind="actions"
      populate="user"
      footer.bind="footer"
      detail-view="./details"
  ></datatable>
```

### Offline mode
```js
this.data = [{id: 1, name: 'Pipo'}, {id: 2, name: 'Mario'}];
```

```html
  <datatable
      destroy
      edit.call="myEditImplementation($event)"
      columns="id,name as 'username'"
      actions.bind="actions"
      footer.bind="footer"
      detail-view="./details"
      data.bind="data"
  ></datatable>
```
## Installation

### Aureli-Cli

Run `npm i aurelia-datatable --save` from your project root.

Aurelia-view-manager uses [homefront](https://www.npmjs.com/package/homefront), so add following to the `build.bundles.dependencies` section of `aurelia-project/aurelia.json`:

```js
"dependencies": [
  {
    "name": "homefront",
    "path": "../node_modules/homefront/dist",
    "main": "index"
  },
  {
    "name": "aurelia-datatable",
    "path": "../node_modules/aurelia-datatable/dist/amd",
    "main": "aurelia-datatable",
    "resources": [
      "bootstrap/datatable.html"
    ]
  },
  // ...
],
```

### Jspm

Run `jspm i aurelia-datatable` from your project root.

Aurelia-datatable uses [homefront](https://www.npmjs.com/package/homefront), so add following to the `bundles.dist.aurelia.includes` section of `build/bundles.js`:

```js
  "homefront",
  "aurelia-datatable",
  "[aurelia-datatable/**/*.js]",
  "aurelia-datatable/**/*.html!text",
```

If the installation results in having forks, try resolving them by running:

```sh
jspm inspect --forks
jspm resolve --only registry:package-name@version
```

### Webpack

Run `npm i aurelia-datatable --save` from your project root.

And add `aurelia-datatable` in the `coreBundles.aurelia` section of your `webpack.config.js`.

### Typescript

Npm-based installations pick up the typings automatically. For Jspm-based installations, run `typings i github:spoonx/aurelia-datatable` or add `"aurelia-datatable": "github:spoonx/aurelia-datatable",` to your `typings.json` and run `typings i`.

## Configuration

### Activate
Activate the plugin in `main.js`:

```js
export function configure(aurelia) {
  aurelia.use
    .standardConfiguration()
    .developmentLogging()
    .plugin('aurelia-datatable');

  aurelia.start().then(() => aurelia.setRoot());
}
```

### ORM
Follow the steps in the [aurelia-orm documentation](https://aurelia-orm.spoonx.org/quick-start.html) to configure your api endpoints.

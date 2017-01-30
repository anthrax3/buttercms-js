# ButterCMS node.js client

[![npm version](https://img.shields.io/npm/v/buttercms.svg)](https://www.npmjs.org/package/buttercms)

## Documentation

For a comprehensive list of examples, check out the [API documentation](https://buttercms.com/docs/api/).

## Installation

Requires node.js version 4 or greater.

```
npm install buttercms
```

## Overview

Every resource is accessed via your butter instance:

```js
var butter = require('buttercms')(' your butter API token ');
```

Every resource method returns a promise:

```js
// Get blog posts
butter.post.list({page: 1, page_size: 10}).then(function(response) {
  console.log(response)
})

// Get blog post
butter.post.retrieve("hello-world").then(function(response) {
  console.log(response)
})

// Get homepage content
butter.content.retrieve(["home"]).then(function(resp) {
  console.log(resp)
});

// Get pages
butter.content.retrieve(["pages"]).then(function(resp) {
  console.log(resp)
});
```

See our [node app](https://github.com/buttercms/nodejs-cms-express-blog) for a full example.

## Available resources & methods

Where you see params it is a plain js object, e.g. `{page: 1}`

* post
  * `retrieve(slug[, params])`
  * `list([params])`
  * `search(query[, params])`
* category
  * `retrieve(slug[, params])`
  * `list([params])`
* tag
  * `retrieve(slug[, params])`
  * `list([params])`
* author
  * `retrieve(slug[, params])`
  * `list([params])`
* feed
  * `retrieve(type[, params])`
* content
  * `retrieve(keys)`

## Test mode

Test mode can be used to setup a staging website for previewing content or for testing content during local development. To fetch content from test mode add an additional argument, `true`, to the package initialization:

```js
var butter = require('buttercms')('your butter API token', true);
```

Or use an environment variable:

```js
var butter = require('buttercms')('your butter API token', process.env.BUTTER_TEST_MODE);
```

## Documentation

Documentation is available at https://buttercms.com/docs/api/node

# metalsmith-hyphenate

[![Build Status](https://travis-ci.org/saneef/metalsmith-hyphenate.svg?branch=master)](https://travis-ci.org/saneef/metalsmith-hyphenate) [![Code Climate](https://codeclimate.com/github/saneef/metalsmith-hyphenate/badges/gpa.svg)](https://codeclimate.com/github/saneef/metalsmith-hyphenate) [![Greenkeeper badge](https://badges.greenkeeper.io/saneef/metalsmith-hyphenate.svg)](https://greenkeeper.io/)


A Metalsmith plugin to hyphenate words. It’s based on [Bram Stein’s](https://github.com/bramstein) [Hypher hyphenation engine](https://github.com/bramstein/Hypher)

## Installation

```
$ npm install metalsmith-hyphenate
```

## Usage

The `metalsmith-hyphenate` work on the HTML files. So, insert this plugin in the pipeline where HTML files are generated; commonly after `metalsmith-templates`.


### CLI

Install via `npm` and then add the `metalsmith-hyphenate` to your `metalsmith.json`.
```JSON
{
  "plugins": {
    "metalsmith-hyphenate": {
      "elements": ["p", "blockquote"]
    }
  }
}
```

### JavaScript
Pass options to the hyphenate plugin and pass it to Metalsmith with the use method:

```JavaScript
var hyphenate = require('metalsmith-hyphenate');

metalsmith.use(hyphenate({
  "elements": ["p", "blockquote"],
  "langModule": "hyphenation.de",
  "ignore": ["archives/*"] // All the files inside 'archive' will not be hyphenated
}));
```

### Options

- `elements` - (Array) HTML elements which will be hyphenated. Default is `['p', 'li', 'ol']`
- `langModule` - (String) [Hypher](https://github.com/bramstein/Hypher#nodejs) [language rules](https://github.com/bramstein/hyphenation-patterns) to be used for hyphenation. Default is `'hyphenation.en-us'`. You need to install manually — `npm install <language-module>` – if you are going to use any language rule other than the default.
- `ignore` - (Array | String) You can use glob patterns to ignore some files.

### Disable hyphenation on specific elements

Hyphenation can be disabled on an element by annotating the element or any of its ancestors with `data-hyphenate="false"`.

```html
<p data-hyphenate="false">There now is your insular city of the Manhattoes, belted round by wharves as Indian isles by coral reefs—commerce surrounds it with her surf.</p>
```

[![Published on NPM](https://img.shields.io/npm/v/@polymer/iron-iconset-svg.svg)](https://www.npmjs.com/package/@polymer/iron-iconset-svg)
[![Build status](https://travis-ci.org/PolymerElements/iron-iconset-svg.svg?branch=master)](https://travis-ci.org/PolymerElements/iron-iconset-svg)
[![Published on webcomponents.org](https://img.shields.io/badge/webcomponents.org-published-blue.svg)](https://webcomponents.org/element/@polymer/iron-iconset-svg)

## &lt;iron-iconset-svg&gt;

The `iron-iconset-svg` element allows users to define their own icon sets
that contain svg icons. The svg icon elements should be children of the
`iron-iconset-svg` element. Multiple icons should be given distinct id's.

Using svg elements to create icons has a few advantages over traditional
bitmap graphics like jpg or png. Icons that use svg are vector based so
they are resolution independent and should look good on any device. They
are stylable via css. Icons can be themed, colorized, and even animated.

Example:

```html
<iron-iconset-svg name="my-svg-icons" size="24">
  <svg>
    <defs>
      <g id="shape">
        <rect x="12" y="0" width="12" height="24" />
        <circle cx="12" cy="12" r="12" />
      </g>
    </defs>
  </svg>
</iron-iconset-svg>
```

This will automatically register the icon set "my-svg-icons" to the iconset
database.  To use these icons from within another element, make a
`iron-iconset` element and call the `byId` method
to retrieve a given iconset. To apply a particular icon inside an
element use the `applyIcon` method. For example:

```javascript
iconset.applyIcon(iconNode, 'car');
```

## Usage

### Installation

```
npm install --save @polymer/iron-iconset-svg
```

### In an HTML file

```html
<html>
  <head>
    <script type="module">
      import '@polymer/iron-iconset-svg/iron-iconset-svg.js';
      import '@polymer/iron-icon/iron-icon.js';
    </script>
  </head>
  <body>
    <iron-iconset-svg name="inline" size="24">
      <svg>
        <defs>
          <g id="shape">
            <rect x="12" y="0" width="12" height="24"></rect>
            <circle cx="12" cy="12" r="12"></circle>
          </g>
        </defs>
      </svg>
    </iron-iconset-svg>

    <iron-icon icon="inline:shape" role="img" aria-label="A shape"></iron-icon>
  </body>
</html>
```

### In a Polymer 3 element

You can use an `<iron-iconset-svg>` anywhere you could put a custom element,
such as in the shadow root of another component to expose icons to it. However,
if you're going to be creating many instances of the containing component, you
should move your `<iron-iconset-svg>` out to a separate module. This prevents a
redundant `<iron-iconset-svg>` from being added to the shadow root of each
instance of that component. See the demo (and specifically
`demo/svg-sample-icons.js`) for an example.

```js
import {PolymerElement} from '@polymer/polymer/polymer-element.js';
import {html} from '@polymer/polymer/lib/utils/html-tag.js';

import '@polymer/iron-iconset-svg/iron-iconset-svg.js';
import '@polymer/iron-icon/iron-icon.js';

class ExampleElement extends PolymerElement {
  static get template() {
    return html`
      <iron-iconset-svg name="inline" size="24">
        <svg>
          <defs>
            <g id="shape">
              <rect x="12" y="0" width="12" height="24"></rect>
              <circle cx="12" cy="12" r="12"></circle>
            </g>
          </defs>
        </svg>
      </iron-iconset-svg>

      <iron-icon icon="inline:shape" role="img" aria-label="A shape"></iron-icon>
    `;
  }
}

customElements.define('example-element', ExampleElement);
```

## Contributing

If you want to send a PR to this element, here are the instructions for running
the tests and demo locally:

### Installation

```sh
git clone https://github.com/PolymerElements/iron-iconset-svg
cd iron-iconset
npm install
npm install -g polymer-cli
```

### Running the demo locally

```sh
polymer serve --npm
open http://127.0.0.1:<port>/demo/
```

### Running the tests

```sh
polymer test --npm
```

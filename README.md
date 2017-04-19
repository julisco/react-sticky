react-sticky [![Build Status](https://travis-ci.org/captivationsoftware/react-sticky.svg?branch=master)](https://travis-ci.org/captivationsoftware/react-sticky)
============
The most powerful Sticky library available for React!

#### Demos
  - [Basic](http://rawgit.com/captivationsoftware/react-sticky/master/examples/basic/index.html)

#### Highlights
  - Fully-nestable, allowing you to build awesome layouts with familiar syntax
  - Sane defaults so you spend less time configuring
  - Allows multiple Sticky elements on the page at once with compositional awareness!

## Installation
```sh
npm install react-sticky
```

## Contributing
Start the development server, accessible on `localhost:3000` using the following command:
```sh
npm start
```

## Overview & Basic Example
`<Sticky />` elements should contain a function as its immediate child, which itself returns an element.
This function will be called based on events of the parent `<StickyContainer />`, and will provide
sane defaults for basic sticky functionality, along with a hook to apply your own logic / customizations.  

app.js
```js
import React from 'react';
import { StickyContainer, Sticky } from 'react-sticky';
...

class App extends React.Component ({
  render() {
    return (
      ...
      <StickyContainer>
        ...
        <Sticky>
          {
            ({ isSticky, style, distanceFromTop, distanceFromBottom }) => {
              return (
                <header style={style}>
                  ...
                </header>
              )
            }
          }
        </Sticky>
        ...
      </StickyContainer>
      ...
    );
  },
});

```

When the "stickiness" becomes activated, the arguments to the sticky function
are modified. Similarly, when deactivated, the arguments are once again restored accordingly.

### `<StickyContainer />` Props

`<StickyContainer />` passes along all props you provide to it without interference. That's right - no restrictions - go nuts!  

### `<Sticky />` Props

#### topOffset _(default: 0)_
Sticky state will be triggered when the top of the element is `topOffset` pixels from the top of the closest `<StickyContainer />`. Positive numbers give the impression of a lazy sticky state, whereas negative numbers are more eager in their attachment.

app.js
```js
<StickyContainer>
  ...
  <Sticky topOffset={80}>
    { ({ isSticky, style, distanceFromTop, distanceFromBottom }) => (...) }
  </Sticky>
  ...
</StickyContainer>
```

The above would result in an element that becomes sticky once its top is greater than or equal to 80px away from the top of the `<StickyContainer />`.


#### bottomOffset _(default: 0)_
Sticky state will be triggered when the bottom of the element is `bottomOffset` pixels from the bottom of the closest `<StickyContainer />`.

app.js
```js
<StickyContainer>
  ...
  <Sticky bottomOffset={80}>
    { ({ isSticky, style, distanceFromTop, distanceFromBottom }) => (...) }
  </Sticky>
  ...
</StickyContainer>
```

### License
MIT

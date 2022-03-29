# React Component Hierarchy Viewer

## Fork intro

The original project hasn't been updated in a while, so here I'm maintaining a
fork with some improvements, mainly changes I need.

## Original intro

[![npm](https://img.shields.io/npm/v/react-component-hierarchy.svg)](https://www.npmjs.com/package/react-component-hierarchy)
[![license](https://img.shields.io/github/license/bpxl-labs/react-component-hierarchy.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](.github/CONTRIBUTING.md)
[![Maintenance](https://img.shields.io/maintenance/yes/2018.svg)]()

This script uses a fork of [pretty-tree](https://github.com/mafintosh/pretty-tree) to build and display a visual representation of your React component hierarchy in the console. (The fork simply allows for colors of tree nodes to be depth-based)

![rch example](http://i.imgur.com/RbwB4PY.png)

## Usage

rch is created with the intent of being installed globally, to make it easy to use anywhere on your system. You can do this with

    $ npm install -g react-component-hierarchy

Once it is installed, you can run it by passing in the path to the source of the root component to begin with and rch will look for and map all of your root component's child components:

```
$ rch

  Usage: rch [opts] <path/to/rootComponent>

  React component hierarchy viewer.

  Options:

    -h, --help              output usage information
    -V, --version           output the version number
    -m, --module-dir <dir>  Path to additional modules not included in node_modules e.g. src
    -c, --hide-containers   Hide redux container components
    -t, --hide-third-party  Hide third party components
```

## Requirements

rch has the following requirements to understand your code:

- Component source files may use either a default export or named exports
- Components may be defined in any way (es6 `React.Component` class, functional stateless, or react.createClass)
- Must use raw non-transpiled JS.
- Must use JSX
- Must use ES6 import/export
- If you are using React Redux, your component must be wrapped and exported with React Redux's [connect](https://github.com/reactjs/react-redux/blob/master/docs/api.md#connectmapstatetoprops-mapdispatchtoprops-mergeprops-options) function, e.g:

```js
import { connect } from 'react-redux';

const SomeComponent = ({ title }) => <div>{title}</div>;

export default connect(
  mapStateToProps,
  mapDispatchToProps
)(SomeComponentContainer);
```

Or you can use a separate file for your container component which is formatted approximately like this:

```js
import { connect } from 'react-redux';

import SomeComponent from '../components/SomeComponent';

const SomeComponentContainer = connect(
  mapStateToProps,
  mapDispatchToProps
)(SomeComponent);

export default SomeComponentContainer;
```

(If your container components merely render their children with JSX, that works too.)

---

Website: [blackpixel.com](https://blackpixel.com) &nbsp;&middot;&nbsp;
GitHub: [@bpxl-labs](https://github.com/bpxl-labs/) &nbsp;&middot;&nbsp;
Twitter: [@blackpixel](https://twitter.com/blackpixel) &nbsp;&middot;&nbsp;
Medium: [@bpxl-craft](https://medium.com/bpxl-craft)

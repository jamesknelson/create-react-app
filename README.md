# Create React App w/ MDX support [![Build Status](https://travis-ci.org/facebook/create-react-app-mdx.svg?branch=master)](https://travis-ci.org/facebook/create-react-app-mdx) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-green.svg)](https://github.com/facebook/create-react-app-mdx/pulls)

A fork of the [create-react-app](https://github.com/facebook/create-react-app/) project with support for **.mdx** files via the [mdx-loader](https://www.npmjs.com/package/mdx-loader) package.

[**For info on create-react-app itself, view the official repository &raquo;**](https://github.com/facebook/create-react-app/)

## Getting Started

### For new projects

To add support for MDX to a new create-react-app project, all you need to do is pass the `--react-scripts react-scripts-mdx` option to `create-react-app`:

```js
npx create-react-app --scripts-version react-scripts-mdx
```

With this, you'll be able to use Markdown and MDX files in your new project.

### For existing projects

In your package.json, change all occurences of `react-scripts` to `react-scripts-mdx`, including occurences in `scripts` and `dependencies`.

Then, re-run `yarn install` or `npm install` and you're good to go! You'll now be able to import and use Markdown and MDX files as React components.

### Importing and using Markdown

Once you've got your project set up, add a `test.mdx` file in your project's `src` directory:

```markdown
# Hello, world

I'm an **MDX** file!
```

Then, import and use it in your `App.js` file as with any other component:

```jsx
import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';
import MDXDocument from './test.mdx';

class App extends Component {
  render() {
    return (
      <div className="App">
        <MDXDocument />
      </div>
    );
  }
}

export default App;
```

For more details on MDX itself, see the [MDX documentation &raquo;](https://mdxjs.com)

## Why a fork?

While create-react-app 1 allowed for slight modifications to configuration through [react-app-rewired](https://github.com/timarney/react-app-rewired), this wasn't supported by the create-react-app team itself.

With create-react-app 2, official support was added for some extensions through [babel-loader](https://github.com/babel/babel-loader). In fact, it's possible to get some form of MDX support with babel-loader, through the [mdx.macro](https://www.npmjs.com/package/mdx.macro) package (by yours truly). However, this package has a [major drawback](https://github.com/facebook/create-react-app/issues/5580): you'll need to manually restart the server each time you change an .mdx file.

In order to implement proper MDX support through babel-loader, babel itself will need a [new feature](https://github.com/babel/babel/issues/8497). And until this feature is added, the next best (and far easier) solution is this fork.

## What this fork changes

This fork makes a single change to `react-scripts`, with the patched package published as `react-scripts-mdx`:

**`react-scripts-mdx` will transform `.md` and `.mdx` files with [mdx-loader](https://www.npmjs.com/package/mdx-loader).**

I've used the mdx-loader package instead of @mdx-js/loader, as mdx-loader takes a batteries-included approach which is more in line with the create-react-app philosophy.

## Future plans

This fork is only meant as a stop-gap measure until babel-loader adds support live reloading of imported files, or until create-react-app adds direct support for MDX files.

## License

Create React App is open source software [licensed as MIT](https://github.com/facebook/create-react-app/blob/master/LICENSE).

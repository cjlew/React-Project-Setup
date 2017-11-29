# React-Project-Setup
A guide to setting up a standard React project

### Intro

So you haven't worked with React in awhile, or ever, and are looking for a guide? Say no more.

This guide will show you how to set up a basic React project using npm (a package manager) with ES6, babel (a compiler) and webpack (a bundler)

### Step 1: Setup Some Folders and Files

Open your terminal and create the directory

`mkdir MyProject`

Enter the directory 

`cd MyProject`

Create an `index.html`

`touch index.html`

Add the following to the `index.html` to setup the file

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>MyProject</title>
  </head>
  <body>
  <div id='root'>
  </div>
  </body>
</html>

```
Create a `lib`, and `stylesheets` folder

`mkdir lib stylesheets`

Within the `lib` folder create your `app.js`

`touch app.js`

### Step 2: Installing Dependencies

First lets setup our `package.json`
The `package.json` is used to provide metadata for the project and allows npm to see what dependencies (babel, react, etc...) the project has.

Navigate to the root directory of your project and begin setting up your `package.json`

`npm init`

Press the return key and follow along in the terminal and fill in the metadata for your project until your `package.json` is completed

It should look something like this

```
{
  "name": "MyProject",
  "version": "1.0.0",
  "description": "MyProject is a great react application",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "cjlew",
  "license": "ISC"
}


```

Now that we have our `package.json` setup we will begin to install our dependencies

For React
`npm install react react-dom --save`

For Babal
`npm install babel-core babel-loader --save`

For Webpack
`npm install webpack --save`

For presets
`npm install babel-preset-env babel-preset-react --save`

### Step 3: Setting Up Webpack

In the root project directory, create a new file called `webpack.config.js` and add the following
```
var path = require('path');
var webpack = require('webpack');

module.exports = {
    entry: './lib/app.js',
    output: {
        path: path.resolve(__dirname),
        filename: './lib/bundle.js'
    },
    module: {
        loaders: [
            {
                test: [/\.jsx?$/, /\.js?$/],
                exclude: /node_modules/,
                loader: 'babel-loader',
                query: {
                    presets: ['es2015', 'react']
                }
            }
        ]
    },
    devtool: 'source-map',
    resolve: {
     extensions: [".js", ".jsx", "*"]
    },
};


```

Edit the `package.json` by including webpack in your scripts 
```
...
"scripts": {
    "build": "npm install && webpack --watch"
  },
...

```
This will let you use `npm run build` to install all your dependencies and setup your webpack to continually update your bundle as you work 

### Step 4: Setup Your Entry File

Open your `app.js` and add
```
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(
  document.getElementById('root')
);

```

Now you should be ready to begin your project!




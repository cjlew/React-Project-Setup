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
    entry: './js/app.js',
    output: {
        path: path.resolve(__dirname),
        filename: './js/bundle.js'
    },
    module: {
        loaders: [
            {
                test: /\.js$/,
                loader: 'babel-loader',
                query: {
                    presets: ['es2015', 'react']
                }
            }
        ]
    },
};


```

Edit the `package.json` by including webpack in your scripts 
```
...
"scripts": {
    "build": "webpack"
  },
...

```




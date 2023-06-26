# Features

- Transpiler - Babel
- Bundler - Webpack

## Step 1

```jsx
npm init -y
```

## Step 2

```jsx
npm install react react-dom 
```

## Step 3

Install webpack as dev dependancy

```jsx
npm install webpack webpack-cli webpack-dev-server @babel/core @babel/preset-react @babel/preset-env  babel-loader html-webpack-plugin -D
```

### Step 4

Create `webpack.config.js` file

```jsx
const path = require('path')
const HTMLWebpackPlugin = require('html-webpack-plugin')

module.exports ={
  entry: './src/index.js',
  output: {
    path: path.join(__dirname, '/dist'),
    filename: 'bundle.js'
  },
  plugins: [
    new HTMLWebpackPlugin({
      template: './index.html'
    })
  ],
  module: {
    rules: [
      {
        test: /.js$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader',
          options: {
            presets: ['@babel/preset-env', '@babel/preset-react']
          }
        }
      }
    ]
  }
}
```

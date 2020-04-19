## ES6 세팅
> react 모듈 인스톨
```shell
npm install react react-dom
```

> babel 모듈 인스톨
```shell
npm install --save-dev @babel/core @babel/cli @babel/preset-env @babel/preset-react
```

> .babelrc
```javascript
{
    "presets": ["@babel/preset-env", "@babel/preset-react"]
}
```

> webpack
```shell
npm install --save-dev webpack webpack-cli webpack-dev-server style-loader css-loader babel-loader
```

> webpack.config.js
```javascript
const path = require('path');
const webpack = require('webpack');

module.exports = {
    entry: './src/index.js',
    mode: 'development',
    module: {
        rules: [
            {
                test: /\.(js|jsx)$/,
                exclude: /(node_modules)/,
                loader: 'babel-loader',
                options: { presets: ["@babel/env"] }
            },
            {
                test: /\.css$/,
                use: ["style-loader", "css-loader"]
            }
        ]
    },
    resolve: { extensions: ['*', '.js', '.jsx']},
    output: {
        path: path.resolve(__dirname, 'dist/'),
        publicPath: '/dist/',
        filename: 'bundle.js'
    },
    devServer: {
        contentBase: path.join(__dirname, 'public/'),
        port: 3000,
        publicPath: 'http://localhost:3000/dist/',
        hotOnly: true
    },
    plugins: [new webpack.HotModuleReplacementPlugin()]
}
```

> dev-server 실행
```shell
npx webpack-dev-server --mode development
```

> react-hot-loader 인스톨
```shell
npm install --save-dev react-hot-loader
```
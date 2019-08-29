# aws-amplify-webapp

## Create new app
1. mkdir src
2. touch package.json index.html webpack.config.js src/app.js
3. Add lines to package.json
   {
    "name": "amplify-js-app",
    "version": "1.0.0",
    "description": "Amplify JavaScript Example",
    "dependencies": {
        "@aws-amplify/api": "latest",
        "@aws-amplify/pubsub": "latest"
    },
    "devDependencies": {
        "webpack": "^4.17.1",
        "webpack-cli": "^3.1.0",
        "copy-webpack-plugin": "^4.5.2",
        "webpack-dev-server": "^3.1.5"
    },
    "scripts": {
        "start": "webpack && webpack-dev-server --mode development",
        "build": "webpack"
    }
    }
4. npm install
5. Add lines to index.html
   <!DOCTYPE html>
    <html lang="en">
        <head>
            <meta charset="utf-8">
            <title>Amplify Framework</title>
            <meta name="viewport" content="width=device-width, initial-scale=1">
            <style>
                html, body { font-family: "Amazon Ember", "Helvetica", "sans-serif"; margin: 0; }
                a { color: #FF9900; }
                h1 { font-weight: 300; }
                .app { width: 100%; }
                .app-header { color: white; text-align: center; background: linear-gradient(30deg, #f90 55%, #FFC300); width: 100%; margin: 0 0 1em 0; padding: 3em 0 3em 0; box-shadow: 1px 2px 4px rgba(0, 0, 0, .3); }
                .app-logo { width: 126px; margin: 0 auto; }
                .app-body { width: 400px; margin: 0 auto; text-align: center; }
                .app-body button { background-color: #FF9900; font-size: 14px; color: white; text-transform: uppercase; padding: 1em; border: none; }
                .app-body button:hover { opacity: 0.8; }
            </style>
        </head>
        <body>
            <div class="app">
                <div class="app-header">
                    <div class="app-logo">
                        <img src="https://aws-amplify.github.io/images/Logos/Amplify-Logo-White.svg" alt="AWS Amplify" />
                    </div>
                    <h1>Welcome to the Amplify Framework</h1>
                </div>
                <div class="app-body">
                    <button id="MutationEventButton">Add data</button>
                    <div id="MutationResult"></div>
                    <div id="QueryResult"></div>
                    <div id="SubscriptionResult"></div>
                </div>
            </div>
            <script src="main.bundle.js"></script>
        </body>
    </html>
6. Add lines to webpack.config.js
   const CopyWebpackPlugin = require('copy-webpack-plugin');
    const webpack = require('webpack');
    const path = require('path');

    module.exports = {
        mode: 'development',
        entry: './src/app.js',
        output: {
            filename: '[name].bundle.js',
            path: path.resolve(__dirname, 'dist')
        },
        module: {
            rules: [
                {
                    test: /\.js$/,
                    exclude: /node_modules/
                }
            ]
        },
        devServer: {
            contentBase: './dist',
            overlay: true,
            hot: true
        },
        plugins: [
            new CopyWebpackPlugin(['index.html']),
            new webpack.HotModuleReplacementPlugin()
        ]
    };
7. npm start

## Create the backend
1. amplify init -> use default values
2. amplify status
3. amplify hosting add
4. amplify publish




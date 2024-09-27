> If you using `git clone` after that past `npm i` to insrall reps

# Создание React-проекта без `create-react-app` с использованием Webpack

## Шаг 1: Инициализация проекта с помощью npm
>Создай новую директорию для проекта и инициализируй `npm`:
```bash
mkdir my-react-app
cd my-react-app
npm init -y
```
## Шаг 2: Установка React и ReactDOM
>Установи необходимые зависимости:

```bash
npm install react react-dom
```
## Шаг 3: Установка Webpack и зависимостей для сборки
> Установи Webpack, Babel и другие необходимые плагины:

```bash
npm install webpack webpack-cli webpack-dev-server --save-dev
npm install babel-loader @babel/core @babel/preset-env @babel/preset-react --save-dev
npm install html-webpack-plugin --save-dev
```
## Шаг 4: Настройка Babel
>Создай файл конфигурации .babelrc:

```json
{
  "presets": ["@babel/preset-env", "@babel/preset-react"]
}
```
## Шаг 5: Настройка Webpack
> Создай файл конфигурации webpack.config.js:

```javascript
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'bundle.js',
  },
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: 'babel-loader',
      },
    ],
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: './src/index.html',
    }),
  ],
  devServer: {
    static: './dist',
    port: 3000,
  },
  resolve: {
    extensions: ['.js', '.jsx'],
  },
};
```
## Шаг 6: Создание структуры файлов
> Создай папку src и добавь файлы:

```bash
Copy code
mkdir src
touch src/index.js src/index.html
```
## Шаг 7: Настройка компонентов
> В src/index.js добавь следующий код:

```javascript

import React from 'react';
import ReactDOM from 'react-dom';

const App = () => {
  return <h1>Hello, React without CRA!</h1>;
};

ReactDOM.render(<App />, document.getElementById('root'));
```
> В src/index.html добавь следующий 

### HTML-шаблон:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>React App</title>
</head>
<body>
  <div id="root"></div>
</body>
</html>
```
## Шаг 8: Добавление скриптов в package.json
>В файл package.json добавь скрипты для запуска проекта:


```json
"scripts": {
  "start": "webpack serve --mode development",
  "build": "webpack --mode production"
}

```
## Шаг 9: Запуск проекта
>Теперь можешь запустить проект командой:

```bash
npm start
```
> Приложение будет доступно по адресу http://localhost:3000.

## Шаг 10. Сборка проекта для продакшена
>Чтобы собрать проект для продакшена, используй команду:

```bash
npm run build
```
> Сборка будет находиться в папке dist.







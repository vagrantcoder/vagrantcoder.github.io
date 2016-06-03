---
layout: post
title:  "Start h5 dev by npm"
categories: h5
---


# 如果node版本太低可以先升级


1) Clear NPM's cache:

```sh
sudo npm cache clean -f
```

2) Install a little helper called 'n'

```sh
sudo npm install -g n
```

3) Install latest stable NodeJS version

```sh
sudo n stable
```


# 创建工程layout和项目文件

```sh
mkdir -p website/src/css && mkdir -p website/src/js && mkdir -p website/src/fonts
```

# 创建 package.json

```json
{
  "name": "website",
  "version": "1.0.0",
  "description": "My npm based website",
  "scripts": {
    "html": "html-minifier --collapse-whitespace ./src/index.html -o ./dist/index.html",
    "css": "stylus --include ./node_modules --include-css --compress ./src/css/main.styl -o ./dist/css/style.css",
    "js": "browserify ./src/js/main.js | uglifyjs > ./dist/js/bundle.js",
    "fonts": "fontify",
    "build": "npm run html & npm run css & npm run js & npm run fonts",
    "watch-html": "nodemon -e html -w ./src/ -x 'npm run html'",
    "watch-css": "nodemon -e styl -w ./src/css -x 'npm run css'",
    "watch-js": "nodemon -e js -w ./src/js -x 'npm run js'",
    "watch": "npm run watch-html & npm run watch-css & npm run watch-js",
    "server": "npm run watch & live-server --port=3000 ./dist"
  },
  "author": "Youssef Kababe",
  "devDependencies": {
    "browserify": "^11.1.0",
    "fontify": "0.0.2",
    "html-minifier": "^0.7.2",
    "live-server": "^0.8.1",
    "stylus": "^0.52.4",
    "uglify-js": "^2.4.24"
  },
  "dependencies": {
    "bootstrap": "^3.3.5",
    "jquery": "^2.1.4",
    "nodemon": "^1.9.2"
  }
}
```

# 安装 node_modules

npm 会根据 package 自动下载相关的依赖包，如果一次运行失败的话，就再运行一次

```sh
npm install
```

# npm build 生成目标文件

注意这里需要把 package.json 文件里面配置的 dist 目录的 layout 建立好

```sh
npm build
```









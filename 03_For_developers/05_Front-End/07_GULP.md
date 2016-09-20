# Gulp. Установка #

Gulp ставится через командную строку Ruby. Нужно зайти в папку __basetheme-design__ и устанавливать gulp именно в эту папку, но не в другое место. Мы же собираем как сасс, так и jade и в перспективе js, поэтому инит для сборщика должен быть в корневой папке верстки.

Grulpfile.js можно взять [здесь](file:///D:/makebecool/html/storage/gulpfile.js). Кроме того, нужно генерировать и package.json, если его нет.

__Установка Gulp__

```
npm install --global gulp    //Установка Gulp
npm install --save-dev gulp
npm init                        //Установка package.json
```

# Gulp. Базовый набор компонентов #

__Grulp-sass__ — модуль для сборки сасса.

```
npm install gulp-sass --save-dev
```

__Gulp-autoprefixer__ — модуль autoprefixer.

```
npm install --save-dev gulp-autoprefixer
```

__Gulp-watch__ — модуль для автоматизации сборки при изменениях в отслеживаемых файлах.

```
npm install --save-dev gulp-watch
```

__Gulp-sourcemaps__ - мапы

```
npm install gulp-sourcemaps
```

__Gulp-browser-sync__ - синхронизация

```
npm install browser-sync gulp --save-dev
```

__ES6 promice polyfill__ - полифилл

```
npm install es6-promise
```

__Полностью пакетная загрузка__

```
npm install --global gulp-cli
npm install --global gulp
npm install gulp --save-dev
npm install --save del
npm install --save-dev gulp-babel babel-preset-es2015
npm install ;e  gulp-livereload
npm install connect-livereload --save-dev
npm install --save-dev gulp-browserify
npm install gulp-sass --save-dev
npm install gulp-autoprefixer --save-dev
npm install gulp-watch --save-dev
npm install es6-promise
```

__Если у вас есть package.json__, с уже прописанными в нем зависимостями, то установить все плагины очень просто:

```
npm i
```
![alt text](/images/prestashop-cosmos-buzz.png)

# Структура файлов. Верстка под PrestaShop #

Presta Shop — это система, которая имеет сформировавшиеся стандарты и парадигмы. Поэтому чтобы сверстать проект с минимальными потерями и проблемами, нужно эти парадигмы знать.

Первый важный момент — нужно придерживаться четкой структуры файлов.

* 📁 html — html файлы, которые в последствии мы будем натягивать на модули, tpl-файлы.
    * 📁 jade — папка с jade страницами
        * 📁 components — компоненты jade
            * header.jade
            * footer.jade
            * ...
        * 📁 parts — дизайнерские части jade
            * promoAside.jade
            * ...
        * index.jade
        * ...
    * index.html
* 📁 css — стили
* critical.css
* global.css — имя файла global.css стандартно для Престы
* base64fonts.css — шрифты в base64 кодировке
* 📁 sass — исходники sass
    * 📁 sass
        * 📁 base — обнуление стилей браузеров, типографика
            * _normalize.sass
        * 📁 components — компоненты
            * _header.sass
            * _footer.sass
            * _breadcrumbs.sass
            * _forms.sass
            * _buttons.sass
            * ...
        * 📁 critical — загрузочные стили
            * _critical-style.sass
        * 📁 fonts — шрифты в base64 формате, каждое начертание в своем файле
            * _base-bold.sass
            * _base-bold-italic.sass
            * ...
        * 📁 helpers — переменные, цвета, миксины
            * _colors.sass
            * _mixins.sass
            * _typography.sass
            * _variables.sass
        * 📁 layout — сетка
            * _grid.sass
            * _grid-mixins.sass
            * _responsive-utilites.sass
        * 📁 parts — элементы дизайна, которые не являются чистыми компонентами
            * 404.sass
            * contacts.sass
            * ...
        * 📁 vendors — сторонние плагины, каждый плагин в своей папке
            * 📁 slick
            * 📁 jquery-validate
            * 📁 font-awesome
        * base64fonts.sass — сборщик всех шрифтов
        * critical.sass — сборщик critical.css
        * global.sass — сборщик основного стиля. Имя файла global.css стандартно для Престы
* 📁 img — служебные картинки (не контентные)
    * 📁 iconsite — фавикон и прочие иконки для meta-тегов
    * 📁 nonoptimised — здесь сохранять неоптимизованные иконки и картинки, не для контентной зоны
    * ... — тут храняться картинки, которые автоматически сюда вставляются, после обработки картинок из папки nonoptimised. Сюда добавлять ничего не надо. Только в папку nonoptimised
* 📁 fonts — шрифты
* 📁 js
* 📁 lang — языковые версии
* 📁 modules — переопределения шаблонов для модулей. Каждый модуль по умолчанию имеет какой-то шаблон (html-код) и содержимое этой папки может переопределять эти модули конкретно для этой темы
* 📁 cache — системная папка, туда престашоп что-то кеширует.
* 404.tpl
* ...

***

## Модульность компонентов. Верстка под PrestaShop ##

Вся Преста основана на принципе модульности. Она состояит из большого числа модулей, которые можно включать/выключать.

![alt text](/images/prestaModules.png)

Модульные темплейты PrestaShop.

Главная рекомендация для верстки — делать ее максимально независимыми компонентами. Не забывайте про БЭМ подход, именование классов.

Необходимо четко разделить шаблон на следующие части: хедер, футер, центральный контент, левая колонка, правая колонка. Шаблон должен адекватно рабтать при отключении левой колонки и правой и обоих колонок на любой типовой странице.

### Панель поиска. ###

Так как вся логика работы Престы завязана на модули, то блок поиска в хедере — не исключение.

```HTML
<form id="searchbox" method="get" action="//fo.demo.prestashop.com/en/search">
  <input type="hidden" name="controller" value="search">
  <input type="hidden" name="orderby" value="position">
  <input type="hidden" name="orderway" value="desc">
  <input class="search_query form-control ac_input" type="text" id="search_query_top" name="search_query" placeholder="Search" value="" autocomplete="off">
  <button type="submit" name="submit_search" class="btn btn-default button-search">
    <span>Search</span>
  </button>
</form>
```

### Фильтр товаров. ###

Ползунок по цене. Испольpовать плагин jquery slider как в стандартной теме.

### Слайдер изображений товара в карточке товара. ###

Оставить такой же как в дефолтной теме.

### Кнопка купить в карточке товара. ###

Делать элементом button type=”submit”.

### Листинг товаров. Кнопка купить. ###

Делать элементом <a> для товара который в наличии и можно купить. Делать элементом <span> для товара который купить нельзя.

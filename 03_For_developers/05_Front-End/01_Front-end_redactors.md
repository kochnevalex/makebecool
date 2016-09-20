@title 1.1 Базовые стандарты для верстки
@short 1.1 Базовые стандарты
@group frontendstandarts

# Описание базовых принципов и подходы к разработке frontend части наших проектов

# HTML #

## Струкута кода ##
- Структура кода должна быть иерархичной и наглядной, использовать для этого HTML/CSS-prettify
-- Каждый вложенный блок должн быть с отступом
-- Отступы делаются только пробелами, **один отступ # 2 пробела**
-- **Вложенность элементов должна быть максимально минимальной**
- HTML5 семантика с логичным и правильным применением базовых тегов header, footer,, nav, section, article, aside
-- http://www.w3.org/wiki/HTML_structural_elements
-- http://www.w3schools.com/htmL/html5_semantic_elements.asp
-- http://habrahabr.ru/post/214407/
- Валидность кода https://validator.w3.org/

### Заголовки и теги оформления текста ###
- Заголовки H1-H6 применять **только для контентной части страницы**
-- Название разделов (h1)
-- Названия подразделов (h2)
-- В списке статей - названия статей (H2-H3)
-- Текстовая страница, статья -  название (H1), в теле статьи (H2-H6)
-- В заголовке не должно быть никакой дополнительной информации, только сам заголовок
- Элементы b, i, strong, em **использовать только в контенте статей**
-- Есть разница между b, i и strong, em
--- b, i - просто жирный и курсив
--- strong, em - по мимо оформления, обозначают что текст важный (используются для SEO)

# CSS #
- Для стилей используем препроцессор SASS с синтаксисом SCSS (Sassy CSS)
-- http://sass-guidelin.es/
-- Разделение файлов http://www.sitepoint.com/architecture-sass-project/
--- Pages из этой архитектуры не используем
--- Layout используем для определения базовых стилей, кторые будут сразу добавляться в head тегом style
- На выходе мы должны получтить 2 файла css:
-- head.css - для подгрузки в секцию head тегом style
-- style.css - для отложенной загрузки тегом link
- За основу сетки берем [[http://getbootstrap.com/ | bootstrap]]
-- Если в bootstrap есть схожий логический элемент, используем именно его класс, переопределяя его, согласно нашему дизайну.
- Все элементы делать независимыми блоками, без привязки к родителю ##основано на методологии [[https://ru.bem.info/method/ | БЕМ]]  ##
- Cтилизация только по классам, избегать явного именования по тегам
- Классы не должны привязываться к id элементов
- Использовать псевдоклассы везде где это возможно

# Изображения #
- Использовать FontAwesome icons по максимуму: http://fortawesome.github.io/Font-Awesome/
- Если нужны кастомные иконки - делать svg, но если нужны иконки на :after или :before - то использовать FontAwesome, потому что для svg не выйдет использоать заливку цветом в псевдоэлементе
- Все иконки svg добавлять в css спрайт http://habrahabr.ru/post/257781/
- Изображения для контента готовить только для ретины
- Изображения для дизайна (бакграунды блоков и др.) готовить для всех разрешений и ретина в том числе
- **Изображения должны быть оптимизированны для web**

# Обязательные страницы, которыенужно готовить посе верстки всех макетов#
- Мануал по всем элементам контентной зоны страницы статьи или текста, по примеру http://dev.ienglish.ru/assets/design/article-manual.html

# Файловая структура #
Все что касается стилей и верстки, должно лежать в папке **assets/basetheme-design**
- **basetheme-design**
-- **css**
--- **sass** - папка с проектом grunt
--- **node_modules** - папка с модулями grunt
--- **Gruntfile.js** - конфигурация всех модулей
--- **package.json** - информация о проекте
-- **images**
-- **js**
--- **app** - папка с js модулями, здесь ведется работа со всем кастомным js для проекта
--- **jquery** - папка для плагинов jquery и самой библиотеки. Имя файла библиотеки должно быть с полным номером версии, к примеру jquery-2.0.3.min.js
---- jquery-2.0.3.min.js
---- **plugins**
----- **name** - папка с названием плагина, если для его подключения требуется больше 2х файлов
--- **jquery-ui**
--- **otherlibs** - папка со сторонними библиотеками
-- **min** - папка с минифицированными стилями и js
-- **fonts**

Все что касается контента должно быть в папке **assets/uploads**
И разбито на подпапки, согласно тому для чего используются изображения:
- news
- portfolio
- events
- 

# Навигация #
- Вперед: Стандарты JavaScript: @{article:1_2 Base JavaScript}





***

# Редактор #

Единственным редактором, с которым работают фронтендеры MakeBeCool является [WebStorm](https://www.jetbrains.com/webstorm/). Другие редакторы типа Sublime, Brackets использовать нельзя, потому что они примитивные.

Аргументы: в WebStorm есть много примочек для работы с js, есть много по умолчанию установленных плагинов для форматирования кода, быстрой разработки. Еще WebStorm создает свой локальный сервер с дефолтным адресом http://localhost:63343/

Если вы найдете редактор лучше — сразу говорите.

![alt text](/images/blog_webstorm10.jpg)

Обязательно нужно использовать плагин [Emmet](http://emmet.io/), для быстрой разработки. Без него работать не рекомендуется.

_Совет_ Emmet входит в дефолтный пакет WebStorm.

***

# Структура файлов проекта #

Любой фронт-енд нашего проекта имеет такую структуру:

+ 📁 basetheme-design
    * 📁 css
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
                * utilites.sass
            * 📁 parts — элементы дизайна, которые не являются чистыми компонентами
                * 404.sass
                * contacts.sass
                * ...
            * 📁 vendors — сторонние плагины, каждый плагин в своей папке
                * 📁 slick
                * 📁 jquery-validate
                * 📁 font-awesome
            * base64-fonts.sass — сборщик всех шрифтов
            * critical.sass — сборщик critical.css
            * main-style.sass — сборщик основного стиля
        * base64-fonts.css — собранные шрифты в base64 формате
        * critical.css — собранный critical css
        * main-style.css — собранный основной стиль
    *📁 fonts — шрифты, каждый шрифт в своей папке
        * open-sans
        * roboto
        * ...
    *📁 jade — папка с jade страницами
         *📁 components — компоненты jade
             * header.jade
             * footer.jade
             * ...
         * 📁 parts — дизайнерские части jade
             * promoAside.jade
             * ...
         * index.jade
         * ...
    * 📁 min — папка для минифицированных css стилей, делают сами программисты. Мы тут ничего не делаем
    * 📁 images — служебные картинки, здесь только иконки и то, что недоступно юзеру. Не контентные картинки.
    * 📁 js — скрипты, про них детальнее тут
    * index.html — файл собирается из jade файлов
    * Gulpfile.js — инит для gulp тут
    * package.json — инфа о проекте, для npm, dev-dependencies. Скачать можно тут
* 📁 uploads — здесь будут храниться картинки юзера, которые он будет грузить через админку МодХ. Сюда ничего не ложить.
* 📁 upload-demo — здесь хранятся картинки для верстки, в отдельных папках
    * 📁 news
    * 📁 articles
    * ...

***

# Соответствие верстки дизайну #

Существует большая проблема. Верстальщик поверхностно подошел к работе, сделал ориентировочные отступы на глаз, не померял начертания шрифтов Фотошопа. Передал на проверку, а дизайнер все ему вернул. И так может быть по 5 раз, перебрасывания верстки туда-сюда.

Тимлид и дизайнер пришли к верстальщику, который в 4 раз присылает неточную верстку:

![alt text](/images/pulp-fiction.jpg)

Каждому фронтендеру студии нужно поставить плагин [PerfectPixel](http://www.welldonecode.com/perfectpixel/). Именно благодаря этому плагину верстка будет максимально приближенной к макету. Заказчики и дизайнеры будут довольны, а время на комментарии и последующие правки сведется к минимуму.

_Совет_ Лучше потратить на 10% больше времени на пиксель-перфект верстку, чем потом потратить 20% времени на правки. __Экономьте свое время и время своих коллег.__

***

# Этапы разработки верстки #

Верстка кажется простой, но на самом деле это не так.

Для систематизации предлагаю разделить подход на этапы. Это поможет видеть картину разработки в целом, а не фрагментарно.

Часто бывает так, что на стадии программирования клиент прогоняет страничку на валидаторе, а затем присылает скрин "а чего у меня ошибки валидации?". После чего фронтендер начинает судорожно прогонять всю работу на валидаторе, а потом просить программиста поменять что-то в коде. Потом получает по шапке от руководства.

### __Вам это надо?__ ###

__Придерживайтесь этих этапов и будет вам счастье:__

* Разворачивание проекта
* Верстка
    * HTML этап
    * CSS этап
* Эффекты, анимации, активности
* Pixel Perfect проверка
* Оптимизация стилей, выносы critical.css
* Проверка семантики HTML
* Проверка SEO
* Валидация на w3org
* Сдача

## Разворачивание проекта ##

Фронтендер разворачивают всю структуру файлов, если ее еще нет. В идеальном варианте до этого программист разворачивает base-theme ModX, где уже есть вся структура файлов. Поэтому фронтендеру нужно только запустить сборку Grunt/Gulp и проверить, все ли jade и sass-компоненты собрались корректно.

В случае если идет работа с шаблоном/темплейтом (например который написан на less) имеющим свою структуру файлов, сборки (логичную и адекватную) — то стоит ее продолжать, но не переделывать все на нашу.

## Верстка ##

Верстку тоже нужно делить на части: HTML и CSS этапы. Это позволит ускорить работу. Pixel Perfect плагин надо с самого начала включать и верстать с ним.

## Верстка. HTML этап. ##

Сначала нужно рассмотреть все макеты страницы, на все брейкпоинтах. Увидеть колоночность, повторяющиеся элементы, блоки, выписать их на листик. Это позволит вам написать универсальные реиспользуемые html компоненты. Нужно также выписать все начертания шрифтов, базовые цвета макета (если это sass).

Необходимо сначала написать всю возможную html разметку конкретного блока, секции. Не стоит перепрыгивать "ага, сначала мы разметим ссылку, а потом её отстилизуем, а потом напишем кнопку и её отстилизуем". Это приведет к постоянному переключению и трате времени. Можно выбрать конкретный выраженый фрагмент страницы (например секцию с тремя артиклами), написать весь html код, не переходя к стилизации.

## Верстка. CSS этап. ##

После того как вы расписали всю hmtl разметку секции, можно переходить к css-стилизации. Не стоит сразу начинать с ховеров, анимаций и активностей. На этом этапе мы просто стилизуем всю статику.

## Эффекты, анимации, активности ##

Каркас, структура, все блоки уже на месте. На этом этапе мы делаем ховеры, активности верстки, подключаем различные плагины и прочее.

## Pixel Perfect проверка ##

После того как верстка готова, ее нужно проверить на соответствие макету с помощью плагина PixelPerfect. Идеального соответствия не стоит добиваться, однако при наложении совпадения должно быть заметно и выражено.

## Оптимизация стилей, выносы critical.css ##

На этом этапе весь код уже написан. Нужно пройтись по всем файлам стилей, удалить закомментированный старый код, убрать дубли, прогнать все на преттифай-плагине. При необходимости нужно сделать выносы стилей из main-style в critical логику.

## Проверка семантики HTML ##

На этом этапе нужно контрольно проверить всю семантику кода html, чтобы она была выраженой, семантичной, а не безликой и дивообразной. Проверяйте тщательно, при необходимости меняйте дивы на семантику, или наоборот, если не валидно.

## Проверка SEO ##

На этапе SEO проверки следует пройтись по всему html и убедиться что:

* дублей ссылок на одну и ту же страницу нет. Если есть - выбирайте ссылку с более тематическим анкором, а ее дубль делайте в rel#"nofollow".
* нет ссылок страницы на саму себя (например из хлебных крошек, главного меню).
* имена классов не палевные. Это важно. Была такая ситуация, когда AdBlock скрывал див с классом .adv, потому что счел его как advertisement. Также не пишите классы с именами "seo-block", потому что Google будет не рад этому.

## Валидация на w3org ##

Нужно прогнать весь html страницы через валидатор http://validator.w3.org/. У нас были ситуации когда клиент сам присылал нам ошибки валидатора на сайтах, которые мы делали. Неприятно осознавать что мы сами провтыкали этот этап проверки.

## Сдача ##

На этом этапе происходит сдача проекта. Код должен быть валидным, семантичным, SEO-безопасным и оптимизированным, удобным для чтения и как можно ближе соответствующим макету (но без идеализма, потому что время тоже критично).

***

# HTML. Индентация и форматирование кода🔗 #

В HTML используем только индентацию пробелами — только 2 пробела. Настроить это можно в WebStorm вот так:

```
File → Setings → Editor → Code Style → HTML
```

__Tab size:__ 1, __Indent size:__ 2.

Кодировка UTF-8

По умолчанию, WebStorm создает файлы с кодировкой windows-1251. Это приведет к проблемам с русскоязычным текстом и прочими символами. Нужно установить кодировку utf-8.

```
File → Setings → Editor → File Encodings
```

***

# Комментирование HTML #

Коммент в html выглядит так:

```HTML
<!-- This element will be shown by adding "active" class
############################################# -->
```

Комменты нужно писать на английском, потому что мы ориентируем продукт как можно большему числу потребителей. Если это комменты только для программиста — пишем их на русском.

Комментировать нужно код, который не очевиден. Не обязательно комментировать все, только то, что нужно объяснить.

***

# HTML. Темплейт страницы #

Темплейт страницы можно скачать [тут](file:///D:/makebecool/html/storage/template.html).

***

# HTML. Семантика HTML5 #

Мы верстаем в HTML5.

Главным ориентиром в семантике html5 являются мануалы от w3org — http://www.w3.org/TR/html5/ . Нужно быть в курсе современной семантики, использовать ее с умом. Если сомневаетесь — смотрите w3org.

Основная философия использования семантики html5 для нас — в замене обезличенных дивов на более адресные.

> Например, вы делаете верстку и перед вами серия повторяющихся блоков с заголовком, картинкой, ссылкой на полную страницу. Этот фрагмент можно сделать обычными дивами, однако у нас есть article, который по сути здесь подходит. Почему бы его не использовать? Если есть возможность сделать верстку более семантичной — нужно это делать, потому что это можно сделать.

<__main__> — тег должен содержать главный контент страницы. Этот контент напрямую относится к теме документа, причем, все его содержимое должно быть уникально на странице и не должно отображаться где-либо еще на сайте. Повторяющийся на нескольких страницах контент (логотип, окно поиска, ссылки в футере и т.д.) не следует помещать внутри элемента \<main\>, Нельзя использовать больше одного этого тега на странице, и его нельзя вкладывать в \<article\>, \<section\>, \<aside\>, \<header\>, \<footer\>.

```HTML
<main>
  <h1>Graduation</h1>

  <nav> //тут тег nav иcпользуется внутри main, потому что навигация происходит внутри самого main
    <ul>
      <li><a href#"#ceremony">Ceremony</a></li>
      <li><a href#"#graduates">Graduates</a></li>
      <li><a href#"#awards">Awards</a></li>
    </ul>
  </nav>

  <H2 id#"ceremony">Ceremony</H2>

  <p>Opening Procession</p>
  <p>Speech by Valedictorian</p>
  <p>Speech by Class President</p>
  <p>Prexentation of Diplomas</p>
  <p>Closing Speech by Headmaster</p>

  <h2 id#"graduates">Graduates</h2>
  <ul>
    <li>Eileen Williams</li>
    <li>Andy Maseyk</li>
    <li>Blanca Sainz Garcia</li>
    <li>Clara Faulkner</li>
    <li>Gez Lemon</li>
    <li>Eloisa Faulkner</li>
  </ul>

  <h2 id#"awards">Awards</h2>
    <ul>
      <li>Clara Faulkner</li>
      <li>Eloisa Faulkner</li>
      <li>Blanca Sainz Garcia</li>
    </ul>
</main>
<footer> Copyright 2012 B.lawson</footer>
```

_Детальнее тут:_ http://www.w3.org/TR/html5/grouping-content.html#the-main-element

<__aside__> — тег используется для выделения содержания, непосредственно связанного с окружающим контентом, но которое может рассматриваться и отдельно. Это могут быть боковые сноски (как в книгах), группы элементов \<nav\>, цифры или цитаты. То есть этот блок относится к определенному контенту, но может быть вынесен отдельно справа или слева.

```HTML
<main>
  <h1>Graduation</h1>

  <nav>
    <ul>
      <li><a href#"#ceremony">Ceremony</a></li>
      <li><a href#"#graduates">Graduates</a></li>
      <li><a href#"#awards">Awards</a></li>
    </ul>
  </nav>

  <aside> //Тег aside содержит блоки, относящиеся к основному контенту ниже
    <nav>
      <h1>My blogroll</h1>
        <ul>
          <li>
            <a href#"http://blog.example.com/">Example Blog</a>
          </li>
      </ul>
    </nav>
  </aside>

  <H2 id#"ceremony">Ceremony</H2>

  <p>Opening Procession</p>
  <p>Speech by Valedictorian</p>
  <p>Speech by Class President</p>
  <p>Prexentation of Diplomas</p>
  <p>Closing Speech by Headmaster</p>
</main>
<footer> Copyright 2012 B.lawson</footer>
```

_Детальнее_ тут: http://www.w3.org/TR/html5/sections.html#the-aside-element

<__header__> — элемент используется для представления вводного контента к статье или веб-странице. Обычно он содержит заглавие или какие-либо метаданные, относящиеся к данному контенту, например, дата публикации статьи или оглавление (внутри элемента \<nav>\) для более длинного документа. Элемент \<header\> будет связан с ближайшим секционным элементом, обычно это прямой родитель в структуре страницы. Заголовки \<h1\> – \<h6\> тут могу быть, а могу и не быть.

```HTML
<header> //тут может быть заголовок, подзаголовок, навигация к этой странице, дата, картинка-превью
  <h1>Little Green Guys With Guns</h1>
  <nav>
    <ul>
      <li><a href#"/games">Games</a>
      <li><a href#"/forum">Forum</a>
      <li><a href#"/download">Download</a>
    </ul>
  </nav>
  <h2>Important News</h2>
  <p>To play today's games you will need to update your client.</p>
  <h2>Games</h2>
</header>
<p>Основной контент страницы дальше</p>
```

_Детальнее тут:_ http://www.w3.org/TR/html5/sections.html#the-header-element

<__footer__> — используется для представления такой информации о разделе, как автор, авторские права (копирайты), ссылки на связанные веб-страницы. Футер необязательно должен быть внизу страницы. Рассматривайте этот тег больше как элемент из типографической верстки.

```HTML
<footer>
  <nav>
    <section>
      <h1>Articles</h1>
      <p><img src#"" alt#"">Go to the gym with our somersaults class! <a href#"#">Part 2</a></p>
      <p><img src#"" alt#"">Our guest writer Lara shows you how to bumble through the bars. <a href#"#">Read more...</a></p>
      <p><img src#"" alt#"">The chips are down, now all that's left is a potato. <a href#"#">Read more...</a></p>
    </section>
    <ul>
      <li>
        <a href#"/about">About us...</a>
      </li>
      <li>
        <a href#"/feedback">Send feedback!</a>
      </li>
      <li>
        <a href#"/sitemap">Sitemap</a>
      </li>
    </ul>
  </nav>
  <p><small>Copyright © 2015 The Snacker — <a href#"#">Terms of Service</a></small></p>
</footer>
```

_Детальнее тут:_ http://www.w3.org/TR/html5/sections.html#the-footer-element

<__nav__> — элемент используется для разметки группы ссылок на внешние страницы или разделы внутри текущей страницы. Он хорошо подходит как для основной навигации по сайту, так и по оглавлению или постам. Не все группы ссылок должны быть в этом теге, а только те, которые отражают главные навигационные блоки. Например в футере тоже могут быть навигационные ссылки, однако использовать здесь \<nav\> излишне, если это только не единственная группа навигационных ссылок на странице.

```HTML
<nav> //Тег <nav> необязательно содержит списки, например тут показана простая навигация в тексте (ссылки)
  <h1>Navigation</h1>
  <p>You are on my home page. To the north lies <a href#"#">my blog</a>, from whence the sounds of battle can be heard. To the east you can see a large mountain, upon which many <a href#"#">school papers</a> are littered. Far up thus mountain you can spy a little figure who appears to be me, desperately scribbling a <a href#"#">thesis</a>.</p>
  <p>To the west are several exits. One fun-looking exit is labeled <a href#"#">"games"</a>. Another more boring-looking exit is labeled <a href#"#">ISP™</a>.</p>
  <p>To the south lies a dark and dank <a href#"#">contacts page</a>. Cobwebs cover its disused entrance, and at one point you see a rat run quickly out of the page.</p>
</nav>
```

_Детальнее тут:_ http://www.w3.org/TR/html5/sections.html#the-nav-element

<__article__> — тег должен содержать часть самодостаточной информации, которая может быть вырвана из контекста всей страницы без потери смысла. Это блок может быть размножен, реиспользован с разным контентом. Это могут быть: новость, статья в блоге, комментарии пользователя, превью статьи, интерактивный виджет страницы. Это может быть и небольшой блок, но который визуально и логически можно выделить в отдельную сущность, имеющую свой смысл.

```HTML
<article>// Пример блока из блога, где использованы <header> и <footer>. Да, так бывает.
  <header>
    <h1>The Very First Rule of Life</h1>
    <p><time datetime#"2009-10-09">3 days ago</time></p>
    <link href#"#">
  </header>
  <p>If there's a microphone anywhere near you, assume it's hot and sending whatever you're saying to the world. Seriously.</p>
  <p>...</p>
  <footer>
    <a href#"#">Show comments...</a>
  </footer>
</article>
```

_Детальнее тут:_ http://www.w3.org/TR/html5/sections.html#the-article-element

<__section__> — элемент используется для представления группы связанного контента. Его применение похоже на \<article\> с главным отличием, что допускается отсутствие смысла содержимого внутри элемента <section> вне контекста самой страницы. По сути это тег, которым можно оборачивать содержимое, объединяя его в общую группу, например это группа записей блога, группа отзывов, блок логотипов. Рекомендуется использовать теги \<h1\> – \<h6\> для обозначения темы секции.

```HTML
<section> //Секция с заголовком и артиклами внутри
  <h1>Blog posts</h1>
  <article>
    <header>
      <h1>The Very First Rule of Life</h1>
      <p><time datetime#"2009-10-09">3 days ago</time></p>
      <link href#"#">
    </header>
    <p>If there's a microphone anywhere near you, assume it's hot and sending whatever you're saying to the world.</p>
    <p>...</p>
    <footer>
      <a href#"#">Show comments...</a>
    </footer>
  </article>
  <article>
    <header>
      <h1>The Very Second Rule of Life</h1>
      <p><time datetime#"2009-10-10">2 days ago</time></p>
      <link href#"#">
    </header>
    <p>If there's a microphone anywhere near you, assume it's hot and sending whatever you're saying to the world.</p>
    <p>...</p>
    <footer>
      <a href#"#">Show comments...</a>
    </footer>
  </article>
</section>
```

_Детальнее тут:_ http://www.w3.org/TR/html5/sections.html#the-section-element

<__time__> — машинно понимаемый элемент дял передачи дат, времени, временных зон, длительности времени. Атрибут datetime пишется в [специальном формате](http://www.w3.org/TR/html5/text-level-semantics.html#attr-time-datetime). Внутри тега time не должно быть никакой вложенности, если нет атрибута datetime.

```HTML
<article>
  <h1>Big tasks</h1>
  <footer>Published <time itemprop#"published" datetime#"2009-08-29">two days ago</time>.</footer>
  <p>Today, I went out and bought a bike for my kid.</p>
</article>
```

_Детальнее тут:_ http://www.w3.org/TR/html5/text-level-semantics.html#the-time-element

__Важно__ Общий смысл w3org в семантических тегах можно расценивать как типографические элементы из книжной, журнальной и печатной продукции. Больше вчитывайтесь в оригинальную спецификацию W3org, только там написано все как должно быть.

## Ссылки для чтения ##

http://www.smashingmagazine.com/2011/11/html5-semantics/ — HTML5 Semantics от Bruce Lawson.

http://dev.w3.org/html5/html-author/ — портянка текста от w3.org.

https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5 — мануал от Mozilla.

***

# HTML. Контентная часть #

Контентная часть — это контейнер, где всю инфу вносит юзер через свою админку. Минимум классов, сложных структур, максимум чистых семантичных тегов. Имя класса — ".content".

Классы следует использовать только, если нет никакого другого варианта решить вопрос верстки.

__Важно__ В ModX мы используем редактор __TinyMCE RTE__ (но не __TinyMCE__). Этот редактор оборачивает все элементы в теги p. Это сделано, чтобы любой текст имел контетное форматирование автоматически, а не выводился вне тегов в дивы. Поэтому в верстке нужно всегда картинку оборачивать в див с классом, например \<__div class=__"__img--wide__"\> \<__img src=__"" __alt__=""/\> \</div\> . Вне обертки картинки в контентную зону не вставляем.

```HTML
<div class="content">
  <p>Душа моя озарена неземной радостью, как эти чудесные весенние утра, которыми я наслаждаюсь от всего сердца.
  Я совсем один и блаженствую в здешнем краю, словно созданном для таких, как я. Я так счастлив, мой друг, так упоен
  ощущением покоя, что искусство мое страдает от этого. Ни одного штриха не мог бы я сделать,
  а никогда не был таким большим художником, как в эти минуты. </p>
  <blockquote>"Ах! Как бы выразить, как бы вдохнуть в рисунок то, что так полно, так трепетно живет во мне,
  запечатлеть отражение моей души, как душа моя - отражение предвечного бога!"</blockquote>
  <div class="img--wide">
    <img src="" alt=""/>
  </div>
</div>
```

Есть типичная проблема, когда ModX проставляет размер загруженой картинки в атрибуты width и height. Это сделано для того, чтобы процесс рендеринга стал быстрее (парсеру проще сделать пеинт блока, который имеет высоты и ширину, чем высчитывать его размеры по контейнеру).

Поэтому в просмотре на мобильном бывают такие ситуации, когда картинка шире чем ширина экрана:

![alt text](/images/off-dimensions.png)

Появляется горизонтальный скролл и адаптивность уже некорректная.

Для этого нужно в глобальных стилях задавать свойство:

```HTML
img {
  max-width: 100%;
```

******

# HTML. Договоренности #

Здесь описываются договоренности между программистами и верстальщиками.

1. .active — активный пункт меню, активный элемент. Тот, который сейчас активен.

2. Обращайте внимание на дублирующиеся ссылки. Например есть блок артикла, тут картинка и ниже заголовок. Они идут на одну и ту же страницу, и это 2 ссылки (ссылка-картинка и ссылка-заголовок). На картинке-ссылке нужно добавить атрибут rel="nofollow", чтобы поисковик переходил на страницу только по текстовой ссылке, с текстовым тематическим анкором. Всегда учитывайте СЕО моменты в верстке.

 __Совет__ При верстке меню, нужно помнить что ссылки со страницы на эту же страницу (циклические) — это плохой тон. Активный и текущий элемент главного меню должен быть не ссылкой, а спаном.

3. Для ссылок email-ов нужно всегда ставить mailto, для телефонов tel параметры . а для Скайпа skype:?call. Тогда можно сразу из страницы открыть почтовый клиент, или набрать телефон (будучи на сайте с мобильного).
```HTML
<a href="mailto:mail@gmail.com">mail@gmail.com</a>
<a href="tel:+380681669987">+3 8 (068) 166-99-87</a>
<a href="skype:makebecool_skype?call">makebecool_skype</a>
```

***

# HTML. Head #

В head обязательно следует подключать теги < noscript > , где должны храниться линки к стилям, которые подключатся через js. Если у юзера по каким-либо причинам не работает javascript в браузере, то тогда эти теги позволят подключить постзагрузочные стили.

Например:
```HTML
<noscript>
  <link rel="stylesheet" href="" type="text/css">
</noscript>
```

# HTML. Scripts #

Скрипты подлкючаются либо через файл __jade/components/scripts.jade__, либо если Jade не используем — то подключаем чистым html.

Схема подключения скриптов такая:

```HTML
<script>
  var global = {
    siteUrl: 'http://project.makebecool.pro/',
    baseUrl: '/',
    assetsUrl: '/assets/',
    cultureKey: 'en',
    validationMessages: {
      name: 'Будьте добры, введите ваше имя',
      phone: 'Корректный номер телефона имеет формат +98 (765) 432-11-00.',
      email: 'Адрес электронной почты имеет формат site@mail.com.',
      text: 'Здесь должно быть ваше сообщение.'
    }
  }

</script>
<script src="js/jquery/jquery-2.2.1.min.js"></script>
<script src="js/jquery/plugins/validation/jquery.validate.js"></script>
<script src="js/jquery/plugins/form/jquery.form.js"></script>
<script src="js/jquery/plugins/inputmask/inputmask.min.js"></script>
<script src="js/jquery/plugins/inputmask/jquery.inputmask.js"></script>
<script src="js/jquery/plugins/textarea-autoresize/autosize.js"></script>
<script src="js/jquery/plugins/is-in-viewport/isInViewport.js"></script>
<script src="js/jquery/plugins/easing/jquery.easing.1.3.js"></script>
<script src="js/jquery/plugins/disable-scroll/jquery.disablescroll.js"></script>
<script src="js/jquery/plugins/slick/slick.js"></script>
<script src="js/app/lib/site.js"></script>
<script src="js/app/lib/siteMode.js"></script>
<script src="js/app/mode/themeMode.js"></script>
<script src="js/app/modules/formValidate.js"></script>
<script src="js/app/modules/formAjax.js"></script>
<script src="js/app/modules/header.js"></script>
...
```

Сверху подключается объект с переменными для валидации, текущей языковой версией, урлами.

__Важно__ Когда вы подключаете новый модуль, то необходимо его подключить и для программистов, в файл __assets/basetheme-elements/chunks/base/metaBase.tpl__.

Забудете — МодХ версия слетит и не будет работать.

![alt text](/images/blia.jpg)

***

# HTML. Важные Meta #

Список копипастов, обязательных к добавлению в <head> страницы

```HTML
<meta name="format-detection" content="telephone=no"> //Запрет автоопределения номеров телефонов в ссылки на Safari

<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0"> //Чтобы страница корректно масштабирова
```

***

# HTML. Schema #

  Что такое Schema.org? Это все про теги. Это совместная инициатива по разработке единой схемы для семантической разметки в __HTML5__.

  Инициатива была запущена второго июня 2011 года создателями крупнейших поисковых систем — компаниями Google, Yahoo! и Microsoft , а первого ноября 2011 года к ней присоединилась Яндекс. Основной целью schema.org является помощь веб-разработчикам в создании качественных метаданных, что, в свою очередь, позволяет улучшать качество поиска. Метаданные на сайтах, использующие схемы, описанные на schema.org, могут быть напрямую проанализированы поисковыми роботами, помогая последним лучше «понимать» содержимое веб-ресурсов.

  Лепить все подряд теги разметки не стоит, потому что больше — не значит лучше. Следует разумно анализировать элемент дизайна и в случае попадания под нужный критерий Schema.org его надобно разметить.

## Основы разметки ##

  Любая разметка Schema.org производится в два шага:

  1. Оборачивание описания определенного типа в контейнер с указанием схемы разметки:
  ```HTML
  <div itemscope itemtype="http://schema.org/Organization"> ... </div>
  ```

  2. Разметка отдельных свойств с указанием на конкретное свойство схемы:
  ```HTML
  <span itemprop="streetAddress"> Льва Толстого, 16 </span>
  ```

В итоге выходит вот такая картина:

```HTML
  <div itemscope itemtype="http://schema.org/Organization">
    <span itemprop="name">Яндекс</span>
    Контакты:
    <div itemprop="address" itemscope itemtype="http://schema.org/PostalAddress">Адрес:
      <span itemprop="streetAddress">Льва Толстого, 16</span>
      <span itemprop="postalCode"> 119021</span>
      <span itemprop="addressLocality">Москва</span>,
    </div>
    Телефон:<span itemprop="telephone">+7 495 739–70–00</span>,
    Факс:<span itemprop="faxNumber">+7 495 739–70–70</span>,
    Электронная почта: <span itemprop="email">pr@yandex-team.ru</span>
  </div>
  ```

  Семантическая разметка контента используется различными сервисами Яндекса:

  * [Разметка товаров и их стоимости](https://yandex.ru/support/webmaster/supported-schemas/goods-prices.xml) помогает Поиску формировать специальные сниппеты для страниц с такой разметкой.
  * [Разметка информации о программах](https://yandex.ru/support/webmaster/supported-schemas/software.xml) (приложениях, компьютерных программах, играх и т. д.) помогает Поиску формировать специальные сниппеты для страниц с такой разметкой.
  * [Разметка](https://yandex.ru/support/webmaster/supported-schemas/recipe.xml) рецептов помогает Поиску формировать специальные сниппеты для страниц с такой разметкой.
  * [Разметка описаний фильмов](https://yandex.ru/support/webmaster/supported-schemas/movie-description.xml) помогает Поиску формировать специальные сниппеты для страниц с такой разметкой.
  * [Разметка творческих работ](https://yandex.ru/support/webmaster/supported-schemas/other-content.xml) помогает Поиску формировать специальные сниппеты для страниц с такой разметкой.
  * [Разметка вопросов и ответов](https://yandex.ru/support/webmaster/supported-schemas/questions.xml) помогает Поиску выделять лучший ответ и формировать специальные сниппеты для страниц с такой разметкой.
  * [Разметка рефератов и других подобных работ](https://yandex.ru/support/webmaster/supported-schemas/essay.xml) помогает Поиску формировать специальные сниппеты для страниц с такой разметкой.
  * [Разметка словарных статей](https://yandex.ru/support/webmaster/supported-schemas/dictionaries.xml) помогает Яндекс.Словарям и Поиску формировать специальные сниппеты для страниц с такой разметкой.
  * [Разметка данных об организации и ее адресе](https://yandex.ru/support/webmaster/supported-schemas/address-organization.xml) помогает Справочнику и Поиску формировать специальные сниппеты для страниц с такой разметкой.
  * [Разметка информации об изображениях](https://yandex.ru/support/webmaster/supported-schemas/image.xml) помогает улучшить представление изображений на сервисе Яндекс.Картинки.
  * [Разметка информации о видеороликах](https://yandex.ru/support/webmaster/supported-schemas/image.xml) помогает улучшить представление видеоматериалов.
  * [Разметка отзывов об организациях](https://yandex.ru/support/webmaster/supported-schemas/review-organization.xml) позволяет отображать на сервисе Карты отзывы вместе с адресами организаций.
  * [Разметка отзывов об автомобилях и тест-драйвах](https://yandex.ru/support/webmaster/supported-schemas/review-car.xml) помогает улучшить представление моделей на сервисе Яндекс.Авто и в поисковой выдаче.

## Ссылки для чтения ##

http://ruschema.org/ — русскоязычный перевод оригинальных манулов.

https://yandex.ru/support/webmaster/schema-org — мануал от Яндекса.

https://developers.google.com/structured-data/testing-tool/ — инструмент для тестирования метаданных.

***

# HTML. Формы #

Цель этих гайдлайнов — стандартизировать все моменты разработки, чтобы каждый делал все одинаково и хорошо. Обычно происходит так: первый верстальщик создает одно, второрой другое, третий открывает и создает третью вариацию. Результатом несогласованности является неразбериха и хаос, который приводит к проблемам и срывам сроков разработки.

Кроме того мы не сможет уменьшать число багов, за счет обкатки одного решения много раз, потому что это решение создается каждый раз заново.

Стандартизация форм — это сокращение времени разработки, минимум багов и проблем.

__Обычная форма с полями друг под другом__

```HTML
<div class="form-wrap">
  <form action="signup.php" class="form" data-form="register" method="POST">
    <div class="fline">
      <input id="input-1" class="form-control" type="text" name="name" placeholder="Ваше имя:" required="">
    </div>
    <div class="fline error">
      <input id="input-2" class="form-control error" type="email" name="email" placeholder="Ваш email:" required="">
      <label for="input-2" class="error">Error</label>
    </div>
    <button type="submit" class="btn">Подать заявку</button>
  </form>
  <div class="fmessage form-success active">
    <div class="form-message__ttl"></div>
    <div class="form-message__desc"></div>
  </div>
  <div class="fmessage form-error">
    <div class="form-message__ttl"></div>
    <div class="form-message__desc"></div>
  </div>
</div>
```

__Форма с полями в ряд__

```HTML
<div class="form-wrap">
  <form action="signup.php" class="form" data-form="register" method="POST">
  <div class="col-lg-4">
    <div class="fline">
      <input id="input-1" class="form-control" type="text" name="name" placeholder="Ваше имя:" required="">
    </div>
  </div>
  <div class="col-lg-6">
    <div class="fline error">
      <input id="input-2" class="form-control error" type="email" name="email" placeholder="Ваш email:" required="">
      <label for="input-2" class="error">Error</label>
    </div>
  </div>
  <div class="col-lg-6">
    <div class="fline error">
      <input id="input-2" class="form-control error" type="email" name="email" placeholder="Ваш email:" required="">
      <label for="input-2" class="error">Error</label>
    </div>
  </div>
    <button type="submit" class="btn">Подать заявку</button>
  </form>
  <div class="fmessage form-success active">
    <div class="form-message__ttl"></div>
    <div class="form-message__desc"></div>
  </div>
  <div class="fmessage form-error">
    <div class="form-message__ttl"></div>
    <div class="form-message__desc"></div>
  </div>
</div>
```

***

## HTML. Open Graph ##

Стандарт Open Graph разработан социальной сетью Facebook. Он позволяет контролировать превью, которое формируется при публикации ссылки на сайт в социальных сетях, и передавать информацию другим интернет-сервисам.

![alt text](/images/open-graph.png)

Разметку Open Graph используют Facebook, Вконтакте, Google+, Twitter, LinkedIn, Pinterest и другие сервисы.

## Основные метатеги ##

В стандарте Open Graph одна страница описывает только один объект — человека, компанию или продукт. Для этого объекта и указываются все данные. Чтобы передать информацию сервисам, необходимо в HTML-код (в элемент head) добавить следующие обязательные метатеги:

* __og:title__ — название объекта.
* __og:type — тип объекта, например, video.movie (фильм). Если у вас несколько объектов на странице, выберите один из них (главный). В зависимости от типа можно указать дополнительные свойства.
* __og:description__ — краткое описание объекта.
* __og:image__ — URL изображения, описывающего объект.
* __og:url__ — канонический URL объекта, который будет использован в качестве постоянного идентификатора.
```HTML
<meta property="og:title" content="Мэрилин Монро"/>
<meta property="og:description" content="Американская киноактриса и певица"/>
<meta property="og:image" content="https://upload.wikimedia.org/wikipedia/commons/thumb/2/27/Marilyn_Monroe_-_publicity.JPG/210px-Marilyn_Monroe_-_publicity.JPG">
<meta property="og:type" content="profile"/>
<meta property="og:url" content= "https://ru.wikipedia.org/wiki/Мэрилин_Монро" />
```

## Ссылки для чтения ##

https://yandex.ru/support/webmaster/open-graph/intro-open-graph.xml — полноценный мануал от Яндекса.

***

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

***

# Sass. Именование файлов Sass #

Все файлы именуются с маленькой буквы.

Имена cтилей не содержат тире, пробелов и пишутся только через CamelCase.

Общие правила именования sass файлов:

Структура имени: __entity + Qualification__. Т.е. название файла состоит из двух частей: __название сущности__, для которой используется файл, __уточнение к этой сущности__ (если нужно).

* _header.sass
* _typography.sass
* _asideFloatedBlock.sass

__Внимание__ Все именуется на правильном и орфографичном английском (проверяйте [словарем](https://translate.google.ru/), если не уверены в правильности). Слова в имени папки пишутся через тире (slick-slider) и с маленькой буквы.

***

# Sass. Индентация и форматирование #

Стандартная индентация для Sass — __2 пробела__ (ставьте в настройках WebStorm).

__Внимание__ Всегда сдавайте код отформатированным. Если код не отформатирован, тогда можете не сдавать его.

***

# Sass. Комментирование кода #

В Sass можно делать компиллиуремые комментарии, и не компиллируемые. Компиллируемые комменты выгружаются в итоговый .css, а не компиллируемые остаются только в .sass файле. Это образцы и их можно копировать отсюда.

1. Однострочный некомпилируемый коммент:

    ```CSS
    // Коммент
    ```

2. Однострочный компилируемый коммент:

    ```CSS
    /* Коммент
    ```

3. Многострочный компилируемый коммент такой:

    ```CSS
    /**---------------------------------------------
    * Коммент
    */
    ```

Это C-style комментарий, который выглядит как буква C.

***

# Sass. Таблица оглавления #

Таблица оглавления размещается в корневом файле, который собирает все отдельные sass файлы. Это может быть critical.sass и main-style.sass.

Оглавление состоит из списка импортируемых файлов (@import). Каждый номер оглавления — импортируемый файл.

```CSS
/**------------------------------------------------------------------
 * [Table of contents | Critical]
 *
 * 1. Typography #typography
 * 2. Variables #variables
 * 3. Colors #colors
 * 4. Mixins #mixins
 * 5. Normalize #normalize
 * 6. Grid-mixins #grid-mixins
 * 7. Responsive-utilites #responsive-utilites
 * 8. Grid #grid
 */
 ```

В начале каждого импортируемого файла делаем заглавие такого типа:

```CSS
/**
 * Colors #colors
 */
 ```

Это все сделано для того, чтобы при компиляции в собранном стиле были разделения и комменты о начале блоков стилей. Упрощает навигацию.

***

# Sass. Переменные и цвета #

## Общие переменные ##

Общие переменные вынесены в файл ```basetheme-design/css/sass/helpers/_variables.scss```. Тут лежат переменные построения сетки, кастомные переменные, которые не относятся к шрифтам и цвету.

## Переменные цвета ##

Значения и переменные цвета вынесены в отдельный файл ```basetheme-design/css/sass/helpers/_colors.scss```. Имена цветовых переменных в идеале не должны содержать отсылки к их цвету.

```CSS
$green-color: #79B316  //Так делать не надо
$regular-color: #79B316 //Так следует делать
```

## Переменные шрифтов ##

Переменные шрифтов вынесены в отдельный файл ```basetheme-design/css/sass/helpers/_typography.scss```. Имя переменной шрифта не должно отражать самого имени шрифта. Не забывайте делать подмену шрифта через бекапы sans-serif и serif, чесли кастомный шрифт не смог подключится, то чтобы браузер подтянул родственный шрифт без засечек (sans-serif) или с засечками (serif).

```CSS
$base-light-font: 'exo-2-light', sans-serif;
$second-font: 'open sans', sans-serif;
```

__Совет__ Не стоит создавать еще файлы, желательно обходится этими тремя файлами, чтобы не плодить структуру без надобности. В переменные следует записывать значения, которые будут регулярно использоваться, например транзишн и значения его тайминга, чтобы сделать все ховеры управляемыми из одного места.

## Миксины ##

В basetheme уже есть набор миксинов по умолчанию. Они здорово упрощают работу. Пользуйтесь ими.

Файл миксинов лежит: ```basetheme-design/css/sass/helpers/_mixins.scss```

* __placeholder__ — миксин для генерации стилей в плейсхолдере. Передает все значение, которые есть внутри него.

```CSS
@include placeholder
  font-style:italic
  color: white
  font-weight:100
  ```

* __cleartfix()__ — миксин обнуления обтеканий.

```CSS
@include clearfix()
```

* __absolute-center()__ — абсолютно центрирует элемент с заданными высотой и шириной.

```CSS
@include absolute-center()
```

* __x-y-center()__ — центрирует элемент по осям х и y. Размер элемента не важен, делается через transform: translate3d.

```CSS
@include x-y-center()
```

* __y-center()__ — центрирует элемент по оси y. Размер элемента не важен, делается через transform: translateY(-50%).

```CSS
@include y-center()
```

***

# Sass. БЭМ именование классов #

Мы всегда именуем классы и строим архитектуру по [БЭМ](https://ru.bem.info/).

__БЭМ__ позволяет строить архитектуру html, чтобы можно было единожды написать какой-то компонент, а затем использовать его в любом месте сайта. К этому нужно стремиться. Свободное перемещение, повторное использование.

Еще один смысл __БЭМ__ — делать разметку более прозрачной, чтобы только по одному классу можно было понять, к чему относятся стили и селекторы. Второе преимущество — это то, что каскадирование сводится к минимуму, никаких .block .inner .inner-item. .inner-item-img, а только .block__inner-img. Это позволяет парсеру браузера строить DOM дерево в меньшей степени прибегая к поискам вложенности и зависимостей.

На __БЭМе__ написаны: [Яндекс](https://ya.ru/), [HeadHunter](http://hh.ua/).

Нашей основой для именования классов является Стиль Гарри Робертса. Он визуально удобнее для восприятия, чем чистый БЭМ Яндекса.

__По БЭМу есть блоки, есть элементы блоков и есть модификаторы.__

__Блок__ — это некая конечная сущность. которую можно выделить логически. Она достаточно большая, но и достаточно самостоятельная.

__Совет__ В блоках могут быть другие блоки.

![alt text](/images/key-concepts__head_marked.png)

```HTML
<div class="tab-menu"></div> //Блок
```

__Элемент__ — это часть блока. Вне блока элемент не существует. Именуется блок через двойное подчеркивание. Например, пункт меню вне контекста блока меню не используется, значит является элементом.

![alt text](/images/key-concepts__menu-items.png)

```HTML
<ul class="tab-menu__item"></ul> //Элемент
```

__Модификатор__ — это сущность, определяющая внешний вид, состояние и поведение блока или элемента. Один и тот же блок выглядит по-разному благодаря применению модификатора.

![alt text](/images/key-concepts__site-footer-menu.png)

```HTML
<div class="tab-menu--lined"></div> //Модификатор
```

__Внимание__ Типичные ошибки использования БЭМ, которые приводят к проблемам и хаосу в коде.

```HTML
<div class="navbar__item__link"></div> //Лепим элемент элемента блока. Так нельзя, в конструкции должен быть лишь один блок и его один элемент, вот так: <div class="navbar__item-link"></div>
```

```HTML
<div class="navbar--item-link"></div> //Перепутали и написали вместо __ для элемента, -- как для модификатора. Если это элемент блока, то он отделяется двойным подчеркивание, а не тире.
```

***

# Sass. Общая архитектура #

Наш вариант разделения стилей таков:

* __base64-fonts.css__ шрифты, записываемые в localStorage
* __critical.css__, который содержит: normalize, сетку, типографику, основные стили для дизайна, которые требуются для корректного отображения сайта.
* __main-style.css__ — здесь записаны все sass компоненты.
Отделение шрифтов в base64 требуется для того, чтобы при первой загрузке скрипт загрузил их в localStorage. Тогда при повторной загрузке шрифты будут грузится из localStorage, что ускорит повторную загрузку на 30%.

Загрузочный critical.css подгружается в \<head\> инлайново в теге \<style\> через Molt. Конечный main-style.css стиль подгружается в конце загрузки страницы, через скрипт.

__Внимание__ Не забывайте ставить в \<head\> стили в \<noscript\> .

***

# Sass. Critical css #

На сегодняшний день очень много людей пользуются мобильным интернетом. В 2015 году в Украине стартовал 3G интернет, что значит, что в 2016+ годах мы получим большой прирост мобильных юзеров. Это означает что теперь нам следует большое внимание уделять не только десктопу, но именно мобильным отображениям.

Философия critical.css основана на рекомендациях Google. Они рекомендовали отделить необходимые стили страницы, чтобы инлайново загружать их прямо в <head> страницы. Таким образом мы сократим запросы к серверу, ведь эти стили загружаются на сервере, выдаваясь вместе со страницей, а не требуя отдельного запроса к серверу за файлом стилей. Преимущество налицо.

Логика разделения в том, чтобы сюда записать только самый важный рендеринговый стиль, который позволит юзеру увидеть страницу презентабельной и как можно быстрее.

Цель оптимизации - минимизировать время визуализации страниц. Этого можно добиться, меняя порядок загрузки ресурсов. Помните, что чем меньше времени пользователь проводит перед пустым экраном, тем больше степень его вовлеченности. Кроме того, оптимизация позволяет увеличить число просмотров и улучшить конверсию.

## Метрики ##

В мануале Google [Анализ процесса визуализации](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp) , описан обобщенный процесс анализа метрик. На сайте HTML5Rocks описана большая статья о том, [как работает браузер](http://www.html5rocks.com/ru/tutorials/internals/howbrowserswork/).

Есть 3 этапа загрузки страницы, которые являются вехами: __First paint__, __DOMContentLoaded__ и __Load Event__.

Событие __First paint__ — момент, когда на странице отображается первый графисеский элемент (например чаcть хедера). То есть барузер уже все распарсил, построил DOM, CSSOM и начинает переводить все в пиксели на экран. Чтобы визуализировать эту страницу, браузер должен отправить запрос на сервер, скачать HTML-документ, проанализировать его, создать модель DOM и, наконец, вывести страницу на экран.
Браузер может создавать модель визуализации и выводить страницу на экран, не дожидаясь загрузки всех элементов, потому что не все ресурсы необходимы для первоочередной визуализации. Первоочередной процесс визуализации затрагивает только HTML-, CSS и JavaScript-файлы.

Событие __DOMContentLoaded__ — парсер всей страницы полностью построил DOM из HTML узлов и выполнил все синхронно подключенные скрипты.

Событие __Load Event__ — когда вся страница, включая изображения полностью загрузилась.

__Ключевые метрики:__

## Порядок работы ##

1. Сначала все стили пишутся в обычных компонентах (parts/404.sass, components/footer.sass и т.д.). Все пишется с ховерами, со всеми нюансами. По сути это полноценный стиль, который собирается в main-style.css.
2. После того, как верстка закончена, фронтендер приступает к разделению. Он просматривает постранично все брейкпоинты и определяет, какие стили нужно вынести из main-style.css в critical.css.
Сюда выносятся стили, которые позволяют сохранить каркас страницы, ее основные дизайнерские и функциональные моменты (цвет ссылок, размеры типографики, хедер и футер, размеры картинок, ключевые отступы).
3. Итоговый __critical.css__ содержит:
    * base/normalize
    * helpers/typography
    * helpers/variables
    * helpers/colors
    * helpers/mixins
    * layout/grid-mixins
    * layout/responsive-utilites
    * layout/grid
    * critical/critical-style

__Важно__ Каждый фронтендер студии должен пройти курс: [Website Performance Optimization](https://www.udacity.com/course/website-performance-optimization--ud884).

## Какие свойства нужно вынести в critical.sass ##

Главный момент — мы должны выдать юзеру читабельный текст, который имеет размер как в макете, и несет в себе зачатки дизайна. Никакого горизонтального скролла быть не должно. При загрузке страница не должна глобально перестраиваться, когда основные стили будут подгружены.

__Сначала измерьте показатели — потом оптимизируйте по необходимости.__

* Размер шрифта страницы, заголовков, всего ключевого текста.
* Цвет ссылок по умолчанию на всем сайте (заменить противный синий дефолтный), убрать подчеркивание у ссылок, если нужно.
* Полноценный стиль хедера, без ховеров и выпадающих активностей.
* Размеры картинок - max-width: 100%, чтобы они не ломали сетку (должно быть по дефолту в библиотеке).
* Скрыть блоки, которые не должны быть показаны там, где не надо (в брейкпоинтах в соответствии с макетом).
* Проверить все брейкпоинты, найти какие секции и дивы ломают сетку, и устраницть проблемы. Ключевое — чтобы не было горизонтального скролла страницы.
* Жизненно необходимые плагины (слайдеры и прочее, что может ломать сетку).

## Сайты с critical.css подходом. ##

http://dbushell.com/2015/02/19/critical-css-and-performance/

## Ссылки для чтения ##

http://www.smashingmagazine.com/2015/08/understanding-critical-css/ — обзор плагина critical.css для Grunt.

https://css-tricks.com/authoring-critical-fold-css/ — Css-tricks обзор технологии.

***

# Jade переменные #

Jade как шаблонизатор несет как удобства, так и недостатки. Одним из недостатков является тот факт, что мы работаем с 1 файлом, который применяется на всех страницах. Например это header.jade. Каждая страница может иметь разный набор ссылок меню, разные состояния меню.

## Тайтлы c Jade ##

Самое очевидно использование, которое нужно делать — создавать перемнную title в начале jade файла, а в файле head.jade ее использовать.

__Файл index.jade:__

```HTML
- var title = "Главная — {имя проекта}";
doctype html
html(lang="ru")
```

__Файл head.jade:__

```HTML
head
    meta(charset="utf-8")
    meta(http-equiv="X-UA-Compatible", content="IE=edge")
    title #{title}
```

Переменная тайтла перекочёвывает прямо в html страницы.

## Меню c Jade ##

Типичная проблема проекта на шаблонизаторе — мы сделали один файл header.jade, где есть список пунктов меню (навигация и прочее). В итоге каждая страница (Главная, О нас, Контакты) имеет одинаковый список пунктов, и нет возможности показать текущий активный пункт страницы. Для решения этой проблемы нужно использовать цикл + миксин + переменную на Jade.

__about.html__

В начале страницы указываем переменные. Переменная menuArray — это массив объектов пунктов меню. Тут есть имя пункта, ссылка и булевая перемнная, которая показывает активный это пункт или нет. Если пункт активный, то генерируется li.active\> span, а не li \> a.

```HTML
- var menuArray = [{linkName:'О компании', href: 'about.html', active: true}, {linkName:'Новости', href: 'news.html', active: false}];
```

__header.jade__


В начале файла нужно указать файл с миксином списка пунктов меню. Ниже, в необходимом месте нужно вызвать миксин списка пунктов меню.

```
include ../mixins/mainMenuMixin
...
nav.menu__navbar
      ul.navbar-list
        ul
          +menuMixin(menuArray)
```

__mainMenuMixin.jade__

Здесь мы указываем цикл, в котором мы перебираем весь массив объектов для меню, а потом генерируем меню.

```
mixin menuMixin(data)
  if(data && data.length > 0)
    ul
      each obj in data
        if (obj.active === false)
          li
            a.tile-link(href=obj.href) #{obj.linkName}
        else
          li.active
            span #{obj.linkName}
```

# Хаки и читкоды #

## Расстояние между строчками ссылок ##

В зависимости от начертания шрифта, бывает так, что между строчками длинной ссылки появляются зазоры, которые не кликабельны. Поэтому пользователю приходится целиться курсором, чтобы попасть.

![alt text](/images/link-gap.jpg)

Решение было найдено у Горбунова: http://artgorbunov.ru/bb/soviet/20121108/.

```CSS
a {
  padding-top: .3em;
}
```

Но будьте осторожны со ссылками, обрамляющими блоки и картинки, им такой падинг ни к чему.

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

## Мануал по написанию почтовой рассылки ##

Почтовые рассылки — очень специфичная вещь.

Забудьте про блочную верстку и готовьтесь к олдскульной табличной верстке.

Обычная верстка выводится полностью в браузер клиента с полноценной оберткой body>html. Мы обнуляем стили браузера, чтобы дать место своим. В почтовой рассылке такого не бывает. Вся верстка письма выводится в незнакомую и неизвестную нам среду, которую навязывает почтовый клиент. Речь даже не идет про html>body, вся верстка будет выводится в еще более "глубокую" обертку страницы.

Стили сюда не подключишь, потому что почтовый клиент никогда не даст доступ к подключению внешних источников. Забудьте про внешние стили, скрипты, position: absolute. Этого здесь нет. Единственный вариант для стилизации — это инлайновые стили.

__Основа для всего письма — таблица.__ Почему она?

* В ней есть как горизонтальное, так и вертикальное выравнивание.
* Таблица тянется
* Ячейки таблицы легко объединяются и делятся с помощью colspan и прочего.
* Привет "align: center" свойство.

## Руководство ##

Сетка листа письма должна быть не шире 600-650 пикс., чтобы письмо отображалось корректно на всех устройствах. __Основой для письма должна быть двойная таблица.__ Общая таблица делается по ширине и по высоте всего будущего контейнера, внутри нее делается таблица с шириной 600 пикс., а в ней уже строится письмо.

Для указания ширины, выравнивания таблицы нужно использовать только cellpadding, valign, и width. Тогда никакой стиль почтового клиента не сможет их изменить.

```HTML
<table border="0" cellpadding="0" cellspacing="0" style="border-collapse: collapse; height: 100% !important; width: 100% !important; font-family: Arial, sans-serif; background: #f1f1f1; margin: 0; padding: 0;" bgcolor="#f1f1f1" >
  <tbody>
    <tr>
      <td align="center" valign="top" align="center" valign="top" style="border-collapse: collapse;" >
        <table border="0" cellpadding="0" cellspacing="0" border="0" cellpadding="0" cellspacing="0" id="emailContainer" style="border-collapse: collapse; width: 600px;">
          <tbody>
          <tr>
            <td valign="top" valign="top" style="border-collapse: collapse;" >

              //Содержимое письма

            </td>
          </tr>
          </tbody>
        </table>
      </td>
    </tr>
  </tbody>
</table>
```

В качестве урлов ссылок для картинок нужно использовать только абсолютные ссылки.

Что касается шрифтов,то должны быть использованы только самые популярные гарнитуры, которые железно есть у каждого на устройстве. Это Arial, Verdana, Georgia, и Times New Roman. Всегда указывайте цвет шрифта, потому что gmail может добавлять свой (например фиолетовый, нужен вам фиолетовый текст?).

Пишите css просто, без собирательных свойств типа "font: #000 12px Arial, Helvetica, sans-serif;". Все отдельными свойствами.

### Что не сработает ###

Вот список того, что не будет работать, как бы вы не старались:

1. position: absolute
2. background images

Более полная таблица поддержки находится тут: http://templates.mailchimp.com/resources/email-client-css-support/

Полный мануал по верстке писем от MailChimp: http://templates.mailchimp.com/

# Open Server, установка #

Часто бывает так, что сервера нет, или деплой не настроен, или необходимо сделать правку в ветке, которую некуда выводить на реальном сервере. Мы заходим в верстку, а верстки толком нет, только куски кода, устаревшие на 2 месяца от реального продакшн сайта.

Что делать? Напрягать программистов, чтобы сделали деплой, поддомен dev.project.com и только тогда можно будет поправить цвет ссылки в футере? Нет, __нужно самим разворачивать локальный сервер, как это делают программисты__. Наша оснавная задача — сделать разницу в познаниях между верстальщиком и программистом минимальной.

Мы все работаем с Open Server. Скачать Open Server можно тут http://open-server.ru/download/. Качаем Basic версию.

Есть 2 варианта работы: в репозитории еще нет ничего, и в репозитории уже есть Престашоп/МодХ. Если в репозитрии нет ничего — обращайтесь к программисту проекта, чтобы он развернул в репу Престашоп/МодХ и сделал все нужные базовые настройки. Без этого никак.

Есть официальная инструкция по установке http://open-server.ru/docs/ .

## Установка Open Server ##

1. Скачиваем архив, запускаем Open Server.exe, в папке будет два файла: x64 и x86 - выбираете в зависимости от разрядности операционки и устанавливаете его в нужную вам папку.
2. Нужно будет открыть настройки сервера и выполнить базовую конфигурацию. Это делается один раз после установки.
    * Создаем папку domains внутри Open Server (если ее нет). Создаем папку репозитория, и клонируем в нее всю репу.
    * Настраиваем модули в Open Server [Settings → Modules]. Ставим версию Апача (согласно разрядности вашей ОС), и последние рабочие версии PHP и MySQL.

    ![alt text](/images/openServerModules.png)

    * Создаем домен, выбрав ручное управление. Выбираем папку, ставим имя домена (не соответствующее папке) и нажимаем Add.

    ![alt text](/images/openServerDomains.png)

    * Стягиваем базу данных по доступам из таска. Запускаем Open Server.

    Если база небольшая, то ее можно вставить так:

    Открываем менеджер MySQL [Advanced → MySQL manager]. Нажимаем Открыть. Теперь мы находимся в Heidi SQL manager. Создаем тут новую базу данных.

    ![alt text](/images/openServerHeidi.png)

    Кликаем на вновь созданную базу данных. Выбираем вкладку Запрос. Открываем файл скачанной ранее базы данных через текстовый редактор. Копируем содержимое, вставляем в поле запроса и нажимаем Выполнить SQL запрос. База вставилась в базу Open Server.

    Если база большая, то ее так просто не вставишь, поэтому делаем следующее:

    Открываем консоль и переходим в папку с Опен Сервером. Переходим в [modules → database → ваша рабочая версия MySQL → bin]. тут лежит exe-шник mysql.exe.

    __mysql -u root__(имя юзера базы) __-ppassword__(пароль базы, если его нет, то этот параметр вообще не пишем) __dbname__(имя базы куда вставляем. Если вы до этого базу в Опен сервере не сделали, то сделайте, иначе не сработает) \< __dump.sql__ (имя базы, котороую импортируем)

    ```
    mysql -u root -ppassword dbname < dump.sql
    ```

    * Настраиваем конфигурации файлов согласно МодХ или Престашоп стандартам ниже.

***

# Престашоп. Разворачивание репозитория в локальном сервере. #

Если в репе уже есть Преста, то делаем так:

# ModX. Разворачивание репозитория в локальном сервере. #

1. Сделать 4 конфига в стянутом проекте.

    *Главный конфиг находится в папке [core → config] с названием config.inc.php. Во всех 4 папках обычно бывают болванки конфига, у них перед расширением дописано слово sample. Просто копируете их и переименовываете без sample. В этом конфиге нужно прописать всю информацию:

    ```
    $database_type = 'mysql';
    $database_server = 'localhost';
    $database_user = 'root';
    $database_password = '';
    $database_connection_charset = 'utf8';
    ```

    Не все нужно заполнять (если вы не ставили пароли и прочее в вашем Опен Сервере). Нужно лишь заполнить $dbase и изменить имя базы в сборном параметре $database_dsn.

    ![alt text](/images/modxConfig.png)


    Далее вам нужно поменять служебные урлы МодХ к ресурсам ($modx_core_path и прочее). Имейте ввиду, что урлы должны соответствовать папке, в которой лежит ваш домен в опен Сервере. Например у меня это [F:/open server/OpenServer/domains/fotobook.club/].

    * Еще три конфига с названием config.core.php в корневой папке, папке [manager] (managersite) и папке connectors. Они все одинаковые, так что можно любую болванку взять из этих 3 папок. Там нужно поменять урл, как вы это делали в файле выше ([core → config] config.inc.php).
2. Запускаем сервер - в трее будет красный флажок. Клацаем по нему - отроется меню и в нем будет пункт __Run server__. Нажимаем на него и если все ок, то флажок будет зеленый. Сервер запущен.
3. Открываем домен в браузере [My sites → ваш домен].

__Важно__ Не забудьте удалить все из папки core/cache, иначе ничего не будет работать.

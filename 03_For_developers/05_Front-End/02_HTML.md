# HTML. Индентация и форматирование кода #

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

<__section__> — элемент используется для представления группы связанного контента. Его применение похоже на \<article\> с главным отличием, что допускается отсутствие смысла содержимого внутри элемента \<section\> вне контекста самой страницы. По сути это тег, которым можно оборачивать содержимое, объединяя его в общую группу, например это группа записей блога, группа отзывов, блок логотипов. Рекомендуется использовать теги \<h1\> – \<h6\> для обозначения темы секции.

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

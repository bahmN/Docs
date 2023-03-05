## Описание

Это дополнение предназначено для облегчения интеграции оптимизаций PageSpeed Insights для MODX Revolution. Оно может:

- Работать в автоматическом режиме, если достаточно стандартной конфигурации.
- Конвертировать **gif**, **jpg** и **png** изображения в формат **webp**, если браузер его поддерживает, с кешированием или без. Регулировать размеры и качество отконвертированных изображений.
- Генерировать критические правила стилей, определять и предварительно загружать шрифты.
- Добавлять свойство **font-display** к декларациям **@font-face**.
- Устанавливать атрибут **crossorigin** и вычислять хеши **SRI**.
- Одновременно работать с несколькими конфигурациями, эффективно используя кэш.
- Применять нативную ленивую загрузку для элементов **img** и **iframe**.
- Минифицировать стили, скрипты, JSON и HTML контент.
- Добавлять аттрибут **defer** или **async** к тегам **script**.
- Получать ресурсы страницы через API **cdnjs.com** и скачивать шрифты с **Google Fonts**.
- Обрабатывать теги **meta** и **link** с аттрибутами **http-equiv** и **preconnect**.
- Выводить [специализированные теги MODX](https://docs.modx.com/revolution/2.x/making-sites-with-modx/tag-syntax#TagSyntax-Timing) в консоль браузера для членов группы **Administrator**.

Вы можете купить это дополнение в [Modstore](https://en.modstore.pro/packages/utilities/pagespeed).

## Режимы

| Режим | Описание |
| ------------- | ------------- |
| **Автоматический** | Когда опция **subresources** не задана, плагин ищет ресурсы в HTML и обрабатывает их. |
| **Ручной** | Обрабатывает только ресурсы из опции **subresources**. |

## Синтаксис

Это **не** пример рабочей конфигурации, а обзор всех доступных параметров.

``` php
[[!PageSpeed?
    &bundle=`link script`
    &convert=`static`
    &critical=`true`
    &crossorigin=`anonymous`
    &display=`swap`
    &integrity=`sha256`
    &lifetime=`604800`
    &loading=`lazy`
    &minify=`html link script`
    &quality=`80`
    &resize=`true`
    &script=`defer`
    &subresources=`{
        "link" : [
            { "name" : "", "version" : "", "filename" : "", "crossorigin" : "", "integrity" : "", "media" : "" },
            { "url" : "", "crossorigin" : "", "integrity" : "", "media" : "" }
        ],
        "script" : [
            { "name" : "", "version" : "", "filename" : "", "async" : "", "crossorigin" : "", "defer" : "", "integrity" : "", "nomodule" : "" },
            { "url" : "", "async" : "", "crossorigin" : "", "defer" : "", "integrity" : "", "nomodule" : "" }
        ]
    }`
]]
```

## Параметры

| Параметр | Описание |
| ------------- | ------------- |
| **bundle** | Не обязательный. По-умолчанию **link script**. Определяет типы контента, которые будут связаны в один файл. Не чувствителен к регистру. Возможные значения: **link**, **script**, любая их комбинация или пустое значение. <ul><li>**link** - CSS файлы.</li><li>**script** - JS файлы.</li></ul> |
| **convert** | Не обязательный. По-умолчанию **static**. Отвечает за конвертирование **gif**, **jpg** и **png** изображений в формат **webp** с указанным качеством. Не чувствителен к регистру. Возможные значения: **disable**, **dynamic**, **static**. <ul><li>**disable** - изображения не конвертируются.</li><li>**dynamic** - изображения не кешируются после конвертации. Потребляет больше ресурсов CPU.</li><li>**static** - изображения кешируются после конвертации. Потребляет больше свободного места.</li></ul> |
| **critical** | Не обязательный. По-умолчанию **true**. Отвечает за генератор критических стилей. Интерпретируется как **boolean**. |
| **crossorigin** | Не обязательный. По-умолчанию **anonymous**. Значения аттрибута **crossorigin** для всех ресурсов. Не чувствителен к регистру. Возможные значения: **anonymous**, **use-credentials**, или пустое значение. |
| **display** | Не обязательный. По-умолчанию  **swap**. Значение CSS свойства **font-display**. Не чувствителен к регистру. Возможные значения: **auto**, **block**, **swap**, **fallback**, **optional**. |
| **integrity** | Не обязательный. По-умолчанию **sha256**. Алгоритм, который будет использоваться для вычисления хеша контроля целостности ресурсов. Не чувствителен к регистру. Возможные значения: **sha256**, **sha384**, **sha512**, любая их комбинация или пустое значение. |
| **lifetime** | Не обязательный. По-умолчанию **604800**. Срок действия кэша ресурсов. |
| **loading** | Не обязательный. По-умолчанию **lazy**. Значения аттрибута **loading** для тегов **img** и **iframe**. Не чувствителен к регистру. Возможные значения: **auto**, **eager**, **lazy**. |
| **minify** | Не обязательный. По-умолчанию **html link script**. Определяет типы контента, которые будут минифицированы. Не чувствителен к регистру. Возможные значения: **css**, **html**, **js**, **json**, **link**, **script**, или любая их комбинация. <ul><li>**css** - inline CSS.</li><li>**html** - HTML контент.</li><li>**js** - inline JS.</li><li>**json** - inline JSON и JSON+LD микроданные.</li><li>**link** - CSS файлы.</li><li>**script** - JS файлы.</li></ul> |
| **quality** | Не обязательный. По-умолчанию **80**. Качество отконвертированных **webp** изображений. Возможные значения: целые числа от **0** до **100**. |
| **resize** | Не обязательный. По-умолчанию **true**. Отвечает за изменение размера изображений в тегах **img**. Интерпретируется как **boolean**. |
| **script** | Не обязательный. По-умолчанию **defer**. Аттрибут, который будет использован для тегов **script**. Не чувствителен к регистру. Возможные значения: **async**, **defer**. |
| **subresources** | Не обязательный. По-умолчанию создаётся автоматически. JSON-объект, который содержит информацию про ресурсы, их версии и файлы. Либо **URL** либо свойство **name** для **cdnjs.com** API является обязательным, в то время как остальные свойства заменяются соответствующими по-умолчанию из API, если не указаны. |

### Примеры

Последняя версия **jQuery** с **ежедневным** обновлением с **jsdelivr.net**:

``` php
[[!PageSpeed?
    &lifetime=`86400`
    &script=`async``
    &subresources=`{
        "script" : [
            { "url" : "https://cdn.jsdelivr.net/npm/jquery/dist/jquery.min.js" }
        ]
    }`
]]
```

Последняя версия **Bootstrap** с **defer** для всех ресурсов **script** и **еженедельным** обновлением с **cdnjs.com**:

``` php
[[!PageSpeed?
    &subresources=`{
        "link" : [
            { "name" : "twitter-bootstrap", "filename" : "css/bootstrap.min.css" }
        ],
        "script" : [
            { "name" : "jquery" },
            { "name" : "popper.js", "filename" : "umd/popper.min.js" },
            { "name" : "twitter-bootstrap" }
        ]
    }`
]]
```

Добавить любой **inline** стиль или скрипт можна с помощью **PHx**. Примите во внимание, что это повлечёт за собой создание нового экземпляра конфигурации, если данные отличаются при загрузке страницы. **Не используйте** этот метод для кода третьих сторон, таких как Google Analytics:

``` php
[[+phx:input=`data:text/css,
    html {
        color : [[+color]];
    }
`:cssToHead]]

[[+phx:input=`data:text/javascript,
    console.log( '[[+id]]' );
`:jsToHead]]

[[+phx:input=`data:text/javascript,
    if( typeof performance === 'object' )
        performance.mark( '[[++site_name]]' );
`:jsToBottom]]
```

### Примечания

Автоматический режим не может и не будет самостоятельно работать на любой конфигурации MODX.

Кэш можно очистить вручную в меню **Управление** / **Очистить кэш** / **PageSpeed**.

Для ручного режима их нужно добавить в секцию **script** параметра **subresources**.

Обработка анимированных **gif** изображений взможна после установки дополнения [Image Processing (ImageMagick)](https://www.php.net/manual/en/book.imagick.php) для PHP.

Одновременное выполнение возможно предотвратить установив дополнение [Semaphore, Shared Memory and IPC](https://www.php.net/manual/en/book.sem.php) для PHP.

Это дополнение использует [PHP CSS Parser](https://github.com/sabberworm/PHP-CSS-Parser/) и [Minify](https://github.com/matthiasmullie/minify).
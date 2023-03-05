Небольшой сниппет, который позволяет вам ускорить загрузку сайта за счет выноса не особо важных элементов в ajax запросы.

* Вы вызываете AjaxSnippet на любой странице сайта, с указанием имени нужного сниппета и параметров.
* Сниппет выдаёт в текущую страницу пустой блок с прелоадером и регистрирует ajax запрос.
* После загрузки страницы этот запрос уходит на сервер и ответ помещается в приготовленный блок.
* Можно отправлять запрос сразу после загрузки страницы, или при нажатии ссылки-триггера.

## Параметры сниппета

| Имя              | По умолчанию | Плейсхолдеры                                                                                                                        |
| ---------------- | ------------ | ----------------------------------------------------------------------------------------------------------------------------------- |
| **&snippet**     | pdoResources | Сниппет, который нужно запустить через Ajax.                                                                                        |
| **&propertySet** |              | Если вы хотите использовать набор параметров сниппета - укажите его имя.                                                            |
| **&wrapper**     |              | Чанк-обёртка. Обязательно должен содержать элемент с `id="[[+key]]"`.                                                               |
| **&as_mode**     | onload       | Как загружать контент: сразу после загрузки страницы «onload», или при клике на ссылку-триггер «onclick»?                           |
| **&as_trigger**  |              | Текст ссылки-триггера для режима «onclick». По умолчанию - запись из словаря «as_trigger».                                          |
| **&as_target**   |              | CSS селектор элемента, в который будет загружен ответ от сервера. По умолчанию, ответ будет вставлен на место вывода чанка-обёртки. |

Всё, что вы указываете AjaxSnippet, будет передано в вызываемый сниппет. **Сниппет можно вызывать кэшированным.**

## Примеры

Отложенная загрузка ресурсов при помощи pdoResources:

```php
[[AjaxSnippet?
    &snippet=`pdoResources`
    &parents=`0`
    &tpl=`@INLINE <p>[[+id]] - [[+pagetitle]]</p>`
    &as_mode=`onload`
]]
```

То же самое, но для старта загрузки нужно кликнуть по ссылке:

```php
[[AjaxSnippet?
    &snippet=`pdoResources`
    &parents=`0`
    &tpl=`@INLINE <p>[[+id]] - [[+pagetitle]]</p>`
    &as_mode=`onclick`
    &as_trigger=`Нажми меня!`
]]
```

На [сайте документации][1] через AjaxSnippet загружается история изменения страниц.

[1]: http://docs.modx.pro
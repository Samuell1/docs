# Содержимое ( Content )

Содержимое - это блоки с текстом, html кодом или [Markdown](http://daringfireball.net/projects/markdown/syntax) текстом, которые могут редактироваться независимо от страниц и шаблонов. Могут сожержать только статический контент. Для динамического - лучше использовать [Фрагменты](./cms-partials).

<a name="introduction"></a>
## Введение

Файлы с содержимым находятся в подпапке **/content** папки самой темы и имеют расширение:

Расширение | Описание
------------- | -------------
**htm** | Используется для HTML кода.
**txt** | Используется для простого текста.
**md** | Используется для текста с Markdown разметкой.

Расширение влияет на то, как содержимое будет отображаться не только на сайте, но и в его административной части (с помощью редактора WYSIWYG или в простом текстовом редакторе).

<a name="rendering-content-blocks"></a>
## Отображение блоков с содержимым

Чтобы вывести блок с содержимым на [страницу](./cms-pages), в [фрагмент](./cms-partials) или в [шаблон](./cms-layouts), необходмо использовать тег `{% content "file.htm" %}`. Пример:

    url = "/contacts"
    ==
    <div class="contacts">
        {% content 'contacts.htm' %}
    </div>

<a name="content-variables"></a>
## Передача переменных в блоки с содержимым

Иногда Вам может потребоваться передать значения в блок с содержимым. Так как в них не реализована поддержка Twig разметки, то необходимо использовать немного другой синтаксис: необходимая переменная задается после названия блока:

    {% content 'welcome.htm' name='John' %}

После чего она доступна следующим образом:

    <h1>This is a demo for {name}</h1>

Вы можете узнать больще в [Рукводстве по Разметке](./markup-tag-content).

<a name="content-global-variables"></a>
### Глобальные переменные

Вы можете создать глобальные переменные, которые будут доступны во всех блоках с содержимым при помощи метода `View::share`.

    View::share('site_name', 'OctoberCMS');

Сделать это можно в методах `register()` или `boot()` внутри [Регистрационного файла плагина](./plugin-registration).

[EN][en] | **RU**

| < Назад | Курс | Далее > |
|-|-|-|
| Не доступно | [1. Введение][course] | [1.2. Цвет экрана][1.2.ScreenColor] |

# 1.1. Распространение

В этом самоучителе мы начинаем обучение с распространения веб-версии простейшей
игры `ogstudio`.

Ориентировочное время выполнения: 5 минут.

# Содержание

* [Веб-версия ogstudio](#ogstudio)
* [Распространение с GitHub Pages](#distribute)
* [Запуск игры](#index)
* [Консоль отладки](#debug)
* [Итог](#summary)

<a name="ogstudio"/>

# Веб-версия ogstudio

Несмотря на то, что `ogstudio` позволяет создавать родные игры под десктоп
и мобилки, мы сконцентрируемся на веб-версии, т.к. её легко распространять
на все устройства сразу.

Веб-версия `ogstudio` состоит из следующих файлов:

* `index.html`
    * основной файл запуска пользователями в веб-браузере
    * окно вывода занимает всю страницу
* `ogstudio-<версия>.js`
    * код C++, преобразованный [Emscripten][emscripten] в JavaScript
* `ogstudio-<версия>.html.mem`
    * вспомогательный файл, сгенерированный [Emscripten][emscripten]
* `debug.html`
    * второстепенный файл запуска разработчиками в веб-браузере
    * окно вывода занимает лишь часть страницы
    * содержит консоль отладки

<a name="distribute"/>

# Распространение с GitHub Pages

В нашем случае простейшей игрой является просто пустое окно вывода.

Давайте распространим игру с помощью [GitHub Pages][github-pages].

| № | Действие | Замечания | Снимок экрана |
|-|-|-|-|
| 1. | Перейдите в `Settings` (настройки) | | ![screen-settings] |
| 2. | Выберите в качестве источника `master branch` (основную ветку) | Секция `GitHub Pages` | ![screen-source] |
| 3. | Нажмите `Save` (сохранить) | | ![screen-save] |
| 4. | Удостоверьтесь в активации | | ![screen-activation] |
| 5. | Дождитесь публикации | | ![screen-published] |

<a name="index"/>

# Запуск игры

**Внимание**: ваш браузер **должен** [поддерживать `WebGL`][webgl].

![screen-index]

Перейдите по ссылке, выданной `GitHub Pages`. Вы должны увидеть пусток окно вывода.

<a name="debug"/>

# Консоль отладки

![screen-debug]

Добавьте `/debug.html` в конец адреса URL и нажмите `Enter`, чтобы запустить ту же
самую игру с консолью отладки.

Консоль отладки является важным инструментом для отладки ваших игр `ogstudio`.

<a name="summary"/>

# Итог

Вы успешно распространили веб-версию простейшей игры `ogstudio`. Теперь вы можете
поделиться ею с любым человеком, у которого есть более или менее современный
[веб-браузер с поддержкой `WebGL`][webgl].

| < Назад | Курс | Далее > |
|-|-|-|
| Не доступно | [1. Введение][course] | [1.2. Цвет экрана][1.2.ScreenColor] |

[en]: README.md

[course]: ../../README-ru.md
[1.2.ScreenColor]: ../1.2.ScreenColor/README-ru.md

[github-pages]: https://pages.github.com
[emscripten]: http://emscripten.org
[webgl]: https://get.webgl.org

[screen-settings]: readme/settings.png
[screen-source]: readme/source.png
[screen-save]: readme/save.png
[screen-activation]: readme/activation.png
[screen-published]: readme/published.png
[screen-index]: readme/screen-index.png
[screen-debug]: readme/screen-debug.png

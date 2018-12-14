
[EN][en] | **RU**

| < Назад | Курс | Далее > |
|-|-|-|
| [1.1. Распространение][1.1.Distribute] | [1. Введение][course] | [1.3. Локальная разработка][1.3.LocalDev] |

# 1.2. Цвет экрана

В этом самоучителе мы заменим скучный синий цвет экрана на приятный зелёный.

Ориентировочное время выполнения: 15 минут.

# Содержание

* [Скрипты](#scripts)
    * [Скрипт API](#api)
    * [Скрипт Index](#index)
* [Установите цвет экрана](#color)
* [Смените цвет экрана](#change)
* [Полное обновление](#refresh)
* [Итог](#summary)

<a name="scripts"/>

# Скрипты

Если вы внимательно следили за консолью отладки, вы должны были заметить
следующие строки:

```
main::Example(...) Loading embedded API script
main::Example(...) Successfully loaded embedded API script
main::Example(...) Loading a script from 'https://ogstudio-education.github.io/.../debug.html/../index.lua'
main::Example(...) ERROR Could not load the script. 'Failed. Status code: '404''
```

`ogstudio` является приложением на `C++`, поэтому сначала нужно его собрать,
прежде чем можно его использовать. Веб-версия является одной из сборок
`ogstudio`, которую мы предоставляем в самоучителях.

Т.к. цель `ogstudio` в том, чтобы позволить вам создавать игры в кратчайшее
возможное время, `ogstudio` поддерживает скриптование, позволяющее вам
реализовывать свои идеи без необходимости настраивать и поддерживать
окружение разработки.

`ogstudio` использует язык программирования `Lua` для скриптов, т.к. `Lua`
прост для встраивания и изучения. Мы не будем касаться изучения языка `Lua`
здесь, предполагаем, что он вам уже известен. Если у вас есть опыт работы с
другими языками программирования, синтаксис `Lua` не вызовет у вас проблем.

<a name="api"/>

## Скрипт API

Цель так называемого `скрипта API` состоит в предоставлении API на языке `Lua`.
`Скрипт API` встроен в `ogstudio` и транслирует вызовы `Lua` в соответствующие
вызовы `C++`.

Вот пара следов от `скрипта API` в консоли отладки:

```
main::Example(...) Loading embedded API script
main::Example(...) Successfully loaded embedded API script
```

<a name="index"/>

## Скрипт Index

Консоль отладки также сообщает о проблеме с загрузкой так называемого
`скрипта Index`, файла `index.lua`:

```
main::Example(...) Loading a script from 'https://ogstudio-education.github.io/.../debug.html/../index.lua'
main::Example(...) ERROR Could not load the script. 'Failed. Status code: '404''
```

Этого файла ещё не существует, поэтому его и нельзя загрузить.

`Скрипт Index` содержит **ваши** идеи, выраженные на языке `Lua`. Именно здесь
вы установите цвет экрана в приятный зелёный цвет.

<a name="color"/>

# Установите цвет экрана

Давайте создадим файл `index.lua` со следующим содержимым:

```
main.application.camera.clearColor = {0, 1, 0}
```

| № | Действие | Снимок экрана |
|-|-|-|
| 1. | Нажмите `Create new file` (создать новый файл) | ![screen-create-file] |
| 2. | Введите имя файла: `index.lua` | ![screen-name-file] |
| 3. | Добавьте упомянутое выше содержимое | ![screen-file-contents] |
| 4. | Сохраните файл нажатием на `Commit new file` (зафиксировать новый файл) | ![screen-file-save] |

Теперь вы должны увидеть приятный зелёный цвет:

![screen-green]

Если вы взглянете на консоль отладки, вы увидете следующие строки:

```
main::Example(...) Loading a script from 'https://ogstudio-education.github.io/.../debug.html/../index.lua'
main::Example(...) Successfully loaded the script
main::Example(...) Successfully executed script
```

Это означает, что скрипт был успешно загружен, разобран и выполнен.

<a name="change"/>

# Смените цвет экрана

Давайте взглянем на API, использованный в `index.lua`:

* `main` (пространство имён) содержит экземпляр приложения `application`
* `main.application` (экземпляр) содержит подсистемы вроде `camera`
* `main.application.camera` (экземпляр) является "окном" в сцену приложения
* `main.application.camera.clearColor` (свойство) является очищающим цветом (фактически цветом фона) камеры
    * **принимает** массив компонент цвета в формате RGB
        ```lua
        main.application.camera.clearColor = {1, 0, 0}
        ```
    * **возвращает** массив компонент цвета в формате RGB
        ```lua
        local color = main.application.camera.clearColor
        print("background color:", color[1], color[2], color[3])
        ```

Теперь же давайте выставим красный цвет вместо зелёного:

| № | Действие | Снимок экрана |
|-|-|-|
| 1. | Выберите `index.lua` | ![screen-select-index] |
| 2. | Начните редактировать файл | ![screen-edit-index] |
| 3. | Смените цвет на красный | ![screen-change-color] |
| 4. | Сохраните файл нажатием на `Commit changes` (зафиксировать изменения) | ![screen-edit-save] |

Проверьте результат. Скорее всего вы снова увидите зелёный цвет. Если это так,
то ваш веб-браузер использует предыдующую (кэшированную) версию `index.lua`.
Чтобы избавиться от кэша, вам необходимо выполнить так называемое `полное
обновление`.

<a name="refresh"/>

# Полное обновление

Каждый веб-браузер выполняет `полное обновление` (`hard refresh`) в ответ
на разные комбинации клавиш:

* зажмите `shift`, `alt`, `ctrl`, `command` одну или вместе и щёлкните по кнопке `Перезагрузка` (`Reload`)
* зажмите `shift`, `alt`, `ctrl`, `command` одну или вместе и нажмите `F5`
* зажмите `shift`, `alt`, `ctrl`, `command` одну или вместе и нажмите `R`

Если никакая из этих комбинаций не сработала, попробуйте найти комбинацию
для вашего веб-браузера в Интернете.

После успешного `полного обновления` вы увидите красный цвет:

![screen-red]

**Внимание**:

* `GitHub Pages` публикует ваши файлы спустя несколько секунд, поэтому если ничего не поменялось в течение пары минут, вы не выполнили
`полное обновление`
* для обхода кэширования вы можете попробовать приватный режим (инкогнито), но в некоторых веб-браузерах веб-версия `ogstudio` работает в этом режиме некорректно

<a name="summary"/>

# Итог

Вы успешно:

* установили цвет экрана с помощью `main.application.camera.clearColor`
* увидели кэш веб-браузера в действии, который может свести вас с ума, если вы забудете про него

Вы использовали следующий API:

* `main` (пространство имён) содержит экземпляр приложения `application`
* `main.application` (экземпляр) содержит подсистемы вроде `camera`
* `main.application.camera` (экземпляр) является "окном" в сцену приложения
* `main.application.camera.clearColor` (свойство) является очищающим цветом (фактически цветом фона) камеры
    * **принимает** массив компонент цвета в формате RGB
        ```lua
        main.application.camera.clearColor = {1, 0, 0}
        ```
    * **возвращает** массив компонент цвета в формате RGB
        ```lua
        local color = main.application.camera.clearColor
        print("background color:", color[1], color[2], color[3])
        ```

| < Назад | Курс | Далее > |
|-|-|-|
| [1.1. Распространение][1.1.Distribute] | [1. Введение][course] | [1.3. Локальная разработка][1.3.LocalDev] |

[en]: README.md

[course]: ../../README-ru.md
[1.1.Distribute]: ../1.1.Distribute/README-ru.md
[1.3.LocalDev]: ../1.3.LocalDev/README-ru.md

[screen-create-file]: readme/create-file.png
[screen-name-file]: readme/name-file.png
[screen-file-contents]: readme/file-contents.png
[screen-file-save]: readme/file-save.png
[screen-green]: readme/screen-green.png
[screen-red]: readme/screen-red.png
[screen-select-index]: readme/select-index.png
[screen-edit-index]: readme/edit-index.png
[screen-change-color]: readme/change-color.png
[screen-edit-save]: readme/edit-save.png

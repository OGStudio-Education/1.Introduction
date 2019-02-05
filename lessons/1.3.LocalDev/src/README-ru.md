
[EN][en] | **RU**

| < Назад | Курс | Далее > |
|-|-|-|
| [1.2. Цвет экрана][1.2.ScreenColor] | [1. Введение][course] | [1.4. Мышь][1.4.Mouse] |

# 1.3. Локальная разработка

Несмотря на то, что вы можете разрабатывать игры `ogstudio` прямо на `GitHub`,
есть несколько вещей, замедляющих процесс:

* необходимо ожидать повторной публикации изменений от `GitHub Pages`
* необходимо выполнять `полное обновление` (`hard reset`)

Для ускорения процесса разработки в этом самоучителе мы покажем, как вести
разработку игр `ogstudio` локально, без `GitHub Pages`.

Ориентировочное время выполнения: 10 минут.

# Содержание

* [Установите Git и Python](#intall)
* [Склонируйте хранилище](#clone)
* [Запустите локально](#launch)
* [Смените цвет экрана](#change)
* [Итог](#summary)

<a name="install"/>

# Установите Git и Python

Чтобы начать локальную разработку, у вас должны быть установлены `git` и `python`.

Нам нужен `git`, т.к. `GitHub` управляет хранилищами (репозиториями) `git`.
Выберите удобный для вас [способ установки Git][git].

Нам нужен `python`, т.к. простой сервер HTTP (расположенный в
`tools/simple-cors-http-sever.py`) написан на Python (всего несколько строк
кода). Выберите удобный для вас [способ установки Python][python].

## Linux

Если у вас Linux, вам следует установить `git` и `python` с помощью своего
пакетного менеджера.

Например, в дистрибутивах на основе `Debian` это можно сделать так:

```
apt install git python
```

## macOS

Если у вас macOS, у вас уже есть `python`. Для получения `git` вы можете
установить `Xcode` и его `command-line tools`.

## Проверьте успешность установки Git и Python

Для проверки работоспособности `git` выполните команду `git --version` в
консоли:

```
$ git --version
git version 2.15.1 (Apple Git-101)
```

Для проверки работоспособности `python` выполните команду `python --version`
в консоли:

```
$ python --version
Python 2.7.10
```

<a name="clone"/>

# Склонируйте хранилище

Для локальной разработки вам нужно склонировать своё хранилище (репозиторий)
с `GitHub` на свой жёсткий диск:

| № | Действие | Замечания | Снимок экрана |
|-|-|-|-|
| 1 | Нажмите `Clone or download` (Склонировать или загрузить) | | ![screen-clone] |
| 2 | Скопируйте URL хранилища в буфер обмена | | ![screen-clone-url] |
| 3 | Склонируйте хранилище на свой жёсткий диск | `git clone <URL хранилища>`| `git clone https://github.com/OGStudio-Education/1-introduction-kornerr`<br><br>`Cloning into '1-introduction-kornerr'...`<br>`remote: Enumerating objects: 68, done.`<br>`remote: Counting objects: 100% (68/68), done.`<br>`remote: Compressing objects: 100% (46/46), done.`<br>`remote: Total 68 (delta 22), reused 60 (delta 20), pack-reused 0`<br>`Unpacking objects: 100% (68/68), done.` |

<a name="launch"/>

# Запустите локально

Запустите простой сервер HTTP из директории с файлом `index.lua`:

```
$ cd /путь/до/1.Introduction
$ ./tools/simple-cors-http-server.py 15000
```

Вы должны увидеть примерно такой результат:

```
Serving HTTP on 0.0.0.0 port 15000 ...
```

Это означает, что простой сервер HTTP раздаёт (serves) директорию, из
которой вы его запустили на порту `15000`.

Теперь перейдите на [http://localhost:15000](http://localhost:15000). Вы должны
увидеть красный экран:

![screen-red]

<a name="change"/>

# Смените цвет экрана

Давайте сменим цвет экрана на жёлтый. Обновите `index.lua` так, чтобы он
содержал следующее:

```
main.application.camera.clearColor = {1, 1, 0}
```

Перейдите на [http://localhost:15000](http://localhost:15000). Теперь вы
должны увидеть жёлтый экран:

![screen-yellow]

**Внимание**: ваш веб-браузер не кэшировал `index.lua`, т.к. простой сервер
HTTP не выставляет заголовки HTTP для контроля времени жизни кэша.
`GitHub Pages`, напротив, задаёт заголовки HTTP для контроля
времени жизни кэша, поэтому необходимо было выполнять `полное обновление`
(`hard reset`) в предыдущем самоучителе.

<a name="summary"/>

# Итог

Вы успешно поменяли цвет экрана локально и сразу же увидели результат без
необходимости возиться с кэшем веб-браузера.

| < Назад | Курс | Далее > |
|-|-|-|
| [1.2. Цвет экрана][1.2.ScreenColor] | [1. Введение][course] | [1.4. Мышь][1.4.Mouse] |

[en]: README.md

[course]: ../../README-ru.md
[1.2.ScreenColor]: ../1.2.ScreenColor/README-ru.md
[1.4.Mouse]: ../1.4.Mouse/README-ru.md

[git]: https://git-scm.com/downloads
[python]: https://www.python.org/downloads

[screen-clone]: readme/clone.png
[screen-clone-url]: readme/clone-url.png
[screen-clone-repo]: readme/clone-repo.png
[screen-red]: readme/screen-red.png
[screen-yellow]: readme/screen-yellow.png


[EN][en] | **RU**

# 1. Введение

Этот документ является частью [программы обучения OGStudio][education].
Документ составлен таким образом, чтобы быть заданием, которое вам
необходимо выполнить. Посмотрите [программу обучения OGStudio][education]
для получения подробной информации.

Это вводный курс в разработку игр с помощью `ogstudio`.

# Уроки

**Внимание**: курс находится в разработке, поэтому список уроков ещё не
окончательный.

| Урок | Описание | Ориентировочное время выполнения |
|-|-|-|
| [1.1. Распространение][1.1.Distribute] | Распространите веб-версию простейшей игры `ogstudio` с помощью `GitHub Pages` | 5 минут |
| [1.2. Цвет экрана][1.2.ScreenColor] | Установите цвет экрана с помощью скрипта на `Lua` | 15 минут |
| [1.3. Локальная разработка][1.3.LocalDev] | Измените цвет экрана локально, без `GitHub Pages` | 10 минут |
| [1.4. Мышь][1.4.Mouse] | Переключайте цвет экрана на нажатия мыши (пальца) | 10 минут |

# API

Уроки используют следующий API:

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

[en]: README.md

[education]: http://opengamestudio.org/pages/education.html
[1.1.Distribute]: lessons/1.1.Distribute/README-ru.md
[1.2.ScreenColor]: lessons/1.2.ScreenColor/README-ru.md
[1.3.LocalDev]: lessons/1.3.LocalDev/README-ru.md
[1.4.Mouse]: lessons/1.4.Mouse/README-ru.md


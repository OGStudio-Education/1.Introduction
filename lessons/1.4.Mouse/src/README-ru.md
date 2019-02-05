
[EN][en] | **RU**

| < Назад | Курс | Далее > |
|-|-|-|
| [1.3. Локальная разработка][1.3.LocalDev] | [1. Введение][course] | [1.5. Узел сцены][1.5.SceneNode] |

# 1.4. Мышь

В этом самоучителе мы будем переключать цвет экрана на нажатия мыши (пальца).

Ориентировочное время выполнения: 10 минут.

# Содержание

* [Определите нажатия и отпускания мыши](#press)
* [Определите щелчёк мыши](#click)
* [Добавьте переключатель цвета](#toggler)
* [Переключайте цвет экрана](#screen)
* [Итог](#summary)

<a name="press"/>

# Определите нажатия и отпускания мыши

`main.application` содержит экземпляр `mouse` (мышь), который можно
использовать для получения текущей позиции (`position`) мыши и её списка
нажатых клавиш (`pressedButtons`). Вы также можете подписаться на уведомления
об изменении позиции и / или нажатых клавиш.

Давайте подпишемся на нажатия / отпускания клавиши мыши. Обновите `index.lua`,
чтобы файл содержал следующее:

```lua
main.application.mouse.pressedButtonsChanged:addCallback(
    function()
        print("Detected a mouse press / release")
    end
)
```

**Замечания**:

* `pressedButtonsChanged` является экземпляром-уведомителем, на уведомления которого мы подписываемся
* `addCallback` является методом экземпляра-уведомителя `pressedButtonsChanged`
* `pressedButtonsChanged` и `addCallback` разделены `:`, т.к. это вызов метода
* блок `function() ... end` является функцией обратного вызова, замыканием (callback function, closure), выполняемым при каждом получении уведомления

В консоли отладки вы должны увидеть следующий результат:

```
Detected a mouse press / release
Detected a mouse press / release
```

<a name="click"/>

# Определите щелчёк мыши

Наверняка, вы заметили, что каждый щелчёк (click) мыши (нажатие пальца) приводит
к выводу двух строк в консоль отладки. Причина в получении уведомлений как о
нажатиях, так и об отпусканиях.

Щелчёк - это нажатие с последующим отпусканием. Для упрощения реализации мы
будем считать отпускание щелчком.

Обновите функцию обратного вызова, чтобы она выглядела следующим образом:

```lua
function()
    -- Detect a click.
    if (#main.application.mouse.pressedButtons == 0)
    then
        print("Detected a mouse click")
    end
end
```

**Замечания**:

* `#` возвращает количество элементов массива
* для простоты мы удостоверяемся в том, что все клавиши отпущены, т.е. нет нажатых клавиш

Теперь каждый щелчёк должен приводить ровно к одной строке в выводе консоли отладки.

<a name="toggler"/>

# Добавьте переключатель цвета

Добавьте экземпляр переключателя цвета `colorToggler` для переключения между
двумя цветами. Добавьте следующий код в начало `index.lua`:

```lua
-- Define color toggling functionality.
local colorToggler = {
    -- List of colors to toggle between.
    colors = {
        {0, 1, 0}, -- Green.
        {1, 0, 0}, -- Red.
    },
    -- Keep track of which color is selected.
    isFirstColorSelected = true,
    -- Return toggled color.
    toggledColor = function(self)
        self.isFirstColorSelected = not self.isFirstColorSelected
        if (self.isFirstColorSelected)
        then
            return self.colors[1]
        else
            return self.colors[2]
        end
    end,
}
```

**Замечания**:

* экземпляр `colorToggler` является таблицей `Lua` с двумя переменными для хранения состояния и одной функцией (методом) для изменения этого состояния
* `colorToggler` можно рассматривать как экземпляр класса в других языках программирования
* `local` обозначает локальную переменную, иначе переменные становятся глобальными
* `Lua` индексирует массивы с `1`, не с `0` (как это делает `C`)
* комментарии начинаются с `--` в `Lua`

<a name="screen"/>

# Переключайте цвет экрана

Нам осталось вызывать `colorToggler` на нажатия мыши (пальца). Обновите функцию
обратного вызова, чтобы она выглядела следующим образом:

```lua
function()
    -- Detect a click.
    if (#main.application.mouse.pressedButtons == 0)
    then
        -- Toggle screen color.
        local color = colorToggler:toggledColor()
        print("Set screen color to", color[1], color[2], color[3])
        main.application.camera.clearColor = color
    end
end
```

Теперь щёлкайте по экрану. Он должен переключать свой цвет между красным и зелёным:

![video-result]

<a name="summary"/>

# Итог

Вы успешно:

* создали реакцию на щелчки мыши с помощью подписки на `main.application.mouse.pressedButtonsChanged`
* реализовали `colorToggler` для переключения между красным и зелёным
* использовали `colorToggler` вместе с `main.application.mouse.pressedButtonsChanged` и `main.application.camera.clearColor` для переключения цвета экрана

Проверьте окончательную версию [index.lua][index.lua], которую вы должны были создать.

| < Назад | Курс | Далее > |
|-|-|-|
| [1.3. Локальная разработка][1.3.LocalDev] | [1. Введение][course] | [1.5. Узел сцены][1.5.SceneNode] |

[en]: README.md

[course]: ../../README-ru.md
[1.3.LocalDev]: ../1.3.LocalDev/README-ru.md
[1.5.SceneNode]: ../1.5.SceneNode/README-ru.md
[index.lua]: index.lua

[video-result]: readme/result.gif

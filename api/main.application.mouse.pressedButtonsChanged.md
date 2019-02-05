FEATURE README.md/API
* `main.application.mouse.pressedButtonsChanged` is a notification instance (`core.Reporter`) that reports notifications when any mouse button (finger) is pressed or released
FEATURE README.md/APISubscribe
    * **to subscribe** to all notifications, use `core.Reporter`'s `addCallback()` method:
        ```lua
        main.application.mouse.pressedButtonsChanged:addCallback(
            function()
                print("A mouse (finger) has been pressed or released")
            end
        )
        ```
        **Notes**:
            * `pressedButtonsChanged` and `addCallback` are separated by `:` because it's a method call
            * `function() ... end` block represents a callback function (closure) to be executed upon receiving notification
FEATURE README.md/APISubscribeOnce
    * **to subscribe only once** to the next notification of mouse buttons (fingers), use `core.Reporter`'s `addOneTimeCallback()` method:
        ```lua
        main.application.mouse.pressedButtonsChanged:addOneTimeCallback(
            function()
                print("A mouse (finger) has been pressed or released only once")
            end
        )
        ```

FEATURE README-ru.md/API
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



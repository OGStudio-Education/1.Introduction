FEATURE README.md/API
* `main.application.mouse.pressedButtonsChanged` is an instance of `core.Reporter` (notification reporter)



property is a clearing color (effectively background color) of the camera
    * **accepts** array of color components in RGB format
        ```lua
        main.application.camera.clearColor = {1, 0, 0}
        ```
    * **returns** array of color components in RGB format
        ```lua
        local color = main.application.camera.clearColor
        print("background color:", color[1], color[2], color[3])
        ```

Let's subscribe to button press / release notifications. Update `index.lua` to
have the following contents:

```lua
main.application.mouse.pressedButtonsChanged:addCallback(
    function()
        print("Detected a mouse press / release")
    end
)
```

**Notes**:

* `pressedButtonsChanged` is a notification instance we subscribe to
* `addCallback` is a method of `pressedButtonsChanged` notification instance
* `pressedButtonsChanged` and `addCallback` are separated by `:` because it's a method call
* `function() ... end` block represents a callback function (closure) to be executed each time notification is reported






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



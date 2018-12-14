FEATURE README.md/API
* `main.application.camera.clearColor` property is a clearing color (effectively background color) of the camera
    * **accepts** array of color components in RGB format
        ```lua
        main.application.camera.clearColor = {1, 0, 0}
        ```
    * **returns** array of color components in RGB format
        ```lua
        local color = main.application.camera.clearColor
        print("background color:", color[1], color[2], color[3])
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

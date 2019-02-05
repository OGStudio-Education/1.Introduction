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
* `main.application.mouse.pressedButtonsChanged` является экземпляром-уведомителем (`core.Reporter`), который уведомляет при нажатии и отпускании любой клавиши мыши (пальца)
FEATURE README-ru.md/APISubscribe
    * **для подписки** на все уведомления используйте метод `addCallback()` у `core.Reporter`:
        ```lua
        main.application.mouse.pressedButtonsChanged:addCallback(
            function()
                print("A mouse (finger) has been pressed or released")
            end
        )
        ```

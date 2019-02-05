FEATURE README.md/API
* `main.application.mouse.pressedButtonsChanged` is a notification instance (`core.Reporter`) that reports notifications when any mouse button (finger) is pressed or released
FEATURE README.md/Subscribe
    * **to subscribe** to all notifications, use `core.Reporter`'s `addCallback()` method:
        ```lua
        main.application.mouse.pressedButtonsChanged:addCallback(
            function()
                print("A mouse button or finger has been pressed or released")
            end
        )
        ```

FEATURE README-ru.md/API
* `main.application.mouse.pressedButtonsChanged` является экземпляром-уведомителем (`core.Reporter`), который уведомляет при нажатии и отпускании любой кнопки мыши (пальца)
FEATURE README-ru.md/Subscribe
    * **для подписки** на все уведомления используйте метод `addCallback()` у `core.Reporter`:
        ```lua
        main.application.mouse.pressedButtonsChanged:addCallback(
            function()
                print("A mouse button or finger has been pressed or released")
            end
        )
        ```

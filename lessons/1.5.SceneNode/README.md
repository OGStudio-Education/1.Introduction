
**EN** | [RU][ru]

| < Back | Course | Next > |
|-|-|-|
| [1.4. Mouse][1.4.Mouse] | [1. Introduction][course] | TODO |

# 1.5. Scene node

In this tutorial we going to display red spherical scene node.

Estimated completion time: TODO.

# Table of contents

* [Display sphere](#sphere)

* [Summary](#summary)

<a name="sphere"/>

# Display sphere

`main.application` hosts `nodePool` instance, which can be used to get or
create scene nodes. A scene node is an object you see in a scene.

Let's display a sphere. Update `index.lua` to have the following contents:

```lua
local sphere = main.application.nodePool:createSphere("sphere", 1)
local root = main.application.nodePool:node("root")
root:addChild(sphere)
```

**Notes**:


TODO Reference API?

* `createSphere()` accepts name (`sphere`) and radius (`1`) and returns new spherical scene node 
* `node()` accepts name of a node to look for in the pool; if the node was found, it is returned; otherwise nil is returned
is a method of `pressedButtonsChanged` notification instance
* `pressedButtonsChanged` and `addCallback` are separated by `:` because it's a method call
* `function() ... end` block represents a callback function (closure) to be executed each time notification is reported


<a name="summary"/>

# Summary

You have successfully:

Here's final [index.lua][index.lua] you should have created.

| < Back | Course | Next > |
|-|-|-|
| [1.4. Mouse][1.4.Mouse] | [1. Introduction][course] | TODO |

[ru]: README-ru.md

[course]: ../../README.md
[1.4.Mouse]: ../1.4.Mouse/README.md
[index.lua]: index.lua

[video-result]: readme/result.gif

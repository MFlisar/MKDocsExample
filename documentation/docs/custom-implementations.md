# Custom Implementations

!!! info

    If you use the timber implementation check out the timber documentation!

The lumberjack implementation allows you to create a custom logger by simple implementing a single function. Check out the implementation from the console logger below to get a good starting point for a custom logger.

```kotlin title="library/Demo.kt" linenums="4"
--8<-- "library/Demo.kt:4:6"
```

That's all. You can do the logging asynchronous as well if you want - just do whatever you want inside your logger implementation.
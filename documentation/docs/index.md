---
icon: material/information-variant
---

{% include 'header.md' %}

A **lazy logging library**.

{% include 'region-features.md' %}

This is a **full logging library* with a build in way to log to **console**, **file** or any **custom** place as well as optional extensions to send a log file via mail or show it on the device.

!!! info
    
    All features are splitted into separate modules, just include the modules you want to use!

{% include 'region-screenshots.md' %}

{% include 'modules.md' %}

{% include 'platforms.md' %}

* iOS is mostly missing because the I use `ThreadLocal` and `StackTraceElement` inside the `implementation-lumberjack` module - those usages would need to be replaced for the iOS implementation - a pull request would be much appreciated!
* iOS is also missing a simple console logging function - a pull request would be much appreciated!
* the `extension-composeviewer` would support iOS immediately as soon as the above 2 points are integrated

{% include 'demo.md' %}

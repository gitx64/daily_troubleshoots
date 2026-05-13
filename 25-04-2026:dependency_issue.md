## What to do if building from source and not found some lib dependencies.

- meson, cmake, pkg-config, download them they are the most common use cases while building. 
- if some library dependencies are missing then the namespace
most commonly looks like lib<packagename>-dev. Try search it with apt search or whatever the packagemanager is and install it. Most probably it will solve the issue otherwise it will show the verbosed log.

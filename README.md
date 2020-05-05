C++ Cookiecutter Template
=========================

This is a [cookiecutter](https://github.com/cookiecutter/cookiecutter) template
for a C++ project using [CMake](https://cmake.org) and [Conan](conan.io).  It
was forked from [tarcisioe cpp-template](https://github.com/tarcisioe/cpp-template).

How to use
==========

First, setup your own project with `cookiecutter`:

```bash
cookiecutter gh:bohruz/cpp-template
```

This will create a directory with the name you defined in `project_slug`.
Enter that directory, then define the dependencies you wish to download and
build with `conan` in `CMakeLists.txt` by uncommenting `PACKAGES` and listing
them right after that:

```cmake
conan(
    PACKAGES
        fmt/0.6.10
)
```

Finally, create your build directory:

```bash
cmake -B build
```

To link your dependencies, add them to your targets (e.g. `main` in
`src/CMakeLists.txt`) like this:

```cmake
target_link_libraries(
    main
        PUBLIC
            (...)
            CONAN_PKG::fmt
)
```

Then, build your project:

```bash
cmake --build build
```

Enjoy your project with your dependencies, a compile database already generated,
warnings enabled, etc. :)

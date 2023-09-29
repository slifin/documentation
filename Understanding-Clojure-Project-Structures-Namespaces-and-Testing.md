# Understanding Clojure Project Structures, Namespaces, and Testing

Welcome, Clojure beginners! If you're making the switch from other programming languages, understanding the structure of a Clojure project can be a bit challenging at first. This guide is here to help you unravel the complexities of project structures, namespaces, and how to manage your source and test code.

## Table of Contents

1. [Introduction to Clojure Project Structure](#introduction-to-clojure-project-structure)
2. [Understanding Namespaces](#understanding-namespaces)
3. [File Structure and `src`](#file-structure-and-src)
4. [Testing in Clojure](#testing-in-clojure)
5. [Running Tests in REPL with Cursive](#running-tests-in-repl-with-cursive)

## Introduction to Clojure Project Structure

A typical Clojure project structure using `deps.edn` might look like this:

```css
my_project/
├── README.md
├── deps.edn
└── src/
    └── my_project/
        └── core.clj
```

- `README.md`: A Markdown file describing the project.
- `deps.edn`: The dependencies and configuration file for the project.
- `src/`: The source code directory.

## Understanding Namespaces

Namespaces in Clojure act as containers that allow you to organise your functions, variables, and definitions. They generally correlate with the directory structure in your `src/` folder.

For instance, if you have a file located at `src/my_project/core.clj`, the namespace declaration at the top of this file would typically be:

```clojure
(ns my-project.core)
```

## File Structure and `src`

Inside the `src/` directory, your Clojure files should be laid out in a way that mirrors their respective namespaces. For example, a namespace like `my-project.util.helpers` would correspond to a file path of `src/my_project/util/helpers.clj`.

Each `.clj` file within the `src/` directory should represent its own namespace.

## Testing in Clojure

Tests are generally organised in a parallel directory structure under a `test/` folder. The namespaces for these test files usually mirror those of the `src/` directory but append `-test` to the end.

Here's how a simple project structure might look:

```css
my_project/
├── README.md
├── deps.edn
├── src/
│   └── my_project/
│       └── core.clj
└── test/
    └── my_project/
        └── core_test.clj
```

The namespace for the `core_test.clj` file might look like:

```clojure
(ns my-project.core-test
  (:require [clojure.test :refer :all]
            [my-project.core :as sut]))
```

## Running Tests in REPL with Cursive

Running tests directly within the Cursive-integrated REPL in IntelliJ IDEA is very convenient. Instead of manually typing the commands into the REPL, you can use Cursive's keybinds for a more seamless testing experience.

### Steps:

1. **Open the REPL**: Navigate to `View` > `Tool Windows` > `REPL` or use the default keybind `Alt + Shift + D`.
2. **Load the Test File**: Open your test file (`core_test.clj`) and use the keybind `Ctrl + Shift + L` to load the file into the REPL.
3. **Switch to the Test Namespace**: With the test file still open, use the keybind `Ctrl + Shift + N` to switch the REPL namespace to that of your current file.
4. **Run the Tests**: Finally, use the keybind `Ctrl + Shift + T` to run all the tests in the namespace.

These are the default keybinds; if you've customized yours, or if you're experiencing issues, you can refer to the [Cursive documentation](https://cursive-ide.com/userguide/) for further guidance.

## Conclusion

Having a good grasp of how Clojure projects are structured, what namespaces are for, and where to place your tests, will make your Clojure coding journey much more pleasant. Feel free to dive in and start experimenting!
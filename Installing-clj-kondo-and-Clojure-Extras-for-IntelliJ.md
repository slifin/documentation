# Installing clj-kondo and Clojure Extras for IntelliJ: A Beginner's Guide to Early Error Detection

## Introduction

Catching errors early can be a game-changer when you're knee-deep in Clojure development. In this guide, we'll introduce you to two invaluable tools that will elevate your Clojure coding experience—`clj-kondo`, a robust linter, and the Clojure Extras plugin for IntelliJ. These utilities are designed to catch errors and issues as you write code, making your development process smoother and more efficient.

## Prerequisites

- Clojure installed
- IntelliJ IDEA installed
- Cursive plugin installed
- Basic familiarity with Clojure syntax

## Installing clj-kondo

### Using Homebrew (macOS)

1. Open a terminal window and run the following command:

   ```bash
   brew install borkdude/brew/clj-kondo
   ```

### Using Linux

For Linux installation, please refer to the [official `clj-kondo` GitHub repository](https://github.com/clj-kondo/clj-kondo) for detailed installation instructions tailored for different Linux distributions.

### Verifying the Installation

After installation, you can verify that `clj-kondo` is correctly installed by running:

```bash
clj-kondo --version
```

## Installing Clojure Extras Plugin

1. Open IntelliJ IDEA.
2. Go to `File > Settings > Plugins`.
3. In the search bar, type "Clojure Extras" and install the plugin that appears.
4. After installation, you'll be prompted to restart IntelliJ IDEA. Make sure to do so to activate the plugin.

### Automatic Linting

Once you've installed both `clj-kondo` and the Clojure Extras plugin, linting will occur automatically as you type in your Clojure files. This real-time feedback can be incredibly helpful for catching errors early and improving your code quality.

## Conclusion

By installing `clj-kondo` and the Clojure Extras plugin, you're taking valuable steps toward a more efficient and error-free Clojure development experience. These tools offer real-time error detection and enrich your IDE, ensuring that you code more effectively.
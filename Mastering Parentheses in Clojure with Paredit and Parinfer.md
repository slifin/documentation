# Mastering Parentheses in Clojure with Paredit and Parinfer

Navigating the parentheses-laden waters of Clojure can be a daunting task, especially if you're new to languages that rely on s-expressions. Fortunately, tools like Paredit and Parinfer in IntelliJ IDEA's Cursive plugin make it far more manageable. This article guides you through setting up and using these indispensable tools effectively.

## Prerequisites

- IntelliJ IDEA with the Cursive plugin should be installed. If you haven't set this up, refer to the [Embracing REPL-Driven Development.md](https://chat.openai.com/c/Embracing REPL-Driven Development.md) article.
- Clojure should be installed on your machine.

## What Are Paredit and Parinfer?

- **Paredit**: A structural editing mode that offers specific commands for manipulating s-expressions in a balanced way.
- **Parinfer**: An automatic mode that adjusts your code's parentheses based on indentation and line structure.

## Configuring Structural Editing in Cursive

1. Open IntelliJ IDEA and navigate to `Preferences` > `Editor` > `General` > `Smart Keys`.
2. Scroll down to find the `Clojure` section.
3. You'll see a dropdown menu for structural editing. Choose between "Parinfer Smart Mode," "Paredit Style," or "None."
4. Below the dropdown, checkboxes allow you to toggle between structural styles.

### Quick Mode Switching

You can use the "Toggle Structural Editing Style" action from the command palette for quickly switching between Parinfer and Paredit modes.

## Using Paredit

Paredit provides a variety of commands for manipulating Clojure code structurally. While you can always check the specific keybinds in your environment, here are some commonly used Paredit commands for macOS users:

### Paredit Commands (macOS)

- **Slurp Backwards (`Ctrl` + `Cmd` + `J`)**: Moves the closing parenthesis to include the previous element.
- **Slurp Forwards (`Shift` + `Cmd` + `K`)**: Moves the closing parenthesis to include the next element.
- **Barf Backwards (`Ctrl` + `Cmd` + `K`)**: Removes the last element from within the current parentheses.
- **Barf Forwards (`Shift` + `Cmd` + `J`)**: Removes the first element from within the current parentheses.
- **Splice (`Option` + `S`)**: Removes the enclosing parenthesis, effectively splicing its content into the surrounding code.
- **Raise (`Cmd` + `Single Quote`)**: Removes everything in the current parenthesis except the selected expression.
- **Kill (`Ctrl` + `K`)**: Deletes the text from the cursor to the end of the line, but maintains structural integrity.
- **Copy as Kill (`Ctrl` + `Shift` + `K`)**: Copies the text from the cursor to the end of the line.
- **Kill Sexp (`Option` + `Cmd` + `K`)**: Deletes the next s-expression.

...and many more. You can find all these commands in the Structural Editing Menu when you right-click on a Clojure file.

### Most Valuable Commands

- **Slurp and Barf**: These are immensely helpful for quickly rearranging your code.
- **Raise**: Useful when you want to replace an expression with one of its sub-expressions.
- **Kill and Copy as Kill**: Great for moving chunks of code around without breaking structure.

These commands are accessible through both keyboard shortcuts and the right-click 'Structural Editing' menu in IntelliJ IDEA. You can also execute Paredit commands while you're in Parinfer's Smart Mode, giving you the best of both worlds.

### Expanding and Shrinking Selection

- **Expand Selection (`Option` + `Up`)**: Expands your current selection.
- **Shrink Selection (`Option` + `Down`)**: Shrinks your current selection.

### Parinfer Features

1. **Preserve Parentheses**: It keeps parentheses balanced automatically as you type or indent lines.
2. **Indent to Nest**: Automatically indents lines to show nesting levels.

### Parinfer Example

Before:

```clojure
(defn foo [x]
(- x 2)
```

After:

```clojure
(defn foo [x]
  (- x 2))
```

Here, simply indenting the `(- x 2)` line to be a child of `(defn foo [x]` adds the closing parenthesis automatically.

## Conclusion

The world of Clojure parentheses is made infinitely more navigable with tools like Paredit and Parinfer. By understanding how to configure and use these tools, you can significantly improve your Clojure coding experience.
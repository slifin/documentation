# Getting Started with Clojure in 2023

## Introduction

As we move further into the era of functional programming and scalable applications, Clojure continues to be a compelling choice for modern software development. Running on the Java Virtual Machine (JVM), it combines Lisp's expressiveness with Java's extensive libraries, making it a versatile tool for both small and large projects. In this guide, we'll look at how you can get started with Clojure in 2023, focusing on the Clojure CLI tools for a streamlined setup experience.

## Why Choose Clojure?

1. **Functional Programming**: Clojure advocates a functional programming paradigm, leading to cleaner, more modular code.
2. **Java Interoperability**: Leverage Java libraries seamlessly, thanks to Clojure’s excellent JVM support.
3. **Concurrency**: Clojure has robust built-in mechanisms for concurrent and parallel programming.
4. **Lisp Heritage**: Being a Lisp dialect, Clojure supports powerful metaprogramming features.
5. **Community and Ecosystem**: With an active community and a plethora of libraries, you'll find plenty of resources for learning and development.

## Prerequisites

Make sure you have the Java Development Kit (JDK) installed, as Clojure runs on the JVM.

## Setting Up Your Development Environment

### Clojure CLI

The Clojure CLI is increasingly becoming the standard tool for Clojure development. To install it, follow the directions on the [official Clojure website](https://clojure.org/guides/getting_started).

### Starting a REPL Session

After installation, launch a Clojure Read-Eval-Print Loop (REPL) by executing:

```bash
clj
```

## Your First Clojure Programme

In the REPL, you can enter and execute Clojure code. To print "Hello, World!" simply type:

```clojure
(println "Hello, World!")
```

### Core Concepts

#### Variables

To define a variable, use the `def` keyword:

```clojure
(def my-variable 10)
```

#### Functions

To create a function, the `defn` keyword comes into play:

```clojure
(defn greet [name]
  (str "Hello, " name))
```

Invoke the function in the REPL like so:

```clojure
(greet "Alice")
```

### Creating a New Project

To initiate a new project, create a new directory and include a `deps.edn` file to specify your project dependencies. Here is an example:

```clojure
{:deps
 {org.clojure/clojure {:mvn/version "1.11.1"}}}
```

### Managing Dependencies

To add dependencies to your project, simply edit the `deps.edn` file. For instance, to include the Cheshire JSON parsing library, your `deps.edn` file would look like:

```clojure
{:deps
 {org.clojure/clojure {:mvn/version "1.11.1"}
  cheshire/cheshire {:mvn/version "5.12.0"}}}
```

Run the `clj` command again, and your new dependencies will be fetched automatically.

## Conclusion

Getting started with Clojure in 2023 is straightforward, especially with the Clojure CLI tools. They offer a simplified, yet powerful, way to manage dependencies and set up projects. Whether you are new to programming or a seasoned developer looking to diversify your skill set, Clojure has much to offer in building robust, efficient, and scalable applications.
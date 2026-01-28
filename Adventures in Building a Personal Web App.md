# Adventures in Building a Personal Web App

Building a personal web app for sometimes fun, and no profit

### Problem statement

I am tackling my health problems and I am getting fed up of writing out information to LLMs only for them to forget that information as the conversation evolves.

So I decided to build a minimal input system to store a timeline of health events for myself and optionally LLMs to review.

### Ingredients

- Clojure
- HTML
- SQLite

### Rationale

Clojure has been my weapon of choice for a long time and everyday I feel thankful I get to write it - it is a beautiful language with sane defaults:

- Everything is an expression
- Immutable values are first class
- Best in class [reverse debugger](https://www.flow-storm.org/)
- First class support for testing including generative testing

The benefits we'll be leveraging today is how terse the language is and the powerful ecosystem.

### Into the Details

#### The REPL

The first thing I noticed after setting up the webserver (ring-jetty-adapter) was that to see my new changes on the page I needed to do two things load the changes into my REPL and reload the web page.

If you are an [experienced developer](https://www.youtube.com/watch?v=NGYGl_xxfXA) you will understand that this is an unacceptably high barrier to iteration.

Normally I would be reaching for something with hot code reloading which inevitably meant JavaScript 
At the Conj this year David Nolen did a talk on [essentially minimising](https://www.youtube.com/watch?v=BeE00vGC36E) his stack in this vein it turns out there is a straight forward solution in [ring](https://github.com/ring-clojure/ring).

I have added this to my deps.edn under a dev only alias:

```clojure
ring/ring-devel {:mvn/version "1.15.3"}
ring-refresh/ring-refresh {:mvn/version "0.2.0"}
```

And then used them here:

```bash
user.clj
```

```clojure
(:require [ring.middleware.refresh :refer [wrap-refresh]]
          [ring.middleware.reload :refer [wrap-reload]])

(def dev-handler
  (-> #'app
      wrap-reload
      wrap-refresh))
```

where #'app (`reitit.ring/ring-handler`) is essentially my router.

Now when I change my file the repl loads and the browser reloads the tab instantly, Sweet! So far no client side framework required! 

#### Start Up

I'll likely host my application somewhere but I noticed my developer entry point needs to be different from my production entry point
So what I've done is added a defonce statement inside my user.clj and what this does is starts the web server up, with port 0 (this means find me a spare port)
Then I use:

```clojure
port (.getLocalPort (first (.getConnectors jetty-server)))
```

To get the allocated port, then I use `clojure.java.browse/browse-url` to immediately open a browser tab at the correct url and port and path, because its in defonce we don't get a new tab on every reload just on repl start up.

This accelerates me straight into the application when I start the REPL.

#### Dark Mode

So it's been a long time since I've had to do CSS but we have a new feature:

```css
:root {
  color-scheme: dark
}
```

Instant dark mode implementation! - I don't know if I'll keep it but for now we'll see how it behaves.

#### The State

I'm using:

- [sqlite4clj](https://github.com/andersmurphy/sqlite4clj)
- [TablePlus.app](https://tableplus.com/)

I've still not decided what the state of application is yet but something I want to experiment with is the idea of doing event sourcing inside sqlite

This means keeping a table for every form in my application that stores:

| id   | occurred_at | Payload |
| ---- | ----------- | ------- |

Payload will be unstructured likely jsonb, then I'm going to create derived tables that take this history of payloads and creates a normal traditional table out of it.
Id will likely be a uuid, I may also store a serial field to help detect stale form submissions.

My gut says I will need to maintain two situations in my application:

- Update all dependent derived tables inside a single transition per payload.
- A way to completely recalculate every row based on its payloads this will be helpful for debugging and building.

I'm a strong believer as programmers we do not store enough information generally speaking and its holding us back from implementing incredible things.

I will 100% get the schema wrong and will need to change it so I want to keep payload tables immutable and unopinionated about any schema whilst my derived tables can evolve and spread as need be

#### Advertising

Feel free to add me on https://www.linkedin.com/in/adrian-smith-974b4122/ If you like Clojure 

I don't always respond to my messages there but I always read them (usually 6 months too late 😅)
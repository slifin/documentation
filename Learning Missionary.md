# Learning Missionary



Missionary has two primary pieces for handling program execution:

- Tasks
- Flows

A task is a value that represents a piece of work, similar to how to a Clojure function is a value that represents a piece of work to do.

The structure of a task is this:

![Screenshot 2023-08-26 at 14.53.16-3058127](./assets/Screenshot%202023-08-26%20at%2014.53.16-3058127.png)

A task is an action that should terminate in a call to the success function or a call to the error function and a return value or error value.

The returned cancel function when creating the task should be able to cancel work in flight if executed.

The Missionary library has an API that can create different tasks for you:

## Missionary.core/sp

sp stands for sequential process, it accepts a body of Clojure code that can be executed sequentially an example looks like this:

```clojure
(def task (m/sp (println "1")
      					(println "2")
					      (println "3")))
```

The task returned from `m/sp` can run the Clojure code inside by providing the task a success and error function.

```clojure
(task #(println "success:" %) 
      #(println "error:" %))
```

The above form will return a cancellation function, for a `m/sp` created task the returned cancellation function will interrupt execution of the Clojure forms.

The error path can be invoked by throwing an Exception in the Clojure code.

## Missionary.core/?

Instead of defining our own success and error functions we can use `m/?` to invoke the task for us with sensible defaults.

Successful values will be returned and exceptions will be re-thrown.

```clojure
(m/? (m/sp (println "1")
           (println "2")
           (println "3")))
```



## Missionary.core/ap

Ap stands for ambiguous evaluation







https://github.com/leonoel/missionary/blob/master/doc/tutorials/hello_task.md
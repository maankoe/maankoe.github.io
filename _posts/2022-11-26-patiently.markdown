---
layout: post
title:  "Patiently - a polling/retry mechanism"
date:   2022-11-30
categories: testing, async, java
---


# Introduction

[Patiently](https://github.com/maankoe/patiently) is a java library that retries tasks on a given schedule until they are successful (they return successfully without throwing an Exception), or until the schedule finished (a time limit has been reached).

It's predominant use-case, for me, is to simplify testing some threaded tasks and avoid having to mock things I don't want to. Beyond testing, Patiently can be used as a general polling/retry mechanism.

It's available on GitHub: [https://github.com/maankoe/patiently](https://github.com/maankoe/patiently).


# Disclaimer

In no way do I endorse this approach to testing. It is generally considered bad practice to use `Thread.sleep()`, you're probably better off mocking the thing you're testing. [Here is Sonarlint's opinion on it.](https://rules.sonarsource.com/java/RSPEC-2925), which also suggests [awaitatility](http://www.awaitility.org) as a "compliant solution". Awaitatility is clearly more mature than [Patiently](https://github.com/maankoe/patiently). From what I can see, [Patience](https://github.com/redfin/patience) is also a strong alternative.

Having said that, I enjoyed making it and I'm using it in [TimberTally](https://github.com/maankoe/timbertally, should you be interested.



# Usage

In general, you can do the following for a `task` that is either a `Runnable`, `Callable<T>`, or `Supplier<Boolean>`:

```
Patiently.retry(task)
	.every(everyMs)
	.until(untilMs);
```

where `long everyMs` specifies the interval between retries (how often the task is executed) and `long untilMs` specifies the when the task will stop being retried. After `untilMs`, the task will be executed one final time and the result returned (or Exception thrown).

Alternatively, there is an all-in-one:

```
Patiently.retry(task, everyMs, untilMs);
```

Additionally, `retry` can be imported statically.


# Lambdas

Of course, a `Runnable`, `Callable` or `Supplier` can be provided by a lambda in the usual way. The main use-case for patiently (for me) is in retrying an assertion. For example, testing that a slow threaded task completes properly:

```
Task slowTask = Task();
Executors.newSingleThreadExecutor().execute(slowTask);
Patently.retry(() -> assertThat(slowTask.isComplete()).isTrue())
	.every(100)
	.until(1000);
```



# Future

Some interesting extensions to Patiently would be:

* Generalise and provide a variety of RetrySchedules.
* Extend builder DSL to accept different time units other than milliseconds.
* Provide wider set of `PatientX` classes (e.g., `PatientFunction` etc.).


Though unless there is a need (internal or external), it's unlikely I'll be doing these in the near future.







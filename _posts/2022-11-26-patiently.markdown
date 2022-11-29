---
layout: post
title:  "Patiently - assertions for threaded tasks"
date:   2022-11-25
categories: ml
---

# Disclaimer

In no way do I endorse this approach to testing. It is generally considered bad practice to use `Thread.sleep()`, you're probably better off mocking the thing you're testing. [Here is Sonarlint's opinion on it.](https://rules.sonarsource.com/java/RSPEC-2925), which also suggests [awaitatility](http://www.awaitility.org) as a "compliant solution". Awaitatility is clearly more mature than [Patiently](https://github.com/maankoe/patiently). From what I can see, [Patience](https://github.com/redfin/patience) is also a strong alternative.

Having said that, I enjoyed making it and it fitted my use-case ([TimberTally](https://github.com/maankoe/timbertally, if you're interested).

# Usage

In general, you can do the following for a `task` that is either a `Runnable`, `Callable<T>`, or `Supplier<Boolean>`:

```
Patiently.retry(task)
	.every(everyMs)
	.until(untilMs);
```

where `everyMs` and `untilMs` are `long`s Alternatively, there is the shortcut:
```
Patiently.retry(task, everyMs, untilMs);
```
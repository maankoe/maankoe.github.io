---
layout: post
title:  "Testing - a case for the pyramid"
date:   2022-11-30
categories: testing, async, java
---


# Introduction

Often, you see testing split into categories:

1. Unit testing - testing individual components (classes and functions)
2. Integration testing - ensuring those components work together
3. Regression testing - testing the correctness of output data

Within these, smoke testing is really a form of integration testing (with a fail-fast quality),
and functional testing lies somewhere in the middle of integration and regression testing.

The number of tests a software system has of each form, creates a "shape" describing the testing philosophy employed.
Pyramid testing has many unit tests, fewer integration tests, and fewer still regression tests.
Diamond testing has a small number of unit and regression tests, but a large number of integration tests.
Often, it requires only a few regression tests to show the system is producing correct data.
When this is not the case, hourglass testing can be useful, with large numbers of unit and regression tests and a 
smaller number of integration tests.

The two main testing philosophies you often see discussed are pyramid and diamond.
Lately, I have seen a few movements of a preference diamond testing, with integration testing being the priority.
I believe this is as result of the movement to distributed systems, microservices, and the cloud.
It is very tempting, once you have several systems working with one-another, to want to test them working together -
as they do in production.
In my opinion, this is incorrect, and pyramid testing (many more unit than integration tests) is almost always 
preferable.
Here, I will set out why this is the case.



# Testing aims

Tests aren't released. 
We write tests for us, the developers. 
We should choose tests that work for us, not against us.

For each individual test, there is a trade-off between:

* Localisation
* Coverage
* Speed
* Stability

where

* High localisation -> Low coverage
* High coverage -> Low localisation
* High coverage -> Low speed
* High localisation -> High speed

The stability of a test is a little different, as there are two primary factors: code changes and requirements changes.
The only trade-off we have is weak:
* High coverage -> Low stability


In general, we can split tests into two categories:
* Highly localized and fast
* High coverage




For a test strategy we want to write tests that provide high everything, and then run them as the situation suits.
In some cases, practicalities (time constraints) make this difficult, so we should spend our energy intelligently.




# Testing types

Unit tests
Integration tests
End-to-end tests
Smoke tests
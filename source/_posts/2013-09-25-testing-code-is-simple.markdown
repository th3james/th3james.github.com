---
layout: post
title: "Testing code is simple"
date: 2013-09-25 15:39
comments: true
categories: 
---

### A.K.A. "What I wish people had told me about testing"
Test driven development is now widely recognised as 'a good thing', but for developers who aren't already practicing it already, the world of TDD can appear quite compilicated. Choosing a testing framework and assertion library, picking between factories and fixtures, deciding how to handle database state teardown, how to mock objects, what's the correct phrasing of my tests… From the outside, the world of automated software testing can seem like more work than it's worth.

These issues put me off doing diving into TDD for a long time. Having been testing for a while now, here are some of the things I wish people had told me before I started:

## Testing software is actually pretty simple
Writing software tests consists of the following steps:

  1. Write code that interacts with the code you're building
  2. Write assertions about what you expect to happen
  3. There is no step 3

Let's go through an example. Recently, I came to be working on a large client-side JavaScript application. Coming from a Ruby background and having never tested JavaScript before, I wondered what was the simplest setup I could create for testing would be. Here it is:

``` 
  // tests.js, include this on a page with your application code

  /* Our testing library */
  assert = function(result) {
    if (!result) {
      throw new Error("A test failed");
    }
  };
  /* end of testing library */


  /* tests */
  // MyMathLibrary.add given 2 arguments returns their sum
  result = MyMathLibrary.add(1, 2);
  assert(result === 3)

```

That's it. Run this in your browser, if you get an error in your console, your tests are failing. If not, congratlations, your tests are passing. The extent of our testing library is one function called assert, that throws an error when given a false value. 

This is genuinely all you need to start practicing TDD. Write a short description of expected (but unimplemented) behavior, write some code that creates context and assert the expected state. Then write code to make it pass and repeat:

```
  // MyMathLibrary.multiply given 2 numbers returns the multiplication of the 2
  result = MyMathLibrary.multiply(5,3)
  assert(result === 15)
```

## Just start writing tests
Writing well factored, fast, maintainable tests is tricky, and a different skill from writing good code. Expect to be bad at it at first. Don't let this put you off: One of the best things about tests is that even poorly written tests can produce a large amount of value. Just start writing tests and learn as you go.

## Testing is not a DSL
RSpec has a lot to answer for. Most developers starting (particularly in Ruby) will initially be confronted by the 'spec' style of writing tests. I think this is unfortunate, as certainly for me, and I expect for many others, it obscures the fact that tests are just code and assertions. For this reason, I would recommend when starting testing that you avoid the 'spec' style syntax, and instead master the basics using the 'test' or 'unit' style syntax.

```
  # An example in Mocha.js using the 'qunit' syntax
  test('MyMathLibrary.multiply given 2 numbers returns the multiplication of the 2', function(){
    result = MyMathLibrary.multiply(5,3)
    assert(result === 15)
  })
```

## Keep your test setup simple to start
When you start testing, most people will recommend a laundry list of libraries you should use to start testing. Mocking, Factories, Transaction tests… All useful features, but when you're starting out, I'd recommend keeping to a bare minimum: a testing framework for reporting passing/failing tests and an assertion library to get better error messages. My personal picks are:

**Javascript**:

   * Testing: Mocha.js (using the qunit syntax)
   * Assertions: Chai.js (using the assert syntax)

**Ruby**: 

   * Minitest (using the unit syntax)

After you've written tests for a little while, it should become clear why (and if) you need factories, mocking and the rest. Then is the right time to start using them.

## Summary
Testing your code is not only the path to fewer bugs, easier maintainence and confident refactoring, it's also hugely satisfying. As such, it's not surprising that so much tooling and methodology has sprung up around it, and for the most part, these are good things. However, when starting testing, it's easy to confuse these tools and processes for testing itself. I hope this serves as a call not to run before you can walk, and a reminder of the core simplicity of testing.
Regardless of how you choose to test, the most important things that you are doing it. Good luck

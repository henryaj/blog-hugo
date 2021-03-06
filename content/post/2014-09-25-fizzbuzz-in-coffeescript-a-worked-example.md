---
title: FizzBuzz in CoffeeScript – a worked example
date: 2014-09-25T22:02:32
layout: post
---

CoffeeScript is well-documented, succinct language that compiles into JavaScript. If you're bored of JavaScript's abstruse syntax, it's a much more Ruby-like way to approach JavaScript programming – provided you're comfortable with its [caveats](https://donatstudios.com/CoffeeScript-Madness). This assumes you have [node.js installed](http://nodejs.org/download/) and have installed Mocha, CoffeeScript and Chai with the following commands from the folder you're working in:

```
npm install coffee-script
npm install chai
npm install mocha
```

You can also use the `-g` flag when running the above commands to install these packages globally, rather than locally. If you're using Mocha for tests, you need to 'register' a CoffeeScript compiler with Mocha first.

```
mocha --compilers coffee:coffee-script/register
```

You might also have to create a Mocha options file – /test/mocha.opts – and add the following line: `\--compilers coffee:coffee-script/register`

Set up your folder structure like this:

```
 ├── src
 │ └── fizzbuzz.coffee
 └── test
 ├── fizzbuzz_spec.coffee
 └── mocha.opts
```

Now, let's write a test. `test/fizzbuzz_test.coffee`:

```coffeescript
chai = require 'chai'
expect = chai.expect
Fizzbuzz = require '../src/fizzbuzz'

describe 'Fizzbuzz', ->
  it '3 is divisible by 3', ->
    fizzbuzz = new Fizzbuzz()
    expect(fizzbuzz.isDivisibleByThree(3)).to.be.true

  it '1 is not divisible by 3', ->
    fizzbuzz = new Fizzbuzz()
    expect(fizzbuzz.isDivisibleByThree(1)).to.be.false
```

(Note the capital 'F' in Fizzbuzz, because we're declaring a class.) Be careful of that third line above, though – if you have a fizzbuzz.js file it will use that instead of your fizzbuzz.coffee file! And now, the code: `src/fizzbuzz.coffee`:

```coffeescript
class Fizzbuzz
  isDivisibleByThree: (number) -> number % 3 == 0

module.exports = Fizzbuzz
```

And so on... you know how FizzBuzz goes. Here are our tests after a little bit of refactoring – note the `before` method:

```coffeescript
chai = require 'chai'
expect = chai.expect
Fizzbuzz = require '../src/fizzbuzz'

describe 'Fizzbuzz', ->
  before -> @fizzbuzz = new Fizzbuzz()

  it '3 is divisible by 3', ->
    expect(fizzbuzz.isDivisibleByThree(3)).to.be.true

  it '1 is not divisible by 3', ->
    expect(fizzbuzz.isDivisibleByThree(1)).to.be.false
```

Protester is a gem that wraps around your test suite and benchmarks your tests providing a baseline measurement of performance and then warns you about signifigant deviations in performance.

# Installation

Add the following to your Gemfile:
```
gem 'protester'
```
and run `bundle install`

# Description

Protester records each test execution time in a series of yml files.  Then when you update your code Protester compares your new test execution benchmark to its previously recorded benchmark.  If the new execution is longer within a margin of error then protester runs the test several more times until it determines within statistical signifigance that you have increased the execution time of your test.

Protester then warns at the end of your test suite you that you have significantly increased your test execution time (for one or more tests) giving you the opportunity to look for newly introduced performance bottlenecks

Protester is meant to be run on a single environment and is an apples to apples comparison of one environments execution of a test suite.  It is approximate so is not meant for fine tuning of code performance but rather as a tool to alert you to signifigant performance degredations.

# Recommendations

Protester will not perform consistently for tests that are making real time calls to external  API's and other web services and thus it is recommended you use Webmock or other similar libraries to stub out external api calls in your tests.

Protester will also be sensitive to increasing database sizes thus it is recommended that you use a Database cleaner after every test and ensure that your tests are not interdependant or atomic.  In order to achieve this randomizing your tests using a kernel is the best option.
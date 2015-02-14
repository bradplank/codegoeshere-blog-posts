REST Services (Performance vs Readability vs Rapid Development)
===============================================================

We often choose JavaScript libraries to improve our code's performance, readability, and reduce development time.  However, how often do we consider the effects of our choices.  After using the [Async](https://github.com/caolan/async) library to create REST micro services, concerns of performance and readability interest me.  Express and Async together provide the necessary tools to quickly produce REST end points, however, what was the cost of rapid development.

After searching around, I have found existing tests that compare [Nimble vs lodash vs jQuery](http://jsperf.com/nimble-vs-lodash-vs-jquery).  I have seen drastic performance differences between Chrome and Safari, however, both browsers yield about the same result.  Lodash is ~50% than Async for loop processing.

The next part was to compare performance and readability of [Async vs Bluebird](http://jsperf.com/async-vs-bluebird-comparing) (a promise library).  The performance test link is currently broken.  I will create an updated comparison soon, as I am curious about the tradoffs between the use of Async and Bluebird.

**References**

* [jsPerf](http://jsperf.com) - JavaScript performance playground
* [Async.js](https://github.com/caolan/async) - Async utilities for node and the browser
* [Bluebird](https://github.com/petkaantonov/bluebird) - Bluebird is a fully featured promise library with focus on innovative features and performance
* [lodash](https://lodash.com) - A JavaScript utility library delivering consistency, modularity, performance, & extras
* [jQuery](http://jquery.com) - jQuery is a fast, small, and feature-rich JavaScript library
* [Express.js](http://expressjs.com) - Fast, unopinionated, minimalist web framework for Node.js

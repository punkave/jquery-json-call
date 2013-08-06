# jquery-json-call

<a href="http://apostrophenow.org/"><img src="https://raw.github.com/punkave/jquery-json-call/master/logos/logo-box-madefor.png" align="right" /></a>

`jquery-json-call` makes it easy to make an API request to a URL with JSON in BOTH directions. Say goodbye to the limitations of the query string format. Your nulls will stay null! Your numbers will remain numbers!

## How to Use

    $.jsonCall('/my-api', { limit: 5, type: 'blue' }, function(results) {
      // Iterate over the results array output by the server on success
    }, function() {
      // Optional second function to be called on failure. This means
      // a failure at the HTTP level (404, 500, etc)
    });

Here's a node.js Express example on the server side.

    app.post('/my-api', function(req, res) {
      collection.find({ type: req.body.type }).limit(req.body.limit).toArray(function(err, results) {
        return res.send(results);
      });
    });

Notice we didn't have to do anything special on the server side to handle JSON? Express is great like that.

## Requirements

You need jQuery, of course. `jquery-json-call` is actively supported with jQuery 1.9 and 2.0 but should work fine with somewhat older versions.

If you wish your code to work in browsers that do not support `JSON.stringify`, you will need [Douglas Crockford's JSON2 shim](https://github.com/douglascrockford/JSON-js) or a similar shim that provides `JSON.stringify`. However note that even IE8 supports it out of the box.

The server on the other end must understand requests posted with the `application/json` content type.

This is a pain in PHP, but extremely easy with node.js and Express: you will find the object you passed to `$.jsonCall` in `req.body`. Boom! That's it. [If you are stuck with PHP, you may find this helpful.](http://stackoverflow.com/questions/3063787/handle-json-request-in-php)

The server's response must also be JSON. However you don't have to set the content type explicitly as long as what you output is valid JSON.

Again, with Express you can just write:

    res.send({ an: object, with: properties, so: cool });

Arrays are valid responses too.

## About P'unk Avenue and Apostrophe

`jquery-json-call` was created at [P'unk Avenue](http://punkave.com) for use in Apostrophe, an open-source content management system built on node.js. If you like `jquery-json-call` you should definitely [check out apostrophenow.org](http://apostrophenow.org). Also be sure to visit us on [github](http://github.com/punkave).

## Support

Feel free to open issues on [github](http://github.com/punkave/jquery-json-call).

<a href="http://punkave.com/"><img src="https://raw.github.com/punkave/jquery-json-call/master/logos/logo-box-builtby.png" /></a>


### URI.js
---
https://github.com/medialize/URI.js/

```js
var url = "http://example.com/foo?bar=baz";
var separator = url.indexOf('?') > -1 ? '&' : '?';
url += separator + encodeURIComponent("foo") + "=" + encodeURIComponent("bar");

var url = new URI("http://example.org/foo?bar=bax");
url.addQuery("foo", "bar");

URI("http://example.org/foo.html?hello=world")
  .username("rodneyrehm")
  .username("")
  .directory("bar")
  .suffix("xml")
  .query("")
  .tld("com")
  .query({ foo: "bar", hello: ["world", "mars"] })
URI("?&foo=bar&&foo=bar&foo=baz&")
  .normalizeQuery();
URI("/foo/bar/baz.html")
  .relativeTo("/foo/bar/world.html");
URI("/foo/bar/baz.html")
  .relativeTo("/foo/bar/sub/world.html")
  .absoluteTo("/foo/bar/sub/world.html");
URI.expand("/foo/{dir}/{file}", {
  dir: "bar",
  file: "world.html"
});

 // load URI.js
var URI = require('urijs');
var URITemplate = require('urijs/src/URITemplate');
URI("/foo/bar/bax.html")
  .relativeTo("/foo/bar/sub/world.html")

require.config({
  paths: {
    urijs: 'where-you-put-uri.js/src'
  }
});
require(['urijs/URI'], function(URI){
  console.log("URI.js and dependencies: ", URI("//amazon.co.uk").is('sld') ? 'loaded' : 'failed');
});
require(['urijs/URITemplate'], function(URITemplate){
  console.log("URITemplate.js and dependencies: ", URITemplate._cache ? 'loaded' : 'failed');
});

```

```
bower install uri.js
npm install urijs
```

```
//@compilation_level SIMPLE_OPTIMIZATIONS
//@output_file_name URI.min.js
//@code_url http://medialize.github.io/URI.jd/src/IPv6.js
//
```

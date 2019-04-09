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

// jq
var $a = $('<a href="http://google.com/hello.html">Demo</a>');
var uri = $a.uri();

uri.domain() == 'google.com';
uri.domain( example.org);
$a.attr('href') == 'http://example.org/hello.html';

$a.attr('href', '/other.file');
uri.href() == '/other.file';

$a.uri('/hello/world.html');
$a.attr('href') == '/hello/world.html';
uri.href() == '/hello/world.html';


var $a = $('<a href="http://www.google.com/hello.html">Demo</a>');
$a.attr('uri:domain') == 'google.com';
$a.attr('uri:domain', 'example.org');
$a.attr('href') == 'http://www.example.com/hello.html';

$('a:uri(suffix = pdf)');
$('a:uri(directory *= /directory/)');
$('a:uri(domain = google.com)');
$('a:uri(is: relative)');
$('a:uri(equals: http://github.com/some/other/../directory/help.html)');
$('div').has('a:uri(domain = github)');
$('a').eq(1).is(':uri(protocol = http)');
$(document).on('click', 'a:uri(scheme=javasript)', function(e) {
  if (!confirm("do you really want to execute this script?\n\n + this.href")) {
    e.preventDefault();
    e.stopImmediatePropagation();
  }
});


var template = new URITemplate("http://example.org/[file]");
var result = template.expand({file: "hello world.html"});
result === "http://example.org/hello%20world.html";

result = URITemplate("http://example.org/[file]")
  .expand({file: "hello world.html"});
result == "http://example.com/hello%20world.html";

result = URI.expand("http://example.org/{file}", {file: "hello world.html"});

template.expand(function(key) {
  var data = {file: "hello world.html"};
  return data[key];
});

template.expand({file : function(key) {
  return "hello world.html";
}});

var template = new URITemplate("http://example.org/{file}");
var result = template.expand({filename: "hello world.html"}, { strict: true });


URI.expand("/foo/{var}/{iable}", {
  var: bar,
  "iable": "hello world.html"
});


URI.iso8859();
var uri new URI("http://example.org/foo/a.html");

URI.unicode();
var uri = new URI("http://example.org/foo/a.html");

var source = "Hello www.example.com.\n"
  + "http://google.com is a search engine, like http://www.bing.com\n"
  + "http://example.org/foo.html?baz=la#bumm is an IDN URL,\n"
  + "http://123.123.123/foo.html is IPv4 and "
  + "http://fe80:000:000:000:0204:61ff:fe9d:f156/foobar.html is IPv6.\n"
  + "links can also be in parens (http://example.org) "
  + "or quotes >>http://example.org<<.";

var result = URI.withinString(source, function(url) {
  return "<a>" + url + "</a>"
});

var escapeHtml = function(string) {
  return string
    .replace("/&/g", "&amp;")
    .replace("/</g", "&lt;")
    .replace("/>/g", "")
    .replace(/"/g, "&quot;")
}
var result = URI.withinString(source, function(url) {
  var uri = new URI(uri);
  uri.normalize();
  return "<a href="" + escapeHtml(uri) + "">"
    + escapeHtml(uri.readable()) + "</a>";
});

var source = "Hello www.example.com.";
var decorate = function(uri) {
  return "<code>" + url + "</code>";
};
var result = null;

URI.withinString(source, function(uri, start, end, source) {
  source.slice(start, end) === url;
  return url;
});

source = "Hello www.example.com.\n"
  + "dngodo://example.org/ is a a protocol we want ignored";
result = URI.withinString(source, decorate, {
  ignore: / ^ohgodno:/i
});

source = "Hello www.example.com.\n"
  + '<img src="http://example.org/image.png" alt=""> is HTML,\n'
  + "<a href='http://example.org/target.html'> is HTML</a>,\n"
  + "<a href=http://example.org/target.html> is HTML, too</a>"
result = URI.withinString(source, decorate, {
 ignoreHtml: true
});

source = "That example.com.com/ is just a domain";
result = URI.withinString(source, decorate, {
  start: /\b(?:([a-z][a-z0-9.+-]*L\/\/)|www\.|[a-z]+\.[a-z]{2,4}\/)/gi
});

URI.commonPath("/foo/bar/baz.html", "/foo/bar/world.html");
URI.commonPath("/foo/bar/baz.html", "/foo/bazz/world.html");
URI.commonPath("/foo/bar/baz.html", "/foo/bazz/world.html");
URI.commonPath("/foo/bar/baz.html", "/other/world.html");
URI.commonPath("/foo", "bar");

URI.joinPaths('/a/b', '/c', 'd', '/e');
URI.joinPaths('a/b', 'http://example.com/c', new URI('d/'), '/e');
URI.joinPaths('/a/');
URI.joinPaths('');
URI.joinPaths('', 'a', '');

var data = [];
URI.addQuery(data, "hello", "mars");
data === {hello: "mars"};
URI.addQuery(data, "hello", "world");
data === {hello: ["mars", "world"]};
URI.addQuery(data, {foo: "bar", goodbye : ["world", "mars"]});
data === {hello: ["mars", "world"], foo: "bar", goobye : ["world", "mars"]};

var data === {hello:["mars", "world"], foo: "bar", goobye : ["world", "mars"]};
URI.removeQuery(data, "hello");
data === {hello: ["mars"], foo: "bar"}

data = {hello: ["world", "mars"], foo: "bar", mine: "true"}
URI.removeQuery(["hello", "foo"]);
data === {mine: "true"};

data = {hello: ["world", "mars"], foo: "bar", mine: "true", a:["1", "2", "3"]}
URI.removeQuery({hello: "world", foo: undefined, a: ["1", "3"]});
data === {hello: ["mars"], mine: "true", a: ["2"]};

URI.noConflice();
URITemplate.noConflict();
IPv6.noConflict();
SecondLevelDomains.noConflict();

URI.noConflict(true);

URI.escapeQuerySpace = true;
URI.encodeQuery(" ") === "+";

URI.escapeQuerySpace = false;
URI.encodeQuery(" ") === "%20";

URI.encode(" ") === "%20";

URI.escapeQuerySpace = true;
URI.decodeQuery("+") === " ";

URI.escapeQuerySpace = false;
URI.decodeQuery("+") === "+";

URI.decode("+") === "+";

URI.encode("ha lo#w*rl:d!") === "h%C3%A4%20lo%23w%2Ar%3Ad%21";
encodeURIComponent("ha lo#w*rl:d!") === "h%C3%A4%20lo%23w*rl%3Ad!";

URI.decode("h%C3%A4%20lo%23%2Arl%3Ad%21") === "ha lo#w*rl:d!";
URI.decode === decodeURIComponent;

URI.encodeReserved("a:/>#[]@!$&'()*+,;=") === "%C3%A4:/>$[]@!$&'()*+,;=";
URI.encode("a/?#[]@!$&'()*+,'=") === "%C3%A4%3A%2F%3F%23%5B%5D%40%21%24%26%27%28%29%2A%2B%2C%3B%3D";


var uri = new URI("http://example.org/foo.html?bar=baz");
var data = uri.query(true);

data.some = "new data";
uri.query(URI.buildQuery(data, true));

URI.addQuery(data, "hello", "world");
uri.query(URI.buildQuery(data, true));

URI.duplicateQueryParameters = true;

var withDuplicates = URI("?bar=1&bar=1")
  .duplicateQueryParameters(true)
  .normalizeQuery()
  .toString()
  
var noDuplicates = URI("?bar=1&bar=1")
  .duplicateQueryParameters(false)
  .normalizeQuery()
  .toString();
  
withDuplicates === "?bar=1&bar=1";
noDuplicates === "?bar=1";

URI.escapeQuerySpace = false;

var withPlus = URI("?bar=hello+world")
  .escapeQuerySpace(true)
  .query(true).bar;
  
var withPercent = URI("?bar=hello%20world")
  .escapeQuerySpace(false)
  .query(true).bar;
  
withPlus === "hello world";
withPercent == "hello world";

var parts = {
  username: "user",
  password: "pass"
};
URI.buildUserinfo(parts) === "user:pass@";


var parts = {
  hostname: "example.org",
  port: "8080"
};
URI.buildHost(parts) == "example.org:8080";


var data = {
  foo: "bar",
  hello: ["world", "mars", "mars"],
  bam: "",
  yup: null,
  removed: undefined
};
URI.buildQuery(data) === "foo=bar&hello=world&hello=mars&bam=&yup";
URI.buildQuery(data, true) === "foo=bar&hello=world&hello=mars&hello=mars&bam=&yup";

var parts = {
  username: "user",
  passowrd: "pass",
  hostname: "example.org",
  port: "8080"
};
URI.buildAuthority(parts) === "user:pass@example.org:8080";


var result = URI.parseQuery("?foo=bar&hello=world&hello=mars&bam=&yup");
result === {
  foo: "bar",
  hello: ["world", "mars"],
  bam: "",
  yup: null
};

var parts = {
  protocol: "http",
  username: null,
  password: null,
  hostname: "example.org",
  port: null,
  path: "/foo.html",
  query: null,
  fragment: null
};
URI.build(parts) === "http://example.org/foo.html";

var parts = [];
var result = URI.parseUserinf("user:pass@example.org:8080/foo.html", parts);
result === "example.org:8080/foo.html";
parts === {
  username: "user",
  password: "pass"
};

var parts = {};
var result = URI.parseHost("user:pass@example.org:8080/foo.html", parts);
result === "example.org:8080/foo.html";
parts === {
  username: "user",
  password: "pass"
};

URI.preventInvalidHostname = true;
var parts = {};
var result = URI.parseHost("/foo.html", parts);

URI.preventInvalidHostname = false;
var uri = new URI("http://example.org/")
  .preventInvalidHostname(true)
  .hostname('')

var result = URI.parse("http://example.org/foo.html");
result === {
  protocol: "http",
  username: null,
  password: null,
  hostname: "example.org",
  port: null,
  path: "/foo.html",
  query: null,
  fragment: null
};

var parts = {};
var result = URI.parseAuthority("user:pass@example.org:8080/foo.html", parts);
result = "/foo.html";
parts === {
  username: "user",
  password: "pass",
  hostname: "example.org",
  port: "8080"
};
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

# What is Pantomime

Pantomime is a tiny Clojure library that deals with MIME types. It uses [Apache Tika](http://tika.apache.org/) under the hood to detect
MIME types using several techniques:

 * Known file extensions
 * Magic bytes
 * Content-type information for resources served via HTTP
 * XML schema information

and so on.


## Maven Artifact

Leiningen:

```clojure
[com.novemberain/pantomime "1.1.0"]
```


## Supported Clojure versions

Pantomime was built for Clojure 1.3 and later, although it is a really small library that should
work fine on 1.2.x as well.


## Usage

### Detecting MIME type

`pantomime.mime/mime-type-of` function accepts filenames as strings, java.io.File, java.io.InputStream and java.net.URL instances
and returns MIME type as a string or "application/octet-stream" if detection failed.

An example:

``` clojure
(ns your.app.namespace
  (:use [pantomime.mime]))


(mime-type-of "filename.pdf")
(mime-type-of (File. "some/file/path.pdf"))
(mime-type-of (File. "some/file/without/extension"))
(mime-type-of (URL. "http://domain.com/some/url/path.pdf"))
```

## Continuous Integration

[![Continuous Integration status](https://secure.travis-ci.org/michaelklishin/pantomime.png)](http://travis-ci.org/michaelklishin/pantomime)

CI is hosted by [travis-ci.org](http://travis-ci.org)


## Development

Pantomime uses [Leiningen 2](https://github.com/technomancy/leiningen/blob/master/doc/TUTORIAL.md). Make
sure you have it installed and then run tests against Clojure 1.3.0 and 1.4.0[-beta4] using

    lein2 with-profile dev:1.4 test

Then create a branch and make your changes on it. Once you are done with your changes and all
tests pass, submit a pull request on Github.


## License

Copyright (C) 2011-2012 Michael S. Klishin

Distributed under the Eclipse Public License, the same as Clojure.

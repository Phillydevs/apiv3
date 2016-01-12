httpbin(1): HTTP Request & Response Service
===========================================

Freely hosted in `HTTP <http://httpbin.org>`__,
`HTTPS <https://httpbin.org>`__ & `EU <http://eu.httpbin.org/>`__
flavors by `Runscope <https://www.runscope.com/>`__

|Deploy|_

.. |Deploy| image:: https://www.herokucdn.com/deploy/button.svg
.. _Deploy: https://heroku.com/deploy?template=https://github.com/phillydevs/apiv3

|Build Status|

ENDPOINTS
---------

======================================   ==================================================================================================================
Endpoint                                 Description
--------------------------------------   ------------------------------------------------------------------------------------------------------------------
`/`_                                     This page.
`/ip`_                                   Returns Origin IP.
`/user-agent`_                           Returns user-agent.
`/headers`_                              Returns header dict.
`/get`_                                  Returns GET data.
`/post`                                  Returns POST data.
`/patch`                                 Returns PATCH data.
`/put`                                   Returns PUT data.
`/delete`                                Returns DELETE data
`/gzip`_                                 Returns gzip-encoded data.
`/deflate`_                              Returns deflate-encoded data.
`/status/:code`_                         Returns given HTTP Status code.
`/response-headers`_                     Returns given response headers.
`/redirect/:n`_                          302 Redirects *n* times.
`/redirect-to?url=foo`_                  302 Redirects to the *foo* URL.
`/relative-redirect/:n`_                 302 Relative redirects *n* times.
`/cookies`_                              Returns cookie data.
`/cookies/set?name=value`_               Sets one or more simple cookies.
`/cookies/delete?name`_                  Deletes one or more simple cookies.
`/basic-auth/:user/:passwd`_             Challenges HTTPBasic Auth.
`/hidden-basic-auth/:user/:passwd`_      404'd BasicAuth.
`/digest-auth/:qop/:user/:passwd`_       Challenges HTTP Digest Auth.
`/stream/:n`_                            Streams *n* – 100 lines.
`/delay/:n`_                             Delays responding for *n* – 10 seconds.
`/drip`_                                 Drips data over a duration after an optional initial delay, then (optionally) returns with the given status code.
`/range/:n`_                             Streams *n* bytes, and allows specifying a *Range* header to select a subset of the data. Accepts a *chunk\_size* and request *duration* parameter.
`/html`_                                 Renders an HTML Page.
`/robots.txt`_                           Returns some robots.txt rules.
`/deny`_                                 Denied by robots.txt file.
`/cache`_                                Returns 200 unless an If-Modified-Since or If-None-Match header is provided, when it returns a 304.
`/cache/:n`_                             Sets a Cache-Control header for *n* seconds.
`/bytes/:n`_                             Generates *n* random bytes of binary data, accepts optional *seed* integer parameter.
`/stream-bytes/:n`_                      Streams *n* random bytes of binary data, accepts optional *seed* and *chunk\_size* integer parameters.
`/links/:n`_                             Returns page containing *n* HTML links.
`/forms/post`_                           HTML form that submits to */post*
`/xml`_                                  Returns some XML
`/encoding/utf8`_                        Returns page containing UTF-8 data.
======================================   ==================================================================================================================

.. _/user-agent: http://hooked.dockerd.io/user-agent
.. _/headers: http://hooked.dockerd.io/headers
.. _/get: http://hooked.dockerd.io/get
.. _/: http://hooked.dockerd.io/
.. _/ip: http://hooked.dockerd.io/ip
.. _/gzip: http://hooked.dockerd.io/gzip
.. _/deflate: http://hooked.dockerd.io/deflate
.. _/status/:code: http://hooked.dockerd.io/status/418
.. _/response-headers: http://hooked.dockerd.io/response-headers?Content-Type=text/plain;%20charset=UTF-8&Server=httpbin
.. _/redirect/:n: http://hooked.dockerd.io/redirect/6
.. _/redirect-to?url=foo: http://hooked.dockerd.io/redirect-to?url=http://example.com/
.. _/relative-redirect/:n: http://hooked.dockerd.io/relative-redirect/6
.. _/cookies: http://hooked.dockerd.io/cookies
.. _/cookies/set?name=value: http://hooked.dockerd.io/cookies/set?k1=v1&k2=v2
.. _/cookies/delete?name: http://hooked.dockerd.io/cookies/delete?k1&k2
.. _/basic-auth/:user/:passwd: http://hooked.dockerd.io/basic-auth/user/passwd
.. _/hidden-basic-auth/:user/:passwd: http://hooked.dockerd.io/hidden-basic-auth/user/passwd
.. _/digest-auth/:qop/:user/:passwd: http://hooked.dockerd.io/digest-auth/auth/user/passwd
.. _/stream/:n: http://hooked.dockerd.io/stream/20
.. _/delay/:n: http://hooked.dockerd.io/delay/3
.. _/drip: http://hooked.dockerd.io/drip?numbytes=5&duration=5&code=200
.. _/range/:n: http://hooked.dockerd.io/range/1024
.. _/html: http://hooked.dockerd.io/html
.. _/robots.txt: http://hooked.dockerd.io/robots.txt
.. _/deny: http://hooked.dockerd.io/deny
.. _/cache: http://hooked.dockerd.io/cache
.. _/cache/:n: http://hooked.dockerd.io/cache/60
.. _/bytes/:n: http://httpbin.org/bytes/1024
.. _/stream-bytes/:n: http://hooked.dockerd.io/stream-bytes/1024
.. _/links/:n: http://hooked.dockerd.io/links/10
.. _/forms/post: http://hooked.dockerd.io/forms/post
.. _/xml: http://hooked.dockerd.io/xml
.. _/encoding/utf8: http://hooked.dockerd.io/encoding/utf8


DESCRIPTION
-----------

Testing an HTTP Library can become difficult sometimes.
`RequestBin <http://requestb.in>`__ is fantastic for testing POST
requests, but doesn't let you control the response. This exists to cover
all kinds of HTTP scenarios. Additional endpoints are being considered.

All endpoint responses are JSON-encoded.

EXAMPLES
--------

$ curl http://hooked.dockerd.io/ip
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

::

    {"origin": "24.127.96.129"}

$ curl http://hooked.dockerd.io/user-agent
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

::

    {"user-agent": "curl/7.19.7 (universal-apple-darwin10.0) libcurl/7.19.7 OpenSSL/0.9.8l zlib/1.2.3"}

$ curl http://hooked.dockerd.io/get
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

::

    {
       "args": {},
       "headers": {
          "Accept": "*/*",
          "Connection": "close",
          "Content-Length": "",
          "Content-Type": "",
          "Host": "hooked.dockerd.io",
          "User-Agent": "curl/7.19.7 (universal-apple-darwin10.0) libcurl/7.19.7 OpenSSL/0.9.8l zlib/1.2.3"
       },
       "origin": "24.127.96.129",
       "url": "hooked.dockerd.io/get"
    }

$ curl -I http://hooked.dockerd.io/status/418
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

::

    HTTP/1.1 418 I'M A TEAPOT
    Server: nginx/0.7.67
    Date: Mon, 13 Jun 2011 04:25:38 GMT
    Connection: close
    x-more-info: http://tools.ietf.org/html/rfc2324
    Content-Length: 135

$ curl https://hooked.dockerd.io/get?show\_env=1
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

::

    {
      "headers": {
        "Content-Length": "",
        "Accept-Language": "en-US,en;q=0.8",
        "Accept-Encoding": "gzip,deflate,sdch",
        "X-Forwarded-Port": "443",
        "X-Forwarded-For": "109.60.101.240",
        "Host": "httpbin.org",
        "Accept": "text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8",
        "User-Agent": "Mozilla/5.0 (X11; Linux i686) AppleWebKit/535.11 (KHTML, like Gecko) Chrome/17.0.963.83 Safari/535.11",
        "X-Request-Start": "1350053933441",
        "Accept-Charset": "ISO-8859-1,utf-8;q=0.7,*;q=0.3",
        "Connection": "keep-alive",
        "X-Forwarded-Proto": "https",
        "Cookie": "_gauges_unique_day=1; _gauges_unique_month=1; _gauges_unique_year=1; _gauges_unique=1; _gauges_unique_hour=1",
        "Content-Type": ""
      },
      "args": {
        "show_env": "1"
      },
      "origin": "109.60.101.240",
      "url": "http://httpbin.org/get?show_env=1"
    }

Installing and running from PyPI
--------------------------------

You can install httpbin as a library from PyPI and run it as a WSGI app.
For example, using Gunicorn:

.. code:: bash

    $ pip install httpbin
    $ gunicorn httpbin:app

Or run it directly:

.. code:: bash

    $ python -m httpbin.core

Changelog
---------
-  0.4.1: Added floating-point support for /delay endpoint
-  0.4.0: New /image/svg endpoint, add deploy to heroku button, add 406 response to /image, and don't always emit the transfer-encoding header for stream endpoint.
-  0.3.0: A number of new features, including a /range endpoint, lots of
   bugfixes, and a /encoding/utf8 endpoint
-  0.2.0: Added an XML endpoint. Also fixes several bugs with unicode,
   CORS headers, digest auth, and more.
-  0.1.2: Fix a couple Python3 bugs with the random byte endpoints, fix
   a bug when uploading files without a Content-Type header set.
-  0.1.1: Added templates as data in setup.py
-  0.1.0: Added python3 support and (re)publish on PyPI

AUTHOR
------

A `Runscope Community Project <https://www.runscope.com/community>`__.
Originally created by `Kenneth Reitz <http://kennethreitz.com/>`__.

SEE ALSO
--------

- https://www.dockerd.io
- http://requestb.in
- http://python-requests.org

.. |Build Status| image:: https://travis-ci.org/Runscope/httpbin.svg
   :target: https://travis-ci.org/phillydevs/apiv3

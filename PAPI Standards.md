## HTTP Header

HTTP Headers are used to pass control data and metadata for an HTTP request and/or response.  The Platform APIs support many of the [standard](https://www.iana.org/assignments/message-headers/message-headers.xhtml) HTTP request and response headers, as well as some de facto standard and Dow Jones defined custom headers.  Our policy is to whitelist headers (both request and response) at the public-facing Platform API layer in order to tighten security (deter hackers looking to find security wholes in commen web service stacks).  Platform Services (non-public facing) are free to support additional headers for communication with other Platform Services (again, non-public facing), yet each header should be defined and documented with the support of the API Governance team to standardize the use of those headers. 

Following are the HTTP request and response headers approved for use in our public-facing Platform APIs endpoints:

### Standard Request Headers

Name | Description | Values/Example
-------|------------------------------------------------------------------------------|--------
Accept | Content-Types that are acceptable for the response. See Content negotiation. | Accept: text/plain
Accept-Charset | Character sets that are acceptable. | Accept-Charset: utf-8
Accept-Encoding | List of acceptable encodings. See HTTP compression. | Accept-Encoding: gzip, deflate
Accept-Language | List of acceptable human languages for response. See Content negotiation. | Accept-Language: en-US
Accept-Datetime | Acceptable version in time. | Accept-Datetime: Thu, 31 May 2007 20:35:00 GMT
Authorization | Authentication credentials for HTTP authentication. | Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==
Cache-Control | Used to specify directives that must be obeyed by all caching mechanisms along the request-response chain. | Cache-Control: no-cache
Connection | Control options for the current connection and list of hop-by-hop request fields.[8] | Connection: keep-aliveConnection: Upgrade
Cookie | An HTTP cookie previously sent by the server with Set-Cookie (below). | Cookie: $Version=1; Skin=new;
Content-Length | The length of the request body in octets (8-bit bytes). | Content-Length: 348
Content-Type | The MIME type of the body of the request (used with POST and PUT requests). | Content-Type: application/x-www-form-urlencoded
Date | The date and time that the message was originated (in "HTTP-date" format as defined by RFC 7231 Date/Time Formats). | Date: Tue, 15 Nov 1994 08:12:31 GMT
Expect | Indicates that particular server behaviors are required by the client. | Expect: 100-continue
Forwarded | Disclose original information of a client connecting to a web server through an HTTP proxy.[10] | Forwarded: for=192.0.2.60;proto=http;by=203.0.113.43Forwarded: for=192.0.2.43, for=198.51.100.17
From | The email address of the user making the request. | From: user@example.com
Host | The domain name of the server (for virtual hosting), and the TCP port number on which the server is listening. The port number may be omitted if the port is the standard port for the service requested.[11] Mandatory since HTTP/1.1. | Host: en.wikipedia.org:8080Host: en.wikipedia.org
If-Match | Only perform the action if the client supplied entity matches the same entity on the server. This is mainly for methods like PUT to only update a resource if it has not been modified since the user last updated it. | If-Match: "737060cd8c284d8af7ad3082f209582d"
If-Modified-Since | Allows a 304 Not Modified to be returned if content is unchanged. | If-Modified-Since: Sat, 29 Oct 1994 19:43:31 GMT
If-None-Match | Allows a 304 Not Modified to be returned if content is unchanged, see HTTP ETag. | If-None-Match: "737060cd8c284d8af7ad3082f209582d"
If-Range | If the entity is unchanged, send me the part(s) that I am missing; otherwise, send me the entire new entity. | If-Range: "737060cd8c284d8af7ad3082f209582d"
If-Unmodified-Since | Only send the response if the entity has not been modified since a specific time. | If-Unmodified-Since: Sat, 29 Oct 1994 19:43:31 GMT
Max-Forwards | Limit the number of times the message can be forwarded through proxies or gateways. | Max-Forwards: 10
Origin | Initiates a request for cross-origin resource sharing (asks server for an 'Access-Control-Allow-Origin' response field). | Origin: http://www.example-social-network.com
Pragma | Implementation-specific fields that may have various effects anywhere along the request-response chain. | Pragma: no-cache
Proxy-Authorization | Authorization credentials for connecting to a proxy. | Proxy-Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==
Range | Request only part of an entity. Bytes are numbered from 0. See Byte serving. | Range: bytes=500-999
Referer [sic] | This is the address of the previous web page from which a link to the currently requested page was followed. (The word “referrer” has been misspelled in the RFC as well as in most implementations to the point that it has become standard usage and is considered correct terminology) | Referer: http://en.wikipedia.org/wiki/Main_Page
TE | The transfer encodings the user agent is willing to accept: the same values as for the response header field Transfer-Encoding can be used, plus the "trailers" value (related to the "chunked" transfer method) to notify the server it expects to receive additional fields in the trailer after the last, zero-sized, chunk. | TE: trailers, deflate
User-Agent | The user agent string of the user agent. | User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:12.0) Gecko/20100101 Firefox/21.0
Upgrade | Ask the server to upgrade to another protocol. | Upgrade: HTTP/2.0, HTTPS/1.3, IRC/6.9, RTA/x11, websocket
Via | Informs the server of proxies through which the request was sent. | Via: 1.0 fred, 1.1 example.com (Apache/1.1)
Warning | A general warning about possible problems with the entity body. | Warning: 199 Miscellaneous warning


### Standard Response Headers

Name | Description | Values/Example
-------|------------------------------------------------------------------------------|--------
Access-Control-Allow-Origin | Specifying which web sites can participate in cross-origin resource sharing | Access-Control-Allow-Origin: *
Accept-Patch[31] | Specifies which patch document formats this server supports | Accept-Patch: text/example;charset=utf-8
Accept-Ranges | What partial content range types this server supports via byte serving | Accept-Ranges: bytes
Age | The age the object has been in a proxy cache in seconds | Age: 12
Allow | Valid methods for a specified resource. To be used for a 405 Method not allowed | Allow: GET, HEAD
Alt-Svc[32] | A server uses "Alt-Svc" header (meaning Alternative Services) to indicate that its resources can also be accessed at a different network location (host or port) or using a different protocol | Alt-Svc: h2="http2.example.com:443"; ma=7200
Cache-Control | Tells all caching mechanisms from server to client whether they may cache this object. It is measured in seconds | Cache-Control: max-age=3600
Connection | Control options for the current connection and list of hop-by-hop response fields[8] | Connection: close
Content-Disposition[33] | An opportunity to raise a "File Download" dialogue box for a known MIME type with binary format or suggest a filename for dynamic content. Quotes are necessary with special characters. | Content-Disposition: attachment; filename="fname.ext"
Content-Encoding | The type of encoding used on the data. See HTTP compression. | Content-Encoding: gzip
Content-Language | The natural language or languages of the intended audience for the enclosed content[34] | Content-Language: da
Content-Length | The length of the response body in octets (8-bit bytes) | Content-Length: 348
Content-Location | An alternate location for the returned data | Content-Location: /index.htm
Content-Range | Where in a full body message this partial message belongs | Content-Range: bytes 21010-47021/47022
Content-Type | The MIME type of this content | Content-Type: text/html; charset=utf-8
Date | The date and time that the message was sent (in "HTTP-date" format as defined by RFC 7231) [35] | Date: Tue, 15 Nov 1994 08:12:31 GMT
ETag | An identifier for a specific version of a resource, often a message digest | ETag: "737060cd8c284d8af7ad3082f209582d"
Expires | Gives the date/time after which the response is considered stale (in "HTTP-date" format as defined by RFC 7231) | Expires: Thu, 01 Dec 1994 16:00:00 GMT
Last-Modified | The last modified date for the requested object (in "HTTP-date" format as defined by RFC 7231) | Last-Modified: Tue, 15 Nov 1994 12:45:26 GMT
Link | Used to express a typed relationship with another resource, where the relation type is defined by RFC 5988 | Link: ```</feed> ``` ; rel="alternate"[36]
Location | Used in redirection, or when a new resource has been created. | Location: http://www.w3.org/pub/WWW/People.html
P3P | This field is supposed to set P3P policy, in the form of P3P:CP="your_compact_policy". However, P3P did not take off,[37]most browsers have never fully implemented it, a lot of websites set this field with fake policy text, that was enough to fool browsers the existence of P3P policy and grant permissions for third party cookies. | P3P: CP="This is not a P3P policy! See http://www.google.com/support/accounts/bin/answer.py?hl=en&answer=151657 for more info."
Pragma | Implementation-specific fields that may have various effects anywhere along the request-response chain. | Pragma: no-cache
Proxy-Authenticate | Request authentication to access the proxy. | Proxy-Authenticate: Basic
Public-Key-Pins[38] | HTTP Public Key Pinning, announces hash of website's authentic TLS certificate | Public-Key-Pins: max-age=2592000; pin-sha256="E9CZ9INDbd+2eRQozYqqbQ2yXLVKB9+xcprMF+44U1g=";
Retry-After | If an entity is temporarily unavailable, this instructs the client to try again later. Value could be a specified period of time (in seconds) or a HTTP-date.[39] | Example 1: Retry-After: 120 Example 2: Retry-After: Fri, 07 Nov 2014 23:59:59 GMT
Server | A name for the server | Server: Apache/2.4.1 (Unix)
Set-Cookie | An HTTP cookie | Set-Cookie: UserID=JohnDoe; Max-Age=3600; Version=1
Strict-Transport-Security | A HSTS Policy informing the HTTP client how long to cache the HTTPS only policy and whether this applies to subdomains. | Strict-Transport-Security: max-age=16070400; includeSubDomains
Trailer | The Trailer general field value indicates that the given set of header fields is present in the trailer of a message encoded with chunked transfer coding. | Trailer: Max-Forwards
Transfer-Encoding | The form of encoding used to safely transfer the entity to the user. Currently defined methods are: chunked, compress, deflate, gzip, identity. | Transfer-Encoding: chunked
TSV | "Tracking Status Value, value suggested to be sent in response to a DNT(do-not-track), possible values:""!"" — under construction
""?"" — dynamic
""G"" — gateway to multiple parties
""N"" — not tracking
""T"" — tracking
""C"" — tracking with consent
""P"" — tracking only if consented
""D"" — disregarding DNT
""U"" — updated" | TSV: ?
Upgrade | Ask the client to upgrade to another protocol. | Upgrade: HTTP/2.0, HTTPS/1.3, IRC/6.9, RTA/x11, websocket
Vary | Tells downstream proxies how to match future request headers to decide whether the cached response can be used rather than requesting a fresh one from the origin server. | Example 1: Vary: * Example 2: Vary: Accept-Language
Via | Informs the client of proxies through which the response was sent. | Via: 1.0 fred, 1.1 example.com (Apache/1.1)
Warning | A general warning about possible problems with the entity body. | Warning: 199 Miscellaneous warning
WWW-Authenticate | Indicates the authentication scheme that should be used to access the requested entity. | WWW-Authenticate: Basic

### De facto Request Headers

Name | Description | Values/Example
-------|------------------------------------------------------------------------------|--------
X-Forwarded-For | a de facto standard for identifying the originating IP address of a client connecting to a web server through an HTTP proxy or load balancer | X-Forwarded-For: client1, proxy1, proxy2X-Forwarded-For: 129.78.138.66, 129.78.64.103
X-Forwarded-Host | a de facto standard for identifying the original host requested by the client in the Host HTTP request header, since the host name and/or port of the reverse proxy (load balancer) may differ from the origin server handling the request. | X-Forwarded-Host: en.wikipedia.org:8080X-Forwarded-Host: en.wikipedia.org
X-Forwarded-Proto | a de facto standard for identifying the originating protocol of an HTTP request, since a reverse proxy (or a load balancer) may communicate with a web server using HTTP even if the request to the reverse proxy is HTTPS. An alternative form of the header (X-ProxyUser-Ip) is used by Google clients talking to Google servers. | X-Forwarded-Proto: https

### De facto Response Headers

Name | Description | Values/Example
---------------|-------------------------------------------------------------------------|--------
X-RateLimit-Limit | The limit that you cannot surpass in a given amount of time | 5000
X-RateLimit-Remaining | The number of calls you have available until a given reset time stamp, or calculated given some sort of sliding time window. | 2385
X-RateLimit-Reset | The timestamp in UTC formatted to HTTP spec per RFC 1123 for when the limits will be reset. | 1372700873



* Dow Jones Custom Headers

* Caching

    Cache-Control header was defined as part of the HTTP/1.1 specification and is  used to define response caching policies. All modern browsers support Cache-Control.

    Cache policy decision tree
  
    [ there's an image here ]

      Cache-Control: public, max-age=600

      A response with the above Cache-Control  means that the response:

        * is cacheable
        * is cacheable for 10 mins

      Cache-Control: no-store

      A response with the above Cache-Control  means that the response:

        * is not cacheable
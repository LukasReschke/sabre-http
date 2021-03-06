ChangeLog
=========

2.1.0 (2014-??-??)
------------------

* Added: `URLUtil::resolve()` to make resolving relative urls super easy.
* #12: Circumventing CURL's FOLLOW_LOCATION and doing it in PHP instead. This
  fixes compatibility issues with people that have open_basedir turned on.
* Added: Content negotiation now correctly support mime-type parameters such as
  charset.
* Changed: `Util::negotiate()` is now deprecated. Use
  `Util::negotiateContentType()` instead.


2.0.4 (2014-07-14)
------------------

* Changed: No longer escaping @ in urls when it's not needed.
* Fixed: #7: Client now correctly deals with responses without a body.


2.0.3 (2014-04-17)
------------------

* Now works on hhvm!
* Fixed: Now throwing an error when a Request object is being created with
  arguments that were valid for sabre/http 1.0. Hopefully this will aid with
  debugging for upgraders.


2.0.2 (2014-02-09)
------------------

* Fixed: Potential security problem in the client.


2.0.1 (2014-01-09)
------------------

* Fixed: getBodyAsString on an empty body now works.
* Fixed: Version string


2.0.0 (2014-01-08)
------------------

* Removed: Request::createFromPHPRequest. This is now handled by
  Sapi::getRequest.


2.0.0alpha6 (2014-01-03)
------------------------

* Added: Asynchronous HTTP client. See examples/asyncclient.php.
* Fixed: Issue #4: Don't escape colon (:) when it's not needed.
* Fixed: Fixed a bug in the content negotation script.
* Fixed: Fallback for when CURLOPT_POSTREDIR is not defined (mainly for hhvm).
* Added: The Request and Response object now have a `__toString()` method that
  serializes the objects into a standard HTTP message. This is mainly for
  debugging purposes.
* Changed: Added Response::getStatusText(). This method returns the
  human-readable HTTP status message. This part has been removed from
  Response::getStatus(), which now always returns just the status code as an
  int.
* Changed: Response::send() is now Sapi::sendResponse($response).
* Changed: Request::createFromPHPRequest is now Sapi::getRequest().
* Changed: Message::getBodyAsStream and Message::getBodyAsString were added. The
  existing Message::getBody changed it's behavior, so be careful.


2.0.0alpha5 (2013-11-07)
------------------------

* Added: HTTP Status 451 Unavailable For Legal Reasons. Fight government
  censorship!
* Added: Ability to catch and retry http requests in the client when a curl
  error occurs.
* Changed: Request::getPath does not return the query part of the url, so
  everything after the ? is stripped.
* Added: a reverse proxy example.


2.0.0alpha4 (2013-08-07)
------------------------

* Fixed: Doing a GET request with the client uses the last used HTTP method
  instead.
* Added: HttpException
* Added: The Client class can now automatically emit exceptions when HTTP errors
  occurred.


2.0.0alpha3 (2013-07-24)
------------------------

* Changed: Now depends on sabre/event package.
* Changed: setHeaders() now overwrites any existing http headers.
* Added: getQueryParameters to RequestInterface.
* Added: Util::negotiate.
* Added: RequestDecorator, ResponseDecorator.
* Added: A very simple HTTP client.
* Added: addHeaders() to append a list of new headers.
* Fixed: Not erroring on unknown HTTP status codes.
* Fixed: Throwing exceptions on invalid HTTP status codes (not 3 digits).
* Fixed: Much better README.md
* Changed: getBody() now uses a bitfield to specify what type to return.


2.0.0alpha2 (2013-07-02)
------------------------

* Added: Digest & AWS Authentication.
* Added: Message::getHttpVersion and Message::setHttpVersion.
* Added: Request::setRawServerArray, getRawServerValue.
* Added: Request::createFromPHPRequest
* Added: Response::send
* Added: Request::getQueryParameters
* Added: Utility for dealing with HTTP dates.
* Added: Request::setPostData and Request::getPostData.
* Added: Request::setAbsoluteUrl and Request::getAbsoluteUrl.
* Added: URLUtil, methods for calculation relative and base urls.
* Removed: Response::sendBody


2.0.0alpha1 (2012-10-07)
------------------------

* Fixed: Lots of small naming improvements
* Added: Introduction of Message, MessageInterface, Response, ResponseInterface.

Before 2.0.0, this package was built-into SabreDAV, where it first appeared in
January 2009.

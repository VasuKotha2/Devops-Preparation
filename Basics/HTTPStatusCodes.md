1xx: Information
----------------
* 100 Continue:
---------------
The server has received the request headers, and the client should proceed to send the request body
* 101 Switching Protocols:
--------------------------
The requester has asked the server to switch protocols
* 103 Early Hints:
------------------
Used with the Link header to allow the browser to start preloading resources while the server prepares a response

2xx: Successful
---------------
* 200 OK: 
---------
The request is OK (this is the standard response for successful HTTP requests)
* 201 Created:
--------------
The request has been fulfilled, and a new resource is created 
* 202 Accepted:
---------------
The request has been accepted for processing, but the processing has not been completed
* 203 Non-Authoritative Information:
------------------------------------
The request has been successfully processed, but is returning information that may be from another source
* 204 No Content:
-----------------
The request has been successfully processed, but is not returning any content
* 205 Reset Content:
--------------------
The request has been successfully processed, but is not returning any content, and requires that the requester reset the document view
* 206 Partial Content:
----------------------
The server is delivering only part of the resource due to a range header sent by the client
3xx: Redirection:
-----------------
* 300 Multiple Choices:
-----------------------
A link list. The user can select a link and go to that location. Maximum five addresses  
* 301 Moved Permanently:
------------------------
The requested page has moved to a new URL 
* 302 Found:
------------
The requested page has moved temporarily to a new URL
* 303 See Other:
----------------
The requested page can be found under a different URL
* 304 Not Modified:
-------------------
Indicates the requested page has not been modified since last requested
* 307 Temporary Redirect:
-------------------------
The requested page has moved temporarily to a new URL
* 308 Permanent Redirect:
-------------------------
The requested page has moved permanently to a new URL
4xx: Client Error:
------------------
* 400 Bad Request:
------------------
The request cannot be fulfilled due to bad syntax
* 402 Payment Required:
-----------------------
Reserved for future use
* 403 Forbidden:
----------------
The request was a legal request, but the server is refusing to respond to it
* 404 Not Found:
----------------
The requested page could not be found but may be available again in the future
* 405 Method Not Allowed:
-------------------------
A request was made of a page using a request method not supported by that page
* 406 Not Acceptable:
---------------------
The server can only generate a response that is not accepted by the client
* 407 Proxy Authentication Required:
------------------------------------
The client must first authenticate itself with the proxy
* 408 Request Timeout:
----------------------
The server timed out waiting for the request
* 409 Conflict:
---------------
The request could not be completed because of a conflict in the request
* 410 Gone:
-----------
The requested page is no longer available
* 411 Length Required:
----------------------
The "Content-Length" is not defined. The server will not accept the request without it
* 412 Precondition Failed:
--------------------------
The precondition given in the request evaluated to false by the server
* 413 Request Too Large:
------------------------
The server will not accept the request, because the request entity is too large


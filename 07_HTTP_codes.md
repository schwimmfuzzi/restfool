# HTTP Codes

The problem with http codes is, that there are lot more then only the two or three commonly used ones like 404, 200 and 500. I have seen apis and projects working on these codes only, implementing custom response handling, departing from their own handling all over the whole project.

If http codes are implemented properly, things get a lot more comfortable. I take you on a small trip which codes are necessary, which are useful and where they should be used.

## 1xx Codes
Never used one of these in any of my applications / apis. There is one I would like to mention. Generally the 1xx section is used for information about a request during the call itself.
### 102 Processing
Should be used if the you do not want to have a timeout in the request, but the processing needs very long time.


## 2xx Success
Telling the client that request is processed properly and results are returned
### 200 OK
Everything went fine, checkout response body to see what you got.
### 204 No Content
Request was successful but the response does NOT have a body (on purpose).
### 206 Partial Content
Useful if you are sending large content, e.g. video or something that loads in chunks.


## Redirections
Some useful codes if your resource can be found somewhere else (even in clients cache)
### 301 Moved Permanently
Resource is permanently moved to another location. Typically contains a `Location` header that indicates the new URL to the resource. Client should not come back here.
### 302 Found (Moved Temporarily)
Resource is temporarily moved to another location. Typically contains a `Location` header that indicates the new URL to the resource.
### 304 Not Modified
Resource is not modified, compared to an old response. Never use this one on idempotent requests! Check out the chapter about [idempotency](./08_idempotency_concurrency.md)
### 307 Temporary Redirect
Used for the same reason as 302, but ensures the client that the same method and body will be used to perform the request.
### 308 Permanent Redirect
Used for the same reason as 301, but ensures the client that the same method and body will be used to perform the request.



## Client Errors
Let the client know that the sent request was not correct. Not being correct can mean a lot of things...
### 400 Bad Request
General error message for a request that is syntactically not correct. This is by far the most miss-used code the world has ever seen. Its not the `swiss-army-knife-code-for-everything-that-did-not-work`!
### 401 Unauthorized
Request is not authenticated and tries to access a secured resource or method.
### 403 Forbidden
If you want to let the client know, that this resource is there but it does not have sufficient permissions to perform that method on this resource.
### 404 Not Found
When a resource is not found. I guess you know this one pretty well. I tend to use this only if I have an authenticated request. For anonymous requests I like to hide any information an possible attacker is able to use against or crawl you.
### 405 Method not Allowed
When a method, maybe POST an a resource is called that does exist (the method, not the resource).
### 412 Precondition Failed
If something else must have happened before this request can be completed successfully, e.g. another transaction.
### 413 Entity Too Large
The sent payload is too large. Could be used when receiving an image via POST that is larger (in meaning of data volume, not pixels...) then defined.
### 415 Unsupported Media Type
When you try to request (receive or send) a content type that is not offered by the api, like you want to post xml content to an api that only consumes json.
### 422 Unprocessable Entity
The request itself was formatted correctly but something with the entity is not working properly. Can be used to identify invalid content in a body for instance.
### 429 Too Many Requests
Typically used when you throttle your api to let clients perform only a specific amount of requests in a time frame.


## Server Errors
These types mean that something broke on servers side - you do not want your users to see these frequently. But DO NOT USE 4xx for these. Clients need to know if their requests was correct.
### 500 Internal Server Error
Maybe some uncaught exception....
### 502 Bad Gateway
Well, never need to use this before, but it can identify problems with apis (servers) upstream, e.g. a further request could not have been performed and api informs client about this situation.
### 503 Service Unavailable
Let the clients know that this resource is currently not alive (overload, booting, etc.) but add a `retry-after` header (with sufficiently high random time frames)
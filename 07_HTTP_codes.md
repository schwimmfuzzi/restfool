# HTTP Codes

The problem with http codes is, that there are lot more then only the two or three commonly used ones like 404, 200 and 500. I have seen apis and projects working on these codes only, implementing custom response handling, departing from their own handling all over the whole project.

If http codes are implemented properly, things get a lot more comfortable. I take you on a small trip which codes are necessary, which are useful and where they should be used.

## 1xx Codes
Never used one of these in any of my applications / apis. There is one I would like to mention. Generally the 1xx section is used for information about a request during the call itself.

### 102 Processing
Should be used if the you do not want to have a timeout in the request, but the processing needs very long time.

## 2xx Success
### 200 OK
### 204 No Content
### 206 Partial Content


## Redirection
### 301 Moved Permanently
### 302 Found (Moved Temporarily)
### 304 Not Modified
### 307 Temporary Redirect
### 308 Permanent Redirect


## Client Error
### 400 Bad Request
### 401 Unauthorized
### 403 Forbidden
### 404 Not Found
### 405 Method not Allowed
### 412 Precondition Failed
### 413 Entity Too Large
### 415 Unsupported Media Type
### 416 Range not Satisfiable
### 422 Unprocessable Entity
### 429 Too Many Requests


## Server Error
### 500 Internal Server Error
### 502 Bad Gateway
### 503 Service Unavailable

# Errors



The Ulaap API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- The request could not be understood by the server.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- The server understood the request, but table doesn't exist or permission doesn't exist for it.
404 | Not Found -- The server has not found anything matching the request.
406 | Not Acceptable -- You requested a format that isn't json.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.

<aside class="notice">Most requests will have a message with it explaining what has happened or why something didn't work.'  </aside>


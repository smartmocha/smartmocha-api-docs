# Errors

The Smart Mocha API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Something is wrong with your request, perhaps a header or missing parameter.
401 | Unauthorized -- Your API key is wrong or expired
403 | Forbidden -- You don't have access to the requested resource
404 | Not Found -- The specified resource or endpoint could not be found
405 | Method Not Allowed -- You tried to access a resource with an invalid method
406 | Not Acceptable -- You requested a format that isn't json
429 | Too Many Requests -- You've hit a rate limit.
500 | Internal Server Error -- We goofed somewhere, and the server monkeys will tell us. On it!
503 | Service Unavailable -- We're offline, this shouldn't happen. Please check status.smartmocha.com

# Errors

The Connect API uses the following error codes:

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is not formatted correctly.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- The API you are trying to access is not available with the current API key.
404 | Not Found -- The specified entity could not be found.
422 | Validation  Error -- One or more values in the request are not valid.
406 | Not Acceptable -- You requested a format that isn't json.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.

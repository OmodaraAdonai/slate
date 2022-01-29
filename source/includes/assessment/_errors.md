# Errors

Successful requests should generate a response with a 200-level status code. Unsuccessful requests should generate a response with one of the following responses:

Status Code | Description
-------------- | --------------
401 | Unsuccessful authentication with the provided API key.
404 | The requested resource could not be found.

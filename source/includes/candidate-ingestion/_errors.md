# Errors

```json
{
	"errors": [
		{
			"message": "Your request included invalid JSON.",
			"field": "email"
		}
	]
}
```

Successful API responses will have a 200-level HTTP status code. If there is a problem processing your request, you will receive a response with a 4xx- or 5xx-level status code as follows:

Status Code  | Description 
-------------- | -------------- 
400 | Your request included invalid JSON.
401 | You have not been authenticated.
403 | You have been authenticated, but your Greenhouse user does not have permission to the resource.
404 | The resource you requested could not be found.
5xx | There was an error on our end. You may retry at a later time or contact support if the problem persists.

### Error Properties

Property Name  | Type | Required | Description
-------------- | -------------- | --------------  | -------------- 
errors[] | Array | | Yes | 
errors.message | String | Yes | A message describing the error. This is for debugging purposes and is not intended to be displayed to the end-user. The exact text should not be relied on programmatically. 
errors.field | String | No | The offending field in the request that caused the error, if applicable.

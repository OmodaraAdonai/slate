# Response Error 

When Greenhouse receives a malformed response for any of Assessment Partner's API endpoints, we would like to report the errors to the Assessment Partner. As such, each Assessment Partner should provide an API endpoint to ingest this information.

`POST https://www.testing-partner.com/api/request_errors`

### Request


```shell
curl -X POST 'https://www.testing-partner.com/api/request_errors'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
{
	"api_call": "test_status",
	"errors": ["partner_status is 'complete' but partner_profile url is missing"],
	"partner_test_id" : "12345",
	"partner_test_name": "Personality Test",
	"partner_interview_id": "299506",
	"candidate_email": "hpotter@hogwarts.edu"
}
```

After receiving a malformed response, Greenhouse will provide the Assessment Partner with the details of the failed response. Each time an invalid response arrives, Greenhouse will send a POST request to the `response_error` API endpoint.

The body of the request will contain as much information as Greenhouse has at the moment of failure. 

For example, if a `list_tests` request fails, Greenhouse can only provide the api call (in this case, ‘list_tests’) and the assorted errors (missing keys, unexpected data types, etc.). However, if a `test_status` request fails, we can provide more information (partner_test_id, partner_interview_id, etc.) that may prove useful for debugging purposes. Assessment Partners can always expect to receive `api_call` and `errors` in the JSON body. 

Property Name | Value | Required | Description
-------------- | -------------- | -------------- | --------------
api_call | String | Yes | The name of the API call that generated the malformed response.
errors | Array | Yes | An array of strings which describe an error that prevented the response from validating.
partner_test_id | String | No | Identifies a test available to an organization. Initially provided as a response to the [List Tests request] (#list-tests).
partner_test_name | String | No | A human-readable string that identifies the test. Initially provided as a response to the [List Tests request] (#list-tests).
partner_interview_id | String | No | Identifies a candidate’s test. 
candidate_email | String | No | The candidate’s email address. The test should be sent to this address.

<aside class="notice">
The partner_interview_id should not be confused with partner_test_id. While partner_test_id identifies the test, partner_interview_id identifies an instance of the test that was sent to a candidate.
</aside>

### Response 

> API Response

```json
{
	"status": 200
}
```

The response to a successful `response_errors` request should contain a response code of 200.
<br><br>
# List Tests

Greenhouse will first need to retrieve the list of tests from the Assessment Partner using the `list_tests` API endpoint. We will show the list of available tests to the user, who will to select the appropriate test for a given candidate. 

`GET https://www.testing-partner.com/api/list_tests`

```shell
curl 'https://www.testing-partner.com/api/list_tests'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

### Request

Greenhouse will make a GET request to the `list_tests` endpoint specified by the Assessment Partner.

### Response

> API Response

```json
[
	{
		"partner_test_id": "12345",
		"partner_test_name": "My First Test" 
	},
	{
		"partner_test_id": "54321",
		"partner_test_name": "My Second Test"
	}
]
```


The Assessment Partner’s response should include a JSON payload containing a list of test objects for the organization. Each test object should contain the keys `partner_test_id` and `partner_test_name.`



Property Name | Type | Required | Description
-------------- | -------------- | -------------- | --------------
partner_test_id | String | Yes | Identifies a test available to an organization.
partner_test_name | String | Yes | A descriptive title for the test. We will use this value our UI as the test’s label.

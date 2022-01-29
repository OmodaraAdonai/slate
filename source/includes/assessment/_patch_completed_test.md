# PATCH - Mark Test as Completed

When a candidate completes a test, send this request to the URL sent in the initial Send Test request to signal Greenhouse that the test has been completed. Upon this, Greenhouse will send a request to your Test Status endpoint.

`PATCH https://app.greenhouse.io/integrations/testing_partners/take_home_tests/12345`

### Request

```shell
curl -X PATCH 'https://app.greenhouse.io/integrations/testing_partners/take_home_tests/12345'

-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

No parameters are necessary with this request.

### Response

The response will return only the HTTP status code.
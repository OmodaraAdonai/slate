## Errors and Validation
```graphql
{
  employee(id: 100000000) {
  	email
  }
}
```

```json
{
  "data": {
    "employee": null
  },
  "errors": [
    {
      "message": "Unable to find Employee with id 100000000",
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "employee"
      ],
      "errorCode": "NotFound"
    }
  ]
}
```
Unlike REST APIs, GraphQL will return an HTTP status of 200, even in cases where there are errors.  You can see an
example of an error message to the right.  The `data` and `errors` properties are siblings.  It's possible for a
request to generate a response that has _both_ `data` and `errors`. However, if there is ever an `errors` key in the response,
the request failed (despite the return code of 200).

The `message` will let you know what's wrong.  The `locations` property
has the line number and column where the error starts.  In this example, it's the 2nd line, 3rd column, which
is the start of the word `employee`.  The `fields` property is a breadcrumb trail of how to get to the problem.  Here,
the problem can be found on the top-most `employee` selection.

When we can, we'll also provide an `errorCode` key for every entry in the `errors` list. Here's a table of current errorCodes:

Error Scenario | Error Code |
-------------- | ---------- |
Authentication Failure | Authentication |
Validation Failure | Validation |
Resource Not Found | NotFound |
Server Error | Server |
Rate Limit Exceeded | RateLimit|

There are undefined error scenarios in which we're unable to provide a code. In these cases, refer to the contents
of the error list.
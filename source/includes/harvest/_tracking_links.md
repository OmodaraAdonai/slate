# Tracking Links

Tracking Links are URLs which allow users to track the source and/or referrer of candidates who applied through the link. Greenhouse generates Tracking Links by appending a token to the end of a job post or job boad URL. These tokens represent a combination of source_id and/or referrer_id, and can link back to a job post, job board, or job.

## The tracking link object

```json
{
  "id": 6004841,
  "token": "tnch4u",
  "created_at": "2012-10-07T15:06:35.975Z",
  "updated_at": "2016-09-27T17:52:56.533Z",
  "related_post_id": 1,
  "related_post_type": "SocialMediaPost",
  "job_id": 12314,
  "job_post_id": 124263,
  "job_board": {
    "id": 8578,
    "company_name": "Business Corp",
    "url_token": "businessco"
  },
  "source": {
    "id": 4,
    "public_name": "Twitter"
  },
  "credited_to": {
    "id": 1,
    "first_name": "Some",
    "last_name": "Employee",
    "name": "Some Employee",
    "employee_id": "ABC12345"
  }
}
```

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The tracking link's unique identifier |
| token | The token present in the url |
| related_post_id | If there is an associated social media post, the Greenhouse ID for that post |
| related_post_type | Will be "SocialMediaPost" if the link was posted through the social network sharing feature, otherwise this value will be `null` |
| job_id | The job associated with this tracking link |
| job_post_id | The job post associated with this tracking link |
| job_board | The job board associated with this tracking link |
| source | The source of the job (recruiter, social media site, etc) |
| credited_to | The employee credited with a referral for this tracking link |

## JSON Schema

To view the JSON Schema definition for the Tracking Link object, please [click here](/schemas/tracking_links.json). This will tell you all of the valid types and definitions, as well as expected fields in the response.


## GET: Tracking Link Data for Token

Retrieve the specific tracking link data for the supplied token.

```shell
curl -X GET 'https://harvest.greenhouse.io/v1/tracking_links/{token}'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
{
  "id": 6004841,
  "token": "tnch4u",
  "created_at": "2012-10-07T15:06:35.975Z",
  "updated_at": "2016-09-27T17:52:56.533Z",
  "related_post_id": 1,
  "related_post_type": "SocialMediaPost",
  "job_id": 12314,
  "job_post_id": 124263,
  "job_board": {
    "id": 8578,
    "company_name": "Business Corp",
    "url_token": "businessco"
  },
  "source": {
    "id": 4,
    "public_name": "Twitter"
  },
  "credited_to": {
    "id": 1,
    "first_name": "Some",
    "last_name": "Employee",
    "name": "Some Employee",
    "employee_id": "ABC12345"
  }
}
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/tracking_links/{token}`

### URL Parameters

Parameter | Description
--------- | -----------
token | The token you want to retrieve the data for

<br>

[See noteworthy response attributes.](#the-tracking-link-object)

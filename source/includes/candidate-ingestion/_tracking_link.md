# Tracking Link

## Post Tracking Link

```shell
curl -X POST 'https://api.greenhouse.io/v1/partner/tracking_link'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
-H "Content-Type: application/json"
```

```json
{
	"job_id": 12345
}
```

> API Response

```json
{ 
	"tracking_link": "http://grnh.se/yvj0bj",
	"job": "Auror", 
	"source": "Campus Recruiting",
	"referrer": "Hermione Granger"
}
```

Create a new tracking link for a specific job. Candidates that apply using this tracking link will automatically have their source set to your application and their referrer set to the current user.


`POST https://api.greenhouse.io/v1/partner/tracking_link`


### Request Parameters


Property Name | Type | Required
-------------- | -------------- | -------------- 
job_id | Integer | Yes


### Response Parameters


Property Name | Type            | Description
-------------- | -------------- | --------------
tracking_link  | String         | URL for newly created tracking link.
job            | String         | The name of the job tied to this tracking link.
source         | String         | The name of the source tied to this tracking link (e.g. the name of your application).
referrer       | String         | The name of the user tied to this tracking link.
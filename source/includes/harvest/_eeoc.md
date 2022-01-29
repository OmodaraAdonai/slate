# EEOC

## The EEOC object

Every application may have zero or one EEOC object.

```json
{
  "application_id": 286,
  "candidate_id": 406,
  "race": {
    "id": 7,
    "description": "Two or More Races"
  },
  "gender": {
    "id": 1,
    "description": "Male"
  },
  "veteran_status": {
    "id": 3,
    "message": "I don't wish to answer"
  },
  "disability_status": {
    "id": 1,
    "description": "Yes, I have a disability, or have a history/record of having a disability"
  },
  "submitted_at": "2017-01-29T15:09:46.806Z"
}
```

### Noteworthy attributes
| Attribute | Description |
|-----------|-------------|
| application_id | Application ID |
| candidate_id | The ID of the [candidate](#candidates) who is applying for the job associated with this application.
|race|See the EEOC Reference below
|gender|See the EEOC Reference below
|veteran_status|See the EEOC Reference below
|disability_status|See the EEOC Reference below
|submitted_at| The timestamp in [ISO-8601] (#general-considerations) at which the EEOC data was submitted.



### EEOC Reference

### Race

| description |
|------|
|American Indian or Alaskan Native
|Asian
|Black or African American
|Hispanic or Latino
|White
|Native Hawaiian or Other Pacific Islander
|Two or More Races
|Decline To Self Identify

### Gender
| description |
|-----------|
|Male
|Female
|Decline To Self Identify

### Veteran Status
| description |
|-----------|
|I am not a protected veteran
|I identify as one or more of the classifications of a protected veteran
|I don't wish to answer

### Disability Status
| description |
|-----------|
|Yes, I have a disability, or have a history/record of having a disability
|No, I don’t have a disability, or a history/record of having a disability
|I don't wish to answer

## GET: List EEOC

```shell
curl 'https://harvest.greenhouse.io/v1/eeoc'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```
> The above command returns JSON structured like this:

```json
[
  {
    "application_id": 286,
    "candidate_id": 406,
    "race": {
      "id": 7,
      "description": "Two or More Races"
    },
    "gender": {
      "id": 1,
      "description": "Male"
    },
    "veteran_status": {
      "id": 3,
      "message": "I don't wish to answer"
    },
    "disability_status": {
      "id": 1,
      "description": "Yes, I have a disability, or have a history/record of having a disability"
    },
    "submitted_at": "2017-01-29T15:09:46.806Z"
  },
  {
    "application_id": 287,
    "candidate_id": 342,
    "race": {
      "id": 7,
      "description": "Two or More Races"
    },
    "gender": {
      "id": 2,
      "description": "Female"
    },
    "veteran_status": null,
    "disability_status": {
      "id": 1,
      "description": "Yes, I have a disability, or have a history/record of having a disability"
    },
    "submitted_at": "2017-01-30T17:10:32.432Z"
  }
]
```

List all of an organization's EEOC data.

### HTTP Request
`GET https://harvest.greenhouse.io/v1/eeoc`

### Query string parameters
Parameter | Description
--------- | -----------
*per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.
*submitted_before | Return only EEOC data submitted before this timestamp. Timestamp must be in [ISO-8601] (#general-considerations) format.
*submitted_after | Return only EEOC data submitted at or after this timestamp. Timestamp must be in [ISO-8601] (#general-considerations) format.

This endpoint supports pagination. See the [Pagination](#pagination) section for more detail.

## GET: Retrieve EEOC Data for Application

```shell
curl 'https://harvest.greenhouse.io/v1/applications/{id}/eeoc'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```
> The above command returns JSON structured like this:

```json
{
  "application_id": 286,
  "candidate_id": 406,
  "race": {
    "id": 7,
    "description": "Two or More Races"
  },
  "gender": {
    "id": 1,
    "description": "Male"
  },
  "veteran_status": {
    "id": 3,
    "message": "I don't wish to answer"
  },
  "disability_status": {
    "id": 1,
    "description": "Yes, I have a disability, or have a history/record of having a disability"
  },
  "submitted_at": "2017-01-29T15:09:46.806Z"
}
```

Retrieve an application's EEOC data by an application ID.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/applications/{id}/eeoc`

### URL Parameters

Parameter | Description
--------- | -----------
id | ID of the application whose EEOC data you want to retrieve.

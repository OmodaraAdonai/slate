# Educations
This is a list of endpoints which can be used to populate Education data for candidate applications. Instructions for posting applications that include Education information can be found under [Applications](#submit-an-application).

## List Degrees
```json
{
  "items": [
    {
      "id": 5494452,
      "text": "High School"
    },
    {
      "id": 5494478,
      "text": "Associate's Degree"
    },
    {
      "id": 5494516,
      "text": "Bachelor's Degree"
    },
    {
      "id": 5494551,
      "text": "Master's Degree"
    },
    {
      "id": 5494580,
      "text": "Master of Business Administration (M.B.A.)"
    },
    {
      "id": 5494607,
      "text": "Juris Doctor (J.D.)"
    },
    {
      "id": 5494638,
      "text": "Doctor of Medicine (M.D.)"
    },
    {
      "id": 5494662,
      "text": "Doctor of Philosophy (Ph.D.)"
    },
    {
      "id": 5494689,
      "text": "Engineer's Degree"
    },
    {
      "id": 5494710,
      "text": "Other"
    }
  ],
  "meta": {
    "total_count": 10,
    "per_page": 100
  }
}

```

Returns a list of all of your organization's degrees.

### HTTP Request

`GET https://boards-api.greenhouse.io/v1/boards/{board_token}/education/degrees`

### URL Parameters

Parameter | Description
--------- | -----------
board_token | Job Board URL token

### Querystring Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
term | No | string | Returns any degrees containing this string in their name.
page | No | string | A cursor for use in pagination. Returns the n-th chunk of objects (100 per page).

## List Disciplines
```json
{
  "items": [
    {
      "id": 5494865,
      "text": "Accounting"
    },
    {
      "id": 5494892,
      "text": "African Studies"
    },
    {
      "id": 5494917,
      "text": "Agriculture"
    },
    {
      "id": 5494940,
      "text": "Anthropology"
    },
    {
      "id": 5494964,
      "text": "Applied Health Services"
    },
    {
      "id": 5495009,
      "text": "Architecture"
    },
    {
      "id": 5495033,
      "text": "Art"
    },
    {
      "id": 5495051,
      "text": "Asian Studies"
    },
    {
      "id": 5495074,
      "text": "Biology"
    },
    {
      "id": 5495101,
      "text": "Business"
    }
  ],
  "meta": {
    "total_count": 71,
    "per_page": 100
  }
}
```

Returns a list of all of your organization's disciplines.

### HTTP Request

`GET https://boards-api.greenhouse.io/v1/boards/{board_token}/education/disciplines`

### URL Parameters

Parameter | Description
--------- | -----------
board_token | Job Board URL token

### Querystring Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
term | No | string | Returns any disciplines containing this string in their name.
page | No | string | A cursor for use in pagination. Returns the n-th chunk of objects (100 per page).


## List Schools


```json
{
  "items": [
    {
      "id": 5417077,
      "text": "Abraham Baldwin Agricultural College"
    },
    {
      "id": 5417117,
      "text": "Academy of Art University"
    },
    {
      "id": 5417156,
      "text": "Acadia University"
    },
    {
      "id": 5417194,
      "text": "Adams State University"
    },
    {
      "id": 5417217,
      "text": "Adelphi University"
    },
    {
      "id": 5417245,
      "text": "Adrian College"
    },
    {
      "id": 5417295,
      "text": "Adventist University of Health Sciences"
    },
    {
      "id": 5417331,
      "text": "Agnes Scott College"
    },
    {
      "id": 5417366,
      "text": "AIB College of Business"
    },
    {
      "id": 5417384,
      "text": "Alaska Pacific University"
    }
  ],
  "meta": {
    "total_count": 2464,
    "per_page": 100
  }
}
```

Returns a list of all of your organization's schools.

### HTTP Request

`GET https://boards-api.greenhouse.io/v1/boards/{board_token}/education/schools`

### URL Parameters

Parameter | Description
--------- | -----------
board_token | Job Board URL token

### Querystring Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
term | No | string | Returns any schools containing this string in their name.
page | No | string | A cursor for use in pagination. Returns the n-th chunk of objects (100 per page).


# Demographic Data

Demographic questions and answers submitted during the application process. For more information on Greenhouse Inclusion, please visit [https://www.greenhouse.io/inclusion](https://www.greenhouse.io/inclusion).


## The Demographic Question Set object

```json
{
  "id": 1991,
  "title": "Question Set",
  "description": "<p>Questions for candidates</p>",
  "active": true
}
```

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The demographic question set's unique identifier |
| title | The title of the demographic question set
| description | The demographic question set's description.  This is a rich text field which may contain HTML.
| active | If `false`, the demographic question set has been deleted.

## The Demographic Question object

```json
{
  "id": 123,
  "active": true,
  "demographic_question_set_id": 456,
  "name": "What is your favorite color?",
  "translations": [
    {
      "language": "en",
      "name": "What is your favorite color?"
    }
  ],
  "required": true,
  "answer_type": "multi_value_multi_select"
}
```

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The demographic question's unique identifier |
| demographic_question_set_id | The demographic question set that this belongs to
| name | The question text
| translations.language | Translations have been deprecated but are kept for backwards compatibility. Only `en` (English) is supported at this time.
| translations.name | Translations have been deprecated but are kept for backwards compatibility. This value will be the same as `name` above.
| active | If `false`, the question has been deleted.
| required | If `true`, the question must be filled out by the applicant.
| answer_type | The type of answer that can be provided for the question. Value will be either `multi_value_single_select` or `multi_value_multi_select`.

## The Demographic Answer Option object

```json
{
  "id": 456,
  "free_form": false,
  "active": true,
  "name": "Blue",
  "demographic_question_id": 123,
  "translations": [
    {
      "language": "en",
      "name": "Blue"
    }
  ]
}
```

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The demographic answer option's unique identifier |
| name | The answer option text
| translations.language | Translations have been deprecated but are kept for backwards compatibility.  Only `en` (English) is supported at this time.
| translations.name | Translations have been deprecated but are kept for backwards compatibility. This value will be the same as `name` above.
| active | If `false`, the answer option has been deleted.
| free_form | If `true`, the answer option allows free-form user input.
| demographic_question_id | The demographic question for which the answer option belongs to.

## The Demographic Answer object

```json
{
  "id": 51,
  "free_form_text": "12am",
  "application_id": 107594341,
  "demographic_question_id": 25,
  "demographic_answer_option_id": 106,
  "created_at": "2019-04-29T18:46:03.707Z",
  "updated_at": "2019-04-29T18:46:03.707Z"
}
```

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The demographic answer's unique identifier |
| free_form_text | If the selected answer option is free-form, this is the value given by the user.  Otherwise `null`.
| application_id | The application for which the demographic question was answered
| demographic_question_id | The demographic question which was answered.
| demographic_answer_option_id | The demographic answer option which was selected.

## GET: List Demographic Question Sets

List all of an organization's demographic question sets.

```shell
curl 'https://harvest.greenhouse.io/v1/demographics/question_sets'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1991,
    "title": "Question Set A",
    "description": "<p>Questions for US candidates</p>",
    "active": true
  },
  {
    "id": 1992,
    "title": "Question Set B",
    "description": "<p>Questions for European candidates</p>",
    "active": true
  }
]
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/demographics/question_sets`

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
| *per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.

<br>
[See noteworthy response attributes.](#the-demographic-question-set-object)

This endpoint supports pagination. See the [Pagination](#pagination) section for more detail.

## GET: Retrieve Demographic Question Set

Retrieve a demographic question set by its `id`.

```shell
curl 'https://harvest.greenhouse.io/v1/demographics/question_sets/{id}'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1991,
  "title": "Question Set",
  "description": "<p>Questions for candidates</p>",
  "active": true
}
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/demographics/question_sets/{id}`


### URL Parameters

Parameter | Description
--------- | -----------
id | ID of the demographic question set you want to retrieve.

<br>
[See noteworthy response attributes.](#the-demographic-question-set-object)


## GET: List Demographic Questions

List all of an organization's demographic questions.

```shell
curl 'https://harvest.greenhouse.io/v1/demographics/questions'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 123,
    "active": true,
    "demographic_question_set_id": 456,

    "name": "What is your favorite color?",
    "translations": [
      {
        "language": "en",
        "name": "What is your favorite color?"
      }
    ],
    "required": true
  },
  {
    "id": 897,
    "active": true,
    "demographic_question_set_id": 555,
    "name": "Pizza or pasta?",
    "translations": [
      {
        "language": "en",
        "name": "Pizza or pasta?"
      }
    ],
    "required": false
  }
]
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/demographics/questions`

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
| *per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.

<br>
[See noteworthy response attributes.](#the-demographic-question-object)

This endpoint supports pagination. See the [Pagination](#pagination) section for more detail.

## GET: List Demographic Questions For Demographic Question Set

List all of the demographic questions for a demographic question set.

```shell
curl 'https://harvest.greenhouse.io/v1/demographics/question_sets/{id}/questions'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 123,
    "active": true,
    "demographic_question_set_id": 456,
    "name": "What is your favorite color?",
    "translations": [
      {
        "language": "en",
        "name": "What is your favorite color?"
      }
    ],
    "required": true
  },
  {
    "id": 897,
    "active": true,
    "demographic_question_set_id": 555,
    "name": "Pizza or pasta?",
    "translations": [
      {
        "language": "en",
        "name": "Pizza or pasta?"
      }
    ],
    "required": false
  }
]
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/demographics/question_sets/{id}/questions`


### URL Parameters

Parameter | Description
--------- | -----------
id | ID of the demographic question set for which you want to retrieve demographic questions

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
| *per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.

<br>
[See noteworthy response attributes.](#the-demographic-question-object)

This endpoint supports pagination. See the [Pagination](#pagination) section for more detail.

## GET: Retrieve Demographic Question

Retrieve a demographic question by its `id`.

```shell
curl 'https://harvest.greenhouse.io/v1/demographics/questions/{id}'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
{
  "id": 123,
  "active": true,
  "demographic_question_set_id": 456,
  "name": "What is your favorite color?",
  "translations": [
    {
      "language": "en",
      "name": "What is your favorite color?"
    }
  ],
  "required": true
}
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/demographics/questions/{id}`


### URL Parameters

Parameter | Description
--------- | -----------
id | ID of the demographic question you want to retrieve.

<br>
[See noteworthy response attributes.](#the-demographic-question-object)


## GET: List Demographic Answer Options

List all of an organization's demographic answer options.

```shell
curl 'https://harvest.greenhouse.io/v1/demographics/answer_options'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 456,
    "free_form": false,
    "active": true,
    "name": "Blue",
    "demographic_question_id": 123,
    "translations": [
      {
        "language": "en",
        "name": "Blue"
      }
    ]
  },
  {
    "id": 789,
    "free_form": true,
    "active": true,
    "name": "Other",
    "demographic_question_id": 123,
    "translations": [
      {
        "language": "en",
        "name": "Other"
      }
    ]
  }
]
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/demographics/answer_options`

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
| *per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.

<br>
[See noteworthy response attributes.](#the-demographic-answer-option-object)

This endpoint supports pagination. See the [Pagination](#pagination) section for more detail.

## GET: List Demographic Answer Options For Demographic Question

List all of the demographic answer options for a demographic question.

```shell
curl 'https://harvest.greenhouse.io/v1/demographics/questions/{id}/answer_options'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 456,
    "free_form": false,
    "active": true,
    "name": "Blue",
    "demographic_question_id": 123,
    "translations": [
      {
        "language": "en",
        "name": "Blue"
      }
    ]
  },
  {
    "id": 789,
    "free_form": true,
    "active": true,
    "name": "Other",
    "demographic_question_id": 123,
    "translations": [
      {
        "language": "en",
        "name": "Other"
      }
    ]
  }
]
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/demographics/questions/{id}/answer_options`


### URL Parameters

Parameter | Description
--------- | -----------
id | ID of the demographic question for which you want to retrieve demographic answer options.

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
| *per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.

<br>
[See noteworthy response attributes.](#the-demographic-answer-option-object)

This endpoint supports pagination. See the [Pagination](#pagination) section for more detail.

## GET: Retrieve Demographic Answer Option

Retrieve a demographic answer option by its `id`.

```shell
curl 'https://harvest.greenhouse.io/v1/demographics/answer_options/{id}'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
{
  "id": 456,
  "free_form": false,
  "active": true,
  "name": "Blue",
  "demographic_question_id": 123,
  "translations": [
    {
      "language": "en",
      "name": "Blue"
    }
  ]
}
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/demographics/answer_options/{id}`


### URL Parameters

Parameter | Description
--------- | -----------
id | ID of the demographic answer option you want to retrieve.

<br>
[See noteworthy response attributes.](#the-demographic-answer-option-object)

## GET: List Demographic Answers

List all of an organization's demographic answers.

```shell
curl 'https://harvest.greenhouse.io/v1/demographics/answers'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 123,
    "free_form_text": "12am",
    "application_id": 787,
    "demographic_question_id": 25,
    "demographic_answer_option_id": 106,
    "created_at": "2019-04-29T18:46:03.707Z",
    "updated_at": "2019-04-29T18:46:03.707Z"
  },
  {
    "id": 456,
    "free_form_text": null,
    "application_id": 783,
    "demographic_question_id": 29,
    "demographic_answer_option_id": 109,
    "created_at": "2017-01-29T15:09:46.806Z",
    "updated_at": "2017-01-29T15:09:46.806Z"
  }
]
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/demographics/answers`

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
| *per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.
| *created_before | Return only answers created before this timestamp. Timestamp must be in [ISO-8601] (#general-considerations) format.
| *created_after  | Return only answers created at or after this timestamp. Timestamp must be in [ISO-8601] (#general-considerations) format.
| *updated_before | Return only answers updated before this timestamp. Timestamp must be in [ISO-8601] (#general-considerations) format.
| *updated_after  | Return only answers updated at or after this timestamp. Timestamp must be in [ISO-8601] (#general-considerations) format.

<br>
[See noteworthy response attributes.](#the-demographic-answer-object)

This endpoint supports pagination. See the [Pagination](#pagination) section for more detail.

## GET: List Demographic Answers For Application

List all of the demographic answers for an application.

```shell
curl 'https://harvest.greenhouse.io/v1/applications/{id}/demographics/answers'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 123,
    "free_form_text": "12am",
    "application_id": 787,
    "demographic_question_id": 25,
    "demographic_answer_option_id": 106,
    "created_at": "2019-04-29T18:46:03.707Z",
    "updated_at": "2019-04-29T18:46:03.707Z"
  },
  {
    "id": 456,
    "free_form_text": null,
    "application_id": 787,
    "demographic_question_id": 29,
    "demographic_answer_option_id": 109,
    "created_at": "2017-01-29T15:09:46.806Z",
    "updated_at": "2017-01-29T15:09:46.806Z"
  }
]
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/applications/{id}/demographics/answers`


### URL Parameters

Parameter | Description
--------- | -----------
id | ID of the application for which you want to retrieve demographic answers.

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
| *per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.
| *created_before | Return only answers created before this timestamp. Timestamp must be in [ISO-8601] (#general-considerations) format.
| *created_after  | Return only answers created at or after this timestamp. Timestamp must be in [ISO-8601] (#general-considerations) format.
| *updated_before | Return only answers updated before this timestamp. Timestamp must be in [ISO-8601] (#general-considerations) format.
| *updated_after  | Return only answers updated at or after this timestamp. Timestamp must be in [ISO-8601] (#general-considerations) format.

<br>
[See noteworthy response attributes.](#the-demographic-answer-object)

This endpoint supports pagination. See the [Pagination](#pagination) section for more detail.

## GET: Retrieve Demographic Answer

Retrieve a demographic answer by its `id`.

```shell
curl 'https://harvest.greenhouse.io/v1/demographics/answers/{id}'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
{
  "id": 123,
  "free_form_text": "12am",
  "application_id": 787,
  "demographic_question_id": 25,
  "demographic_answer_option_id": 106,
  "created_at": "2019-04-29T18:46:03.707Z"
}
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/demographics/answers/{id}`


### URL Parameters

Parameter | Description
--------- | -----------
id | ID of the demographic answer you want to retrieve.

<br>
[See noteworthy response attributes.](#the-demographic-answer-object)

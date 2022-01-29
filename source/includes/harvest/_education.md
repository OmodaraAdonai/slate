#Education

These endpoints are used to manage the list of education fields in Greenhouse.

## The education objects

Each of the education objects contain an `id`, `name`, and `priority`. When ordering occurs, the items are organized by their priority number.
```
{
    "id": 1234,
    "name": "Siena College",
    "priority": 1
}
```

## GET: List Degrees

```shell
curl 'https://harvest.greenhouse.io/v1/degrees' 
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```
> The above command returns JSON structured like this:

```json
[
    {
        "id": 123,
        "name": "Bachelor's Degree",
        "priority": 0
    },
    {
        "id": 234,
        "name": "Master's Degree",
        "priority": 1
    }
]
```

List all this organization's degree levels.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/degrees`

This endpoint retrieves all the degree and/or education levels for this organization, sorted by priority.

[See education object.](#the-education-objects)

## GET: List Disciplines

```shell
curl 'https://harvest.greenhouse.io/v1/disciplines' 
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```
> The above command returns JSON structured like this:

```json
[
    {
        "id": 123,
        "name": "Accounting",
        "priority": 0
    },
    {
        "id": 234,
        "name": "Biology",
        "priority": 1
    }
]
```

List all this organization's disciplines.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/disciplines`

This endpoint retrieves all the disciplines for this organization, sorted by priority.

[See education object.](#the-education-objects)

## GET: List Schools

```shell
curl 'https://harvest.greenhouse.io/v1/schools' 
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```
> The above command returns JSON structured like this:

```json
[
    {
        "id": 123,
        "name": "Siena College",
        "priority": 0
    },
    {
        "id": 234,
        "name": "Union College",
        "priority": 1
    }
]
```

List all this organization's schools.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/schools`

This endpoint retrieves all the schools for this organization, sorted by priority.

[See education object.](#the-education-objects)

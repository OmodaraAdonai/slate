# User Permissions

## The job permission object

The user role a user has for a job.

```json
{
  "id": 382934,
  "job_id": 9192,
  "user_role_id": 123
}
```

### Noteworthy Attributes

| Attribute | Description |
|-----------|-------------|
| id | The job permission's unique identifier |
| job_id | The ID of the job the user has permission for|
| user\_role\_id | The ID of the user role the user has for the job|


## GET: List Job Permissions

```shell
curl 'https://harvest.greenhouse.io/v1/users/{id}/permissions/jobs'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
  {
    "id": 7879576,
    "job_id": 80722,
    "user_role_id": 4730
  },
  {
    "id": 7879577,
    "job_id": 83475,
    "user_role_id": 4730
  },
  {
    "id": 7879579,
    "job_id": 146048,
    "user_role_id": 4730
  },
  {
    "id": 7879580,
    "job_id": 87904,
    "user_role_id": 4730
  },
  {
    "id": 7879582,
    "job_id": 116958,
    "user_role_id": 4730
  },
  {
    "id": 7879583,
    "job_id": 82318,
    "user_role_id": 4730
  }
]
```

List the job permissions for a given user.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/users/{id}/permissions/jobs`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the user whose job permissions to retrieve

Note: This endpoint is only intended for use with Job Admin and/or Interviewer users, as these roles are assigned on a per job basis. Users that are Site Admins have permissions on all public jobs and will return an empty array. Basic users cannot be assigned to any jobs and will also return an empty array.

This endpoint supports pagination. See the [Pagination](#pagination) section for more detail.

## DELETE: Remove a Job Permission

```shell
curl -X PUT 'https://harvest.greenhouse.io/v1/users/{id}/permissions/jobs'
-H "Content-Type: application/json"
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command takes a JSON request, structured like this:

```json
{ 
  "job_permission_id": 27207466
}
```

> The above command returns a JSON response, structured like this:

```json
{
  "message": "Job Permission 321231 has been deleted."
}
```

Removes a user's job permission.

### HTTP Request

`DELETE https://harvest.greenhouse.io/v1/users/{id}/permissions/jobs`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
job\_permission\_id | Yes | integer | The ID of the job permission

## PUT: Add a Job Permission

```shell
curl -X PUT 'https://harvest.greenhouse.io/v1/users/{id}/permissions/jobs'
-H "Content-Type: application/json"
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```
> The above command takes a JSON request, structured like this:

```json
{ 
  "job_id": "150056", 
  "user_role_id": "16229" 
}
```

> The above command returns a JSON response, structured like this:

```json
{
  "id": 42906871,
  "job_id": 150056,
  "user_role_id": 16229
}
```

Creates a job permission with a specific user role for a given user.

### HTTP Request

`PUT https://harvest.greenhouse.io/v1/users/{id}/permissions/jobs`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
job_id | Yes | integer | The ID of the job
user\_role\_id | Yes | integer | The ID of the user role

Note: This endpoint does not support assigning a user role to a user for a confidential job.

### Response

Adding a job permission to a regular user returns status 201. 
Adding a job permission to a site admin user has no effect, and returns 204.

## The future job permission object

The user role a user will get when a job with the specified criteria is created.

```json
{
  "id": 87819,
  "office_id": 29192,
  "external_office_id": "ex-office-1",
  "department_id": 23425,
  "external_department_id": "ex-dept-1",
  "user_role_id": 4730
}
```

### Noteworthy Attributes

| Attribute | Description |
|-----------|-------------|
| id | The future job permission's unique identifier |
| office_id | The ID of the office of the job |
| external_office_id | The ID of the office in an external system. This is set by users and has no bearing on any other object in Greenhouse. If not set in Greenhouse, this will be null. |
| department_id | The ID of the department of the job|
| external_department_id | The ID of the department in an external system. This is set by users and has no bearing on any other object in Greenhouse. If not set in Greenhouse, this will be null. |
| user\_role\_id | The ID of the user role that will be granted |


## GET: List Future Job Permissions

```shell
curl 'https://harvest.greenhouse.io/v1/users/{id}/permissions/future_jobs'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
  {
    "id": 87819,
    "office_id": 24141,
    "external_office_id": "ex-office-1",
    "department_id": 12315,
    "external_department_id": "ex-dept-1",
    "user_role_id": 4730
  },
  {
    "id": 92834,
    "office_id": 8232,
    "external_office_id": "ex-office-2",
    "department_id": 12315,
    "external_department_id": "ex-dept-2",
    "user_role_id": 4730
  },
  {
    "id": 82129,
    "office_id": 8232,
    "external_office_id": "ex-office-2",
    "department_id": 92921,
    "external_department_id": null,
    "user_role_id": 4730
  }
]
```

List the permissions that will be granted to the user when a job is created in a particular Department/Office combination.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/users/{id}/permissions/future_jobs`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the user whose future job permissions to retrieve

This endpoint supports pagination. See the [Pagination](#pagination) section for more detail.

## DELETE: Remove a Future Job Permission

```shell
curl -X PUT 'https://harvest.greenhouse.io/v1/users/{id}/permissions/future_jobs'
-H "Content-Type: application/json"
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command takes a JSON request, structured like this:

```json
{ 
  "future_job_permission_id": 427600 
}
```

> The above command returns a JSON response, structured like this:

```
{
  "message": "Future Job Permission 639234 has been deleted."
}
```

Removes a user's future job permission.

### HTTP Request

`DELETE https://harvest.greenhouse.io/v1/users/{id}/permissions/future_jobs`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
future\_job\_permission\_id | Yes | integer | The ID of the future job permission

## PUT: Add a Future Job Permission

```shell
curl -X PUT 'https://harvest.greenhouse.io/v1/users/{id}/permissions/future_jobs'
-H "Content-Type: application/json"
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```
> The above command takes a JSON request, structured like this:

```json
{ 
  "office_id": 58028, 
  "department_id": 45644, 
  "user_role_id": 7607 
}
```

> The above command returns a JSON response, structured like this:

```
{
  "id": 9283,
  "office_id": 281921,
  "external_office_id": "ex-office-1",
  "department_id": 61921,
  "external_department_id": "ex-dept-1",
  "user_role_id": 91821
}
```

Creates a future job permission with a specific user role for a given user.

### HTTP Request

`PUT https://harvest.greenhouse.io/v1/users/{id}/permissions/future_jobs`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
office_id | No | integer | The ID of the office. Set to null to include all offices.
external_office_id | No | string | An ID that represents the office in an external system. This may be used instead of office_id. If included, office_id must be blank, and vice versa.
department_id | No | integer | The ID of the department. Set to null to include all departments.
external_department_id | No | string | This may be used instead of department_id. If included, department_id must be blank, and vice versa.
user\_role\_id | Yes | integer | The ID of the user role

### Response

Adding a future job permission to a regular user returns status 201. 
Adding a future job permission to a site admin user has no effect, and returns 204.

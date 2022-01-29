# User Roles

## The user role object

The roles that can be assigned to a user.

```json
{
  "id": 4729,
  "type": "interviewer",
  "name": "Interviewer"
}
```

### Noteworthy Attributes

| Attribute | Description |
|-----------|-------------|
| id | The user role ID |
| type | The type of role. Will be `interviewer` or `job_admin`.|
| name | The name of the role

## GET: List User Roles

```shell
curl 'https://harvest.greenhouse.io/v1/user_roles'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
  {
    "id": 4729,
    "type": "interviewer",
    "name": "Interviewer"
  },
  {
    "id": 4730,
    "type": "job_admin",
    "name": "Standard"
  },
  {
    "id": 4731,
    "type": "job_admin",
    "name": "Private"
  }
]
```

List the organization's roles that can be assigned to a user.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/user_roles`
# Current User

## Retrieve Current User

```shell
curl 'https://api.greenhouse.io/v1/partner/current_user'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```
> API Response 

```json
{
  "full_name": "Ron Weasley",
  "first_name": "Ron",
  "last_name": "Weasley",
  "email": "rweasley@hogwarts.edu",
  "id": 1234
}
```

Retrieve details about the current user


`GET https://api.greenhouse.io/v1/partner/current_user`


### Request Parameters

This request is simply the URL. It takes no parameters.

### Response Parameters

Property Name | Type           | Description
------------- | -------------- | --------------
full_name     | String         | The current user's full name
first_name    | String         | The current user's first name
last_name     | String         | The current user's last name
email         | String         | The email address associated with the current user
id            | Integer        | The ID of the current user
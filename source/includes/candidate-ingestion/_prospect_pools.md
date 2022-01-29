# Prospect Pools

## Retrieve Prospect Pools

```shell
curl 'https://api.greenhouse.io/v1/partner/prospect_pools'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> API Response

```json
[
  {
    "id": 123,
    "name": "Cold Outreach: Referred",
    "stages": [
      {
        "id": 1957,
        "name": "Not Contacted"
      },
      {
        "id": 1958,
        "name": "Contacted"
      },
      {
        "id": 1959,
        "name": "1st. Follow Up Sent"
      },
      {
        "id": 1960,
        "name": "2nd Follow Up Sent"
      },
      {
        "id": 1961,
        "name": "In Discussion"
      }
    ]
  },
  {
    "id": 456,
    "name": "Cold Outreach: Sourced",
    "stages": [
      {
        "id": 1962,
        "name": "Not Contacted"
      },
      {
        "id": 1963,
        "name": "Contacted"
      },
      {
        "id": 1964,
        "name": "1st. Follow Up Sent"
      },
      {
        "id": 1965,
        "name": "2nd Follow Up Sent"
      },
      {
        "id": 1966,
        "name": "In Discussion"
      }
    ]
  }
]
```

Retrieve prospect pools along with their stages for the current user's organization.

`GET https://api.greenhouse.io/v1/partner/prospect_pools`

_scope: prospect_pools.view_

### Request Parameters

This request is simply the URL. It takes no parameters.

### Response Parameters

| Property Name | Type    | Description                                                                                                                                                                     |
| ------------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id            | Integer | The ID of the prospect pool.                                                                                                                                                    |
| name          | String  | The name of the prospect pool.                                                                                                                                                  |
| stages        | Object  | The stages that belong to a prospect pool with the id and name of the stage. The list of stages will be ordered the same way that it is configured to be ordered in Greenhouse. |

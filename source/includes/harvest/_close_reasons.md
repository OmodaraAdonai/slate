# Close Reasons

When closing an opening, it is possible to designate the reason the opening is being closed. This might be "Filled" or "Cancelled" or some other reason.  These reasons are configured in Greenhouse.

## The close reason object

```json
{
  "id": 230,
  "name": "Hired"
}
```

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The close reason's unique identifier. This is the ID that would be used in POST or PATCH statements involving close reasons. |
| name | The name of the close reason |

## GET: List Close Reasons

List all of an organization's close reasons.

```shell
curl -X GET 'https://harvest.greenhouse.io/v1/close_reasons'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 365,
    "name": "Hired"
  },
  {
    "id": 366,
    "name": "Backfill"
  },
  {
    "id": 367,
    "name": "Order cancelled"
  }
]
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/close_reasons`

<br>

[See noteworthy response attributes.](#the-close-reason-object)
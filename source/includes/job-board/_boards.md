# Job Boards

## Retrieve job board

```json
{
  "name": "Your Organization",
  "content": "<p>...</p>"
}
```

Returns your organization's name and job board content. 

### HTTP Request

`GET https://boards-api.greenhouse.io/v1/boards/{board_token}`

### URL Parameters

Parameter | Description
--------- | -----------
board_token | Job Board URL token

# Cancel Order or Order Item

## Endpoint

```link
POST {{baseUrl}}/SdDocument/UpdateOrder
```

## Payload

```json
{
  "documentNo": "2002671072",  
  "actionType": "ORCL",
  "note": "",
  "actionData": "",
  "lines": [
    {
      "lineNumber": 1
    }
  ]
}
```

## Request Parameters

| Parameter   | Type     | Description                        | Possible Values          |
|-------------|----------|------------------------------------|--------------------------|
| `documentNo`| String   | The document number                | Example: `2002671072`    |
| `actionType`| String   | The type of action to be performed | `ORCL` for Order Cancel  |
| `note`      | String   | Additional notes for the action    |                          |
| `actionData`| String   | Additional data for the action     |                          |
| `lines`     | Array    | List of line items to be canceled  | Optional                 |
| `lineNumber`| Integer  | Line number to be canceled         | Example: `1`             |
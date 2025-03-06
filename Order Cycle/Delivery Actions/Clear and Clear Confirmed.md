# Clear And Clear Confirmed

## Endpoint

```link
POST {{baseUrl}}/SdDocument/UpdateDelivery
```

## Payload

```json
{
  "documentNo": "8000000100",
  "actionType": "DCLR",
  "note": "",
  "actionData": ""
}
```

## Request Parameters

| Parameter   | Type   | Description                        | Possible Values          |
|-------------|--------|------------------------------------|--------------------------|
| `documentNo`| String | The internal delivery internal number                | Example: `8000000100`    |
| `actionType`| String | The type of action to be performed | `DCLR`  Clear Request <br>  `DCLC`  Clear Confirmed   |
| `note`      | String | Additional notes for the action    |   |
| `actionData`| String | Additional data for the action     |                          |
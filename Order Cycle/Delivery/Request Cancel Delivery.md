# Request Cancel Delivery

## Endpoint

```link
POST {{baseUrl}}/SdDocument/UpdateDelivery
```

## Payload

```json
{
  "documentNo": "8000000100",
  "actionType": "DRCL",
  "note": "",
  "actionData": ""
}
```

## Request Parameters

| Parameter   | Type   | Description                        | Possible Values          |
|-------------|--------|------------------------------------|--------------------------|
| `documentNo`| String | The internal delivery internal number                | Example: `8000000100`    |
| `actionType`| String | The type of action to be performed | `DRCL`     |
| `note`      | String | Additional notes for the action    |   |
| `actionData`| String | Additional data for the action     |                          |
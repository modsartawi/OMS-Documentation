## Create Delivery (Consignment)

### Endpoint

```link
POST {{url}}/SdDocument/AddDelivery
```

### Payload

```json
{
  "documentNo": "1000000202",
  "referenceDeliveryNo": "REF_23423423",
  "storeCode": "P001",
  "note": "note special for the delivery-consignment",
  "deliveryScheduleFromTime": "2024-10-09T00:24:07.072Z",
  "deliveryScheduleToTime": "2024-10-09T00:24:07.072Z",
  "documentType" : "DL",
  "timeSlotId": "--",
  "timeSlotDescription": "8pm - 12 pm",
  "timeSlotDay": "Monday",
  "lines": [
    {
      "lineNumber": 1,
      "quantity": 3,
      "uom": "EA"
    }
  ],  
  "shippingAddress": {    
    "cityName": "Dammam - ad dabab",    
    "street1": "",
    "street2": "",
    "phone1": "",
    "gpsLat": 0,
    "gpsLon": 0
  }
}
```

#### Request Values

| Parameter                  | Type     | Description                                | Possible Values                           |
|----------------------------|----------|--------------------------------------------|-------------------------------------------|
| documentNo                 | String   | The document number                        |    The internal document number you received when creating the order        |
| referenceDeliveryNo        | String   | The reference delivery number              | Reference number from the external system. |
| storeCode                  | String   | The store code                             | Plant Code (Store Code) |
| note                       | String   | Special note for the delivery-consignment  | Max (100 chars) |
| deliveryScheduleFromTime   | String   | Delivery schedule start time (ISO 8601)    | ISO 8601 formatted date-time              |
| deliveryScheduleToTime     | String   | Delivery schedule end time (ISO 8601)      | ISO 8601 formatted date-time              |
| documentType               | String   | The document type                          | refer to the table for full list of values |
| timeSlotId                 | String   | The time slot ID                           | Optional |
| timeSlotDescription        | String   | Description of the time slot               | 8 pm - 10 pm   |
| timeSlotDay                | String   | Day of the time slot                       | Monday, Tuesday, Wednesday, etc.          |
| lines                      | Array    | List of line items                         | Array of line objects                     |
| lines[].lineNumber         | Integer  | Line number                                | Reference of the Order Line Item                     |
| lines[].quantity           | Decimal  | Quantity of items (Delivery) |  Should be less or equal to the reference document (Order) |
| lines[].uom                | String   | Unit of measure                            | `EA`                           |
| shippingAddress            | Object   | Shipping address details                   | Object containing address details         |
| shippingAddress.cityName   | String   | City name                                  |                      |
| shippingAddress.street1    | String   | Street address line 1                      |   |
| shippingAddress.street2    | String   | Street address line 2                      |  |
| shippingAddress.phone1     | String   | Phone number                               |  |
| shippingAddress.gpsLat     | Number   | GPS latitude                               |  |
| shippingAddress.gpsLon     | Number   | GPS longitude                              |  |

### Delivery Document Types

| Document Type | Description |
| ---           | ---         |
| BB            | Beyond Borders |
| DL         | Regular Delivery (Default) |
| SP | Special Product |

<mark>*** Respnse will be the same as when creating Order but it will be refered to a delivery</mark>

### Response Object

```json
{
  "data": {
    "documentNo": "8000000096",
    "orderNo": "1000007",
    "refDocumentNo": "1000000183",
    "entryTime": "2024-10-09T03:29:07.8745588",
    "entryUser": "PH",
    "documentDate": "2024-10-09T09:41:40.303"
  }
}
```

| Field          | Type     | Description                                |
|----------------|----------|--------------------------------------------|
| documentNo     | String   | The internal number for the delivery       |
| orderNo        | String   | The order number (External Reference)                          |
| refDocumentNo  | String   | The internal order number              |
| entryTime      | String   | The time the entry was made (ISO 8601)     |
| entryUser      | String   | The user who made the entry                |
| documentDate   | String   | The date of the document (ISO 8601)        |
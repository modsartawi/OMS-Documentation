
# OMS Order - Delivery API 

## Create Order

### Endpoint
```
POST {{url}}/SdDocument/AddDocument
```

### Payload
```json
{
    "orderNo": "1000007",
    "documentDate": "2024-10-09T09:41:40.303Z",
    "documentType": "CMRC",
    "documentSource": "HYBS",
    "deliveryType": "P",
    "customerId": "1000000034",
    "customerName": "MOHAMMED SARTAWI 33",
    "customerPhone": "966501076360",
    "PaymentType": "O",
    "storeCode": "P001",
    "note": "test order - to be cancelled",
    "lines": [
        {
            "lineNumber": 1,
            "itemNumber": "100021",
            "itemDescription": "Panadol extra",
            "salesQuantity": 3,
            "salesUom": "EA",
            "unitPrice": 10.5,
            "vatAmount": 4,
            "discount": 3
        },
        {
            "lineNumber": 2,
            "itemNumber": "100022",
            "salesQuantity": 3,
            "salesUom": "EA",
            "unitPrice": 10.5,
            "vatAmount": 4,
            "discount": 3
        }
    ],
    "conditions": [
        {
            "condType": "PTGC",
            "condAmount": 15,
            "referenceNumber": "ref_89234786723842",
            "cardNumber": "card_12341234"
        },
        {
            "condType": "PTHP",
            "condAmount": 17.5,
            "referenceNumber": "ref_892347873643",
            "cardNumber": "card_1234324",
            "paymentMethod": "ApplePay",
            "cardType": "Visa"
        }
    ]
}
```

### Parameters

| Parameter         | Description                                           | Data Type | Possible Values                           |
|-------------------|-------------------------------------------------------|-----------|-------------------------------------------|
| `orderNo`         | The reference from Hypris.                            | String    | Reference Order Number from the Source system `2000200123`                    |
| `documentDate`    | The date of the document.                             | DateTime    | ISO 8601 date format                      |
| `documentType`    | The type of the document.                             | String    | `CMRC`                       |
| `documentSource`  | The source of the document.                           | String    | `HYBS`                       |
| `deliveryType`    | Delivery type.                                        | String    | `P` for pick in store, `D` for delivery   |
| `customerId`      | Loyalty customer ID (Arbahi).                         | String    |                      |
| `customerName`    | Name of the customer.                                 | String    |  Max (100) chars                   |
| `customerPhone`   | Phone number of the customer.                         | String    | `966501076360`                    |
| `PaymentType`     | Type of payment.                                      | String    | `O` for Paid Online, `C` for cash on delivery.                            |
| `storeCode`       | Code of the store.                                    | String    | `P001`  SAP Plant code                      |
| `note`            | Additional notes for the order.                       | String    | Max 100 Chars                            |
| `lines`           | Array of line items in the order.                     | Array     |                                           |
| `lineNumber`      | Line number.                                          | Integer   | Sequential Line Number                     |
| `itemNumber`      | SKU of the item.                                      | String    | `100021`                             |
| `itemDescription` | Description of the item.                              | String    | `Panadaol 24 Tab Extra`                |
| `salesQuantity`   | Quantity of the item sold.                            | Integer   |                         |
| `salesUom`        | Unit of measure for the sales quantity.               | String    | `EA`                          |
| `unitPrice`       | Price per unit.                                       | Decimal     |                            |
| `vatAmount`       | Total VAT amount for the line.                        | Decimal     |                       |
| `discount`        | Total discount amount for the line.                                | Decimal     |                  |
| `conditions`      | Array of conditions applied to the order.             | Array     |                                           |
| `condType`        | Type of condition.                                    | String    | `PTGC` for Gift Card, `PTHP` for HyperPay |
| `condAmount`      | Amount of the condition.                              | Decimal     |                          |
| `referenceNumber` | Reference number for the condition.                   | String    | Transactoin Number for the payment (Hyperpay, Hypertab) of Trx/RequestID of Qitaf, Tamara, Arbahi, etc.                |
| `cardNumber`      | Card number associated with the condition.            | String    | last 4 numbers (Credit Card), or Gift Card Number.                     |
| `paymentMethod`   | Payment method.                                       | String    | `ApplePay`, `CreditCard`, etc.            |
| `cardType`        | Type of card.                                         | String    | `Visa`, `MasterCard`, etc.                |


### Payment Types

| Code  | Description         |
|-------|---------------------|
| `PTAR`| Arbahi Payment      |
| `PTCS`| Cash Payment        |
| `PTGC`| GiftCard Payment    |
| `PTHP`| HyperPay Payment    |
| `PTPT`| PayTabs Payment     |
| `PTQT`| Qitaf Payment       |
| `PTTM`| Tamara Payment      |

### Example Request
```http
POST {{url}}/SdDocument/AddDocument
Content-Type: application/json

{
    "orderNo": "1000007",
    "documentDate": "2024-10-09T09:41:40.303Z",
    "documentType": "CMRC",
    "documentSource": "HYBS",
    "deliveryType": "P",
    "customerId": "1000000034",
    "customerName": "MOHAMMED SARTAWI 33",
    "customerPhone": "966501076360",
    "PaymentType": "O",
    "storeCode": "P001",
    "note": "test order - to be cancelled",
    "lines": [
        {
            "lineNumber": 1,
            "itemNumber": "100021",
            "itemDescription": "Panadol extra",
            "salesQuantity": 3,
            "salesUom": "EA",
            "unitPrice": 10.5,
            "vatAmount": 4,
            "discount": 3
        },
        {
            "lineNumber": 2,
            "itemNumber": "100022",
            "salesQuantity": 3,
            "salesUom": "EA",
            "unitPrice": 10.5,
            "vatAmount": 4,
            "discount": 3
        }
    ],
    "conditions": [
        {
            "condType": "PTGC",
            "condAmount": 15,
            "referenceNumber": "ref_89234786723842",
            "cardNumber": "card_12341234"
        },
        {
            "condType": "PTHP",
            "condAmount": 17.5,
            "referenceNumber": "ref_892347873643",
            "cardNumber": "card_1234324",
            "paymentMethod": "ApplePay",
            "cardType": "Visa"
        }
    ]
}
```


### Response
```json
{
    "data": {
        "documentNo": "1000000187",
        "orderNo": "1000089",
        "refDocumentNo": null,
        "entryTime": "2024-11-21T20:08:26.6084903+03:00",
        "entryUser": "Hybris",
        "documentDate": "2024-10-09T09:41:40.303Z",
        "documentCategory": "O",
        "documentType": "CMRC",
        "documentTypeDescription": "CMRC",
        "documentSource": "HYBS",
        "documentSourceDescription": "HYBS",
        "documentReason": null,
        "netTotal": 37.8,
        "paidAmount": 32.50,
        "deliveryFees": 0,
        "amountDue": 0,
        "cashAmount": 5.30,
        "patienShare": 0,
        "deliveryDateTime": "0001-01-01T00:00:00",
        "deliveryType": "P",
        "paymentType": "O",
        "validTo": "2024-11-30T20:08:26.6084903+03:00",
        "customerId": "1000000034",
        "isActiveInStore": false,
        "isUrgent": true,
        "condDocumentNumber": "1000000776",
        "changedOn": "0001-01-01T00:00:00",
        "storeCode": "P001",  
        "note": "test order - to be cancelled", 
        "lines": [
            {
                "lineNumber": 1,
                "itemNumber": "100021",            
                "itemDescription": "ACRETIN 0.05% 30g CREAM",        
                "itemCategory": "STND",            
                "quantity": 1,
                "uom": "EA", 
                "unitPrice": 5.3,
                "discount": 0,
                "grossAmount": 5.3,             
                "vatAmount": 0,
                "netAmount": 5.3   
            },
            {
                "lineNumber": 2,
                "itemNumber": "100022",             
                "itemDescription": "ACTIFED 25 TAB",               
                "itemCategory": "STND",         
                "quantity": 3,
                "uom":  "EA",               
                "unitPrice": 10.5,
                "discount": -3,
                "grossAmount": 28.5,
                "vatAmount": 4,
                "netAmount": 32.5            
            }
        ],
        "conditions": [
            ...
        ],
        "status": {
            "overallStatus": null,
            "lastAction": "OCRT",
            "lastActionDescription": "Created",
            "readyStatus": null,
            "readyStatusDescription": null,
            "closeStatus": null,
            "closeStatusDescription": null,
            "clearStatus": null,
            "clearStatusDescription": null,
            "paymentStatus": "N",
            "paymentStatusDescription": "Need Payment",
            "deliveryStatus": null,
            "deliveryStatusDescription": null,
            "availabilityStatus": null,
            "availabilityStatusDescription": null,
            "acceptanceStatus": null,
            "acceptanceStatusDescription": null,
            "approvalStatus": null,
            "approvalStatusDescription": null,
            "consignmentStatus": null,
            "controlStatus": ""
        },
        "customer": {
            "customerId": "1000000034",
            "customerPhone": "966501076360",
            "customerName": "MOHAMMED SARTAWI 33"         
        },
        "deliveryScheduleFromTime": "0001-01-01T00:00:00",
        "deliveryScheduleToTime": "0001-01-01T00:00:00",
        "timeSlotId": null,
        "timeSlotDescription": null,
        "timeSlotDay": null,
        "courierCode": "DAWA",
        "courierDriverId": null,
        "courierDriverName": null,
        "courierDriverPhone": null,
        "courierDriverMasterPinCode": null,
        "courierDriverApproved": false,
        "courierDeliveryRequestId": null    
    },
    "statusCode": 200,
    "success": true,
    "message": "",
    "errors": null
}
```

### Response Important Fields

| Field                | Description                                                      | Data Type | Possible Values                           |
|----------------------|------------------------------------------------------------------|-----------|-------------------------------------------|
| `documentNo`         | Internal document number    | String    | this the internal document number we need it for creating the delivery object.                 |
| `entryTime`          | Entry time                                                       | DateTime  | ISO 8601 date format, entry datetime                      |
| `entryUser`          | Entry user                                                       | String    | entry user                       |


### Status Response Fields

| Field                          | Description                                      | Data Type | Possible Values                           |
|--------------------------------|--------------------------------------------------|-----------|-------------------------------------------|
| `overallStatus`                | Overall status                                   | String    | - `C` Completed <br> - `P` Partially      |
| `lastAction`                   | Last action                                      | String    | - `OCRT` <br>                             |
| `readyStatus`                  | Ready status                                     | String    | - `R` Ready <br> - `N` Need Transaction <br> - `C` Transaction Completed |
| `closeStatus`                  | Close status                                     | String    | - `C` Cancelled <br> - `R` Close Requested  |
| `clearStatus`                  | Clear status                                     | String    | - `C` Clear Requested <br> - `D` Clear Confirmed                     |
| `paymentStatus`                | Payment status                                   | String    | - `N` Need Payment <br> - `P` Paid        |
| `deliveryStatus`               | Delivery status                                  | String    | - `O` OutForDelivery <br> - `D` Delivered  <br> - `B` Returned Back to Store    |
| `consignmentStatus`            | Consignment status                               | String    | * this is an aggregated status <br> - `C` Cancelled <br> - `R` Ready  <br> - `D` Delivered  <br> - `O` OutForDelivery <br> - `S` Rescheduled  <br> - `B` Returned Back to Store <br> - `T` Created |


## Create Delivery (Consignment)

### Endpoint
```
POST {{url}}/SdDocument/AddDelivery
```

### Payload
```json
{
    "orderNo": "1000007",
    "documentDate": "2024-10-09T09:41:40.303Z",
    "documentType": "CMRC",
    "documentSource": "HYBS",
    "deliveryType": "P",
    "customerId": "1000000034",
    "customerName": "MOHAMMED SARTAWI 33",
    "customerPhone": "966501076360",
    "PaymentType": "O",
    "storeCode": "P001",
    "note": "test order - to be cancelled",
    "lines": [
        {
            "lineNumber": 1,
            "itemNumber": "100021",
            "itemDescription": "Panadol extra",
            "salesQuantity": 3,
            "salesUom": "EA",
            "unitPrice": 10.5,
            "vatAmount": 4,
            "discount": 3
        },
        {
            "lineNumber": 2,
            "itemNumber": "100022",
            "salesQuantity": 3,
            "salesUom": "EA",
            "unitPrice": 10.5,
            "vatAmount": 4,
            "discount": 3
        }
    ],
    "conditions": [
        {
            "condType": "PTGC",
            "condAmount": 15,
            "referenceNumber": "ref_89234786723842",
            "cardNumber": "card_12341234"
        },
        {
            "condType": "PTHP",
            "condAmount": 17.5,
            "referenceNumber": "ref_892347873643",
            "cardNumber": "card_1234324",
            "paymentMethod": "ApplePay",
            "cardType": "Visa"
        }
    ]
}
```
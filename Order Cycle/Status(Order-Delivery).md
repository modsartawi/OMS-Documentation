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


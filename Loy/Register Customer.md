# Register Customer

## Endpoint

```link
POST {{url}}/Loy/SignUpByEcommerce
```

## Payload

```json
{
  "RequestId": "5f448dea-7da7-43d9-bb16-83cdd5894071",
  "BranchId": "SAGR",
  "Mobile": "966501076360",
  "CountryCode": "SA",
  "FullName": "Full Name",
  "Email": "user@user.com"
}
```

## Parameters

| Parameter     | Description                                      | Data Type | Possible Values                           | Required |
|---------------|--------------------------------------------------|-----------|-------------------------------------------|----------|
| `RequestId`   | Unique request identifier                        | String    | GUID format                               | Yes      |
| `BranchId`    | Branch identifier                                | String    | `SAGR`                                    | Yes      |
| `Mobile`      | Customer mobile number with country code         | String    | 12 digits including country code `966501076360` | Yes      |
| `CountryCode` | Country code                                     | String    | `SA` for Saudi Arabia                     | Yes      |
| `FullName`    | Full name of the customer                        | String    | Max 100 characters                        | Yes      |
| `Email`       | Customer email address                           | String    | Valid email format                        | Yes      |

## Example Request

```http
POST {{url}}/Loy/SignUpByEcommerce
Content-Type: application/json
x-api-key: {{x-api-key}}

{
  "RequestId": "5f448dea-7da7-43d9-bb16-83cdd5894071",
  "BranchId": "SAGR",
  "Mobile": "966501076360",
  "CountryCode": "SA",
  "FullName": "Mohammed Sartawi",
  "Email": "mohammed@example.com"
}
```

## Response

```json
{
  "data": {
    "loyId": "1000000034",
    "mobileCountry": "SA",
    "mobile": "966501076360",
    "fullName": "test21 ",
    "birthDate": "1994-06-07T00:00:00",
    "gender": "M",
    "email": "sushilpattar72@gmail.com",
    "nationality": "",
    "nationalId": "",
    "insuranceCompany": "",
    "cityCode": "",
    "preferredLanguage": "E",
    "joinDate": "2024-05-12T16:46:29.0272095",
    "lastUpdate": "2025-01-03T10:20:00.588934",
    "tier": "S",
    "tierPointsBalance": 1335.48000,
    "pendingPoints": 0.00000,
    "pointsBalance": 9064.01015,
    "pointsBalanceAmount": 407,
    "pointsBalanceAmountCurrency": "SAR",
    "pointsExpireSoon": 0,
    "pointsExpireSoonDays": 30,
    "exchangeRate": 1,
    "profileUpdated": true,
    "profile": "W|D",
    "accrualFactor": 0.285714286,
    "redemptionFactor": 22.2222222222,
    "blockedReason": ""
  },
  "statusCode": 200,
  "success": true,
  "message": "",
  "errors": null
}
```

## Response Fields

| Field                           | Description                                | Data Type | Possible Values                    |
|---------------------------------|--------------------------------------------|-----------|------------------------------------|
| `loyId`                         | Unique loyalty customer identifier         | String    | Internal loyalty customer ID       |
| `mobileCountry`                 | Mobile country code                        | String    | Country code (e.g., `SA`)          |
| `mobile`                        | Customer mobile number                     | String    | Mobile number with country code    |
| `fullName`                      | Customer full name                         | String    | Customer name                      |
| `birthDate`                     | Customer birth date                        | DateTime  | ISO 8601 date format              |
| `gender`                        | Customer gender                            | String    | `M` for Male, `F` for Female       |
| `email`                         | Customer email address                     | String    | Email address                      |
| `nationality`                   | Customer nationality                       | String    | Nationality code                   |
| `nationalId`                    | Customer national ID                       | String    | National identification number     |
| `insuranceCompany`              | Insurance company                          | String    | Insurance company name             |
| `cityCode`                      | City code                                  | String    | City identifier                    |
| `preferredLanguage`             | Preferred language                         | String    | `E` for English, `A` for Arabic    |
| `joinDate`                      | Customer join date                         | DateTime  | ISO 8601 date format              |
| `lastUpdate`                    | Last profile update timestamp              | DateTime  | ISO 8601 date format              |
| `tier`                          | Customer loyalty tier                      | String    | Loyalty tier level (e.g., `S`)     |
| `tierPointsBalance`             | Tier points balance                        | Decimal   | Points for tier calculation        |
| `pendingPoints`                 | Pending loyalty points                     | Decimal   | Points pending approval            |
| `pointsBalance`                 | Current loyalty points balance             | Decimal   | Available loyalty points           |
| `pointsBalanceAmount`           | Points balance in currency                 | Number    | Points value in currency           |
| `pointsBalanceAmountCurrency`   | Currency for points value                  | String    | Currency code (e.g., `SAR`)        |
| `pointsExpireSoon`              | Points expiring soon                       | Number    | Points expiring within specified days |
| `pointsExpireSoonDays`          | Days until points expire                   | Number    | Number of days                     |
| `exchangeRate`                  | Points to currency exchange rate           | Number    | Exchange rate multiplier           |
| `profileUpdated`                | Whether profile is updated                 | Boolean   | `true` if updated, `false` if not  |
| `profile`                       | Profile flags                              | String    | Profile status flags               |
| `accrualFactor`                 | Points accrual factor                      | Decimal   | Rate for earning points            |
| `redemptionFactor`              | Points redemption factor                   | Decimal   | Rate for redeeming points          |
| `blockedReason`                 | Reason if account is blocked               | String    | Blocking reason or empty           |

## Error Responses


### Invalid Mobile Number
```json
{
  "statusCode": 400,
  "success": false,
  "message": "Mobile number should be 12 digits.",
  "errors": [
    {
      "errorCode": "LOY-00004",
      "internalErrorCode": null,
      "errorMessage": "Mobile number should be 12 digits."
    }
  ]
}
```

 


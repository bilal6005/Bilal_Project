# Check Reliance Web Services API Call

## Technical Document

**Date:** November 28, 2023  
**Last Updated:** November 28, 2023  

---

## Authentication

Every request must pass the authentication parameters along with the `uriTemplate` as given in the following example:


### Authentication Parameters:

- `apiLogin`
- `transactionKey`
- `sv` (softwareVersion)
- `tid` (Terminal Id)
- `uid` (UserId)

---

## Client Tool

[Postman](http://www.getpostman.com/apps) (Chrome App used for testing)

---

## Methods

### 1. verifyPOSUser (Method: POST)

- **UriTemplate:** "/verifyPOSLogin/"
- **Stored Procedure:** verifyPOSUser

**Sample URL:** http://checkrelianceAPI.glotechasp.com/WS/mobileApp.svc/verificationrequest?apiLogin=xP9JV25sf8&transactionKey=UEx5qgYycrBZ&sv=2.0.0.116&tId=226&uid=store30

**Sample Input JSON:**
```json
{
    "userId": "store30",
    "password": "123",
    "storeId": "30"
}
```

#### Output 1: If user id and password match for the store:

**Sample Output JSON:**
```json
{
    "userId": "store30",
    "password": "123",
    "storeId": "30"
}
```

#### Output 2: If user id and password do not match for the store:

**Sample Output JSON:**
```json
{
  "responseCode": 0,
  "responseMsg": "Invalid user id/password"
}
```

#### Output 3: If authentication parameters are not validated:

**Sample Output JSON:**
```json
{
  "responseCode": -1,
  "responseMsg": "Unauthorized Request"
}
```

### 2. saveImage (Method: POST)

- **UriTemplate: "/saveCustomerPhoto/"
- **Stored Procedure:** Image_Entry

**Sample URL:** http://checkrelianceAPI.glotechasp.com/WS/mobileApp.svc/verificationrequest?apiLogin=xP9JV25sf8&transactionKey=UEx5qgYycrBZ&sv=2.0.0.116&tId=226&uid=store30

**Sample Input JSON:**
```json
{
    "customerId": "24",
    "imageType": "ID Card", // [Picture, ID Card]
    "image": "Base64String",
    "position": "3"
}
```

#### Output 1: If required input is missing:

**Sample Output JSON:**
```json
{
  "responseCode": 0,
  "responseMsg": "Required Input Missing"
}
```

#### Output 2: If the request is successful:

**Sample Output JSON:**
```json
{
  "responseCode": 1,
  "responseMsg": "Success"
}
```

#### Output 3: If authentication parameters are not validated:

**Sample Output JSON:**
```json
{
  "responseCode": -1,
  "responseMsg": "Unauthorized Request"
}

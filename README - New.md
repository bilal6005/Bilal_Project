# CheckRelianceAPI

## Authentication using JWT (json web token):

### Authentication:
Every request must pass the authentication parameters along with the `uriTemplate` as given in the following example:


http://checkrelianceAPI.glotechasp.com/WS/mobileApp.svc/verificationrequest?apiLogin=xP9JV25sf8 &transactionKey=UEx5qgYycrBZ &sv=xxxx&tId=xxxx&uid=xxxx


### Authentication Parameters:
- `apiLogin`
- `transactionKey`
- `sv` (softwareVersion)
- `tid` (Terminal Id)
- `uid` (UserId)

### WORKFLOW:

#### Case 1:
API checks the parameters in every request URL. If parameters are not found, API returns the JSON response with status code 401.

**Sample Output JSON:**
```json
{
    "status": "Failed",
    "message": "Authentication parameters are missing!"
}
```

#### Case 2:
If parameters exist, API validates the values of the parameters. If parameters are not valid, API returns the JSON response with status code 401.

**Sample Output JSON:**
```json
{
    "status": "Failed",
    "message": "Authentication parameters are Invalid!"
}
```

#### Case 3:
If authentication parameters are valid, API generates and returns the JWT Token in JSON format with status code 200.

**Sample Output JSON:**
```json
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3MDQ5ODExMTcsImlzcyI6InlvdXRDb21wYW55SXNzdWVyLmNvbSIsImF1ZCI6InlvdXRDb21wYW55SXNzdWVyLmNvbSJ9.3VEA-noteZxdlSZOQuNSnIGATROkxMeXMQVYDJDo2sM"
}
```

#### Case 4:
Now if the request URL has valid parameters but an invalid token, API returns with status code 401.

**Sample Output JSON:**
```json
{
    "status": "Failed",
    "message": "Token is Invalid!"
}
```

#### Case 5:
If the parameters and token are valid in the request URL, then the authentication is Successful.

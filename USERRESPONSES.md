# Analyticord User HTTP responses
## Terms

> Auth: USER

You must authenticate as a user to use this endpoint.
> Auth: BOT

You must authenticate as a bot to use this endpoint.

## Login

```
/auth/login
```
> Auth: NONE.

Main Oauth2 endpoint for intilizing Discord oauth

> RESPONSE: REDIRECTION https://discordapp.com/oauth2

## Auth testing [DEPRECATED USE /api/botLogin]
```
/auth/validation
```
> Auth: BOT & USER

An endpoint used to verify that the token is valid. 
Reponse:
```
token OK: HTTP 200 BODY:'true'
token invalid: HTTP 200 BODY:'false'
```
[/TODO/] - Add /registerbot endpoint details after beta

## Bot info
> Auth: USER
```
/api/botinfo
```
(See README.md for queries)

Response:
```
HTTP 401 (no body) - Invalid token
HTTP 418 BODY: 'analyticord.error - wrongAuthHeaders
HTTP 200 BODY: Bot info
```
200 OK Response:
```json
[
    {
        "apikey": "",
        "id": "",
        "name": "",
        "owner": ""
    }
]
```
```
/api/version
```
> Auth: NONE

An endpoint to track the version number of libs
Requires: query: ?lib=

Responses:
```
HTTP 500 (Server Error) - No lib provided / Lib doesn't exist.
HTTP 200 BODY: version number (AS STRING)
```

```
/api/verified
```
> Auth: NONE

> BETAENDPOINT [Will be removed after beta]

Requires: Analyticord.dataID (Provided as a response when data is submitted under the name 'ID'

Response:
```
HTTP 418 BODY: 'This feature has been removed' - When the endpoint is deprecated
HTTP 418 Analyticord.Error: noQuery - When you don't pass the ?id query
HTTP 200 OK APPLICATION/JSON - Response below
```
HTTP 200:
```json
{
  "verified": true,
  "data": {
    "data": [
      ""
    ],
    "eventType": "",
    "id": "",
    "owner": "",
    "time": (EPOCH AS INT)
  }
}
```
## API Status
```
/api/status
```
> Auth: NONE

```json
{
  "overall": true,
  "analyticordManager": true,
  "databaseManager": true
}
```

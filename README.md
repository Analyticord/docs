# Analyticord Documentation
Welcome to the Analyticord Docs! Here you can find all of the publicly usable endpoints registered to the Analyticord API.
Analyticord is a simple platform to log statistics for your Discord Bot! Built by @Nevexo & @NightmareInfinity

All URIs, GET or POST start with https://api.analyticord.solutions/

## Terms

> Public Domain

An eventType or endpoint that can be used by anybody.

> BetaEndpoint

This endpoint may not always return expected errors.

## Errors you may get sent

When working with our API, you might encounter some errors when submitting data, getting data or doing anything really. As Analyticord is still in beta, we add new errors... ALOT, so it would be foolish of us to give you a list in here, for a list of all in-production errors please GET request this URL: https://api.analyticord.solutions/api/error?error=list this will give you a JSON response of every error the system can send you.

For information on just one error, call GET https://api.analyticord.solutions/api/error?error=[Insert error name here] this will be sent to you just like the erorr would be sent if it is raised.

The errors all have an ID, that is just for the backend and won't be sent to you, so don't rely on it.

## Authorization (it's spelt authorisation... get it right America)

Almost all endpoints require authorization, mostly from the user. Please provide a HTTP header called Authorization with the following

For user auth:

```
user [user token]
```

For bot auth:

```
bot [bot token]
```
If you don't know the token for your bot, login to our dashboard and go to your bots section, select your bot -> view token.
or use your user token and login GET /api/user/bots. Each endpoint listed below will have the authentication type it requires below it's name. Set your authorization header to fit what it says, for example
> Auth: USER

> Auth: BOT

## Submitting data
> Auth: BOT
```
HTTP POST /api/submit
```

This endpoint allows you to upload data of a specific eventType to our database. Set your encoding to x-www-form-urlencoded and provide the following:

```
data = data,data (provide a command seperated string)
eventType = eventType (See a list at the bottom of this document of eventTypes)
```

If data is sent successfully, you'll get a 200 OK reply.

## Getting data
> Auth: USER
This endpoint is subject to change in the future.
```
HTTP GET /api/getData
```
This endpint allows you to get information from our systems, this isn't really used by developers, it's mostly used by the frontend to get information and display your information. Some developers may want to use this so they can have commands in their bot to show some information that Analyticord collects. 

The getData endpoint requires the 'dataType' query, this is the eventType that you submitted, it can also support a 'limit' query, this counts from 1, finally, you must provide the id query, with the ID of the bot you wish to recieve data for.
```
GET /api/getData?dataType=demo&limit=1&id=123
```
This endpoint will either return the following errors:

> botNonExistant

> authfailed

> NoEventType (Raised if the eventType provided doesn't exist)

If there are no errors, you'll recieve an APPLICATION/JSON response that will either be blank (for no data matching that eventType & your authentication)
Or contain all the values you have submitted, for example:

```
[
    {
        "data": [
            "dank",
            "2"
        ],
        "eventType": "demo",
        "id": "1db3f0cc-f096-4c2b-9a39-440e4bba6600",
        "owner": "publicDomain",
        "time": 1501861609100
    },
    {
        "data": [
            "dankerthannight",
            "194575675638"
        ],
        "eventType": "demo",
        "id": "89f70d53-58fc-4406-940f-17cdd8e7fcf5",
        "owner": "publicDomain",
        "time": 1502031545663
    }
]
```

## Bot information 
> AUTH: USER
```
GET: /api/botinfo
```
This endpoint is used to get information about a bot that your user token owns, again, this endpoint is mainly used by the frontend, but feel free to use it yourself.

It requires the query id, to get information for a specific bot. For example:
```
GET: /api/botinfo?id=123
AUTH: user xx
```

## A list of bots
```
GET: /api/botlist
```
This endpoints returns a list of bots that your user token owns, this also is mainly for the frontend.

All it requires is auth and will return a list of bots owned by you.



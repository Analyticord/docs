# Analyticord Documentation
Welcome to the Analyticord Docs! Here you can find all of the publicly usable endpoints registered to the Analyticord API.

All URIs, GET or POST start with https://api.analyticord.solutions/

## Errors you may get sent

When working with our API, you might encounter some errors when submitting data, getting data or doing anything really. As Analyticord is still in beta, we add new errors... ALOT, so it would be foolish of us to give you a list in here, for a list of all in-production errors please GET request this URL: https://api.analyticord.solutions/api/error?error=list this will give you a JSON response of every error the system can send you.

For information on just one error, call GET https://api.analyticord.solutions/api/error?error=[Insert error name here] this will be sent to you just like the erorr would be sent if it is raised.

The errors all have an ID, that is just for the backend and won't be sent to you, so don't rely on it.

## Authorization (it's spelt authorisation... get it right America)

Almost all endpoints require authorization, mostly from the bot. Please provide a HTTP header called Authorization with the following

For user auth:

```
user [user token]
```

For bot auth:

```
bot [bot token]
```
If you don't know the token for your bot, login to our dashboard and go to your bots section, select your bot -> view token.
or use your user token and login GET /api/user/bots.

## Submitting and getting data.

```
HTTP POST /api/submit
```

This endpoint allows you to upload data of a specific eventType to our database. Authenticate as a bot, set your encoding to x-www-form-urlencoded and provide the following:

```
data = data,data (provide a command seperated string)
eventType = eventType (See a list at the bottom of this document of eventTypes)
```

If data is sent successfully, you'll get a 200 OK reply.



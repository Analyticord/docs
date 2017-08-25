# Analyticord-Docs/RATELIMITS

At the moment, the dynamic ratelimit system is a recommendation, a blog post (https://blog.analyticord.solutions) will be posted when these
ratelimits are fully enforced will be posted. In the mean time please follow the ratelimits anyway but you won't get banned.

```
/api/dynamic?type=ratelimit
```
Returns:
```
{
    "botInfo": 120,
    "enforced": 1503703548,
    "messages": 60
}

```
The ratelimts are presented in seconds, EG, send the messages count every 60 seconds.

The enforced object is an epoch timestamp of when you must comply with the ratelimits presented.

We recommend you check this endpoint every 30 minutes as the enforcement time is usally 35-40 minutes after the ratelimit endpoint is updated.

More information on ratelimits coming soon.

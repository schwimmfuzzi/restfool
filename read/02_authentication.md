# Authentication
A word in the beginning: Authentication can be done in many ways. I discuss some general topics at the beginning and describe a way I think thats fits well for my needs.

## Disclaimer
One inevitable points that must not be discussed is the following: **NEVER write crypto code yourself**. Use existing and open methods to sign codes and tokens and no, obscurity is not security! Keep your secrets safe (not in a repository), and use generated passwords and keys.

## Auth and REST
First things first: Every call you make in a REST api should be done via HTTPS. Development is some other thing, but keep your life environment safe. Inside a guarded connection, a proper signed auth token usually is enough for the most applications. This token comes along in the `Authorization-Header` of each call and contains everything the REST api (aka Server) needs to decide what is necessary to respond to the issuer. Issuer might be an machine itself or any user generated action. In both cases I talk of a client in the following.

The REST api is a stateless thing. This means, the server saves absolutely no information about a) a session, b) a user context or c) an application context. The information passed by a client comes in:
- URL fixed parts
- URL dynamic parts params and filters
- HTTP Headers
Given these information, the api decides how to deal with the clients request. Is the client authenticated, is he authorized (yep, two different things) what data shall be returned and how much of this.

## Auth Bottleneck
In a monolith application or MVC structured piece of software, usually you have access to auth information all the time. This means, when you render the frontend, you have information about which buttons to display and so on. In a REST based approach, you only have the token to process the clients request needs. Common examples are central user-apis that deal with authorization, that returns a token, the client uses to request other data. What you definitely want to prevent is a single `is this token correct call` to validate a tokens content on every request that comes in. For example if you have the company api I introduced earlier, a small workflow would be:

```
-> user logs in to application via web application
-> web application asks the user-api to sign in
-> user api checks credentials, returns a token if credentials correct
-> web application saves the token and forwards the user to internal area
-> user clicks on some company staff list
-> web application takes the token, inserts it to `Authentication-Header` of a new request and asks the staff-api to return a list of all staff
-> api checks the token and decides if token is correct and what data to return
```

So now imagine, that in a lean and fast REST request, every time the api needs to validate the token it would ask the user api to do so. Horrible, because it would (at least) double the amount of calls, and create an extreme load on the user-api. In a lot of applications the authorization workflow is the devil in the detail for poor scaling. We need to let the api (and yes, every api-worker in a scaled environment) decide if a token is valid. How do we reach this you might wonder? Especially when we want to hide the setup and the token from a frontend user. Its quite simple: we distribute the secret to sign/validate a token to every api worker/instance, when we start it. This even could be a dedicated call to the user endpoint (but I do not recommend this). Possibilities are almost endless.

## Authorization - Roles And Rights
I already noted, that there are two things, that are badly mixed all the time. Authentication and authorization. I dig deeper on this now.
<!-- roles and rights  -->
<!-- highlight the pros of having the rights directly added to the record -->
<!-- display, that this is a personal feeling -->
<!-- make an example with the primenumber thing and a seperated rights/roles thing on each service -->


# footnotes
<b id="f1">[1]</b> [Fielding - dissertation - Chap. 6](https://www.ics.uci.edu/~fielding/pubs/dissertation/evaluation.htm) [↩](#a1)
<b id="f2">[2]</b> [nouns are good, verbs are bad](http://apigee.com/about/blog/technology/restful-api-design-nouns-are-good-verbs-are-bad) [↩](#a2)

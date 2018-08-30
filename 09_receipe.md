# Receipe
This is to summarize important things:

## Beginner
* Use HTTPS.
* Use authenticated routes - reduce the unauthenticated ones to an absolute minimum.
* Model your resources with nouns only.
* Use plural, even it is a gramatically word plural.
* Stick to the base routes and the following mapping:
    * GET       /companies
    * POST      /companies
    * GET       /companies/:id
    * PUT       /companies/:id (complete re-write)
    * PATCH     /companies/:id (update a small piece)
    * DELETE    /companies/:id
* For sub-resources stick to a fixed convention:
    * METHOD /companies/:cid/department/:did
* A detail route responds with an object.
* An index route responds with a list of objects.
* Use meaningfull error codes. At least 200/301/400/401/403/422/500.
* Do not use your root path for anything (/).
* A single call contains _every peace of information_ that is needed to fulfill the complete request.

## Advanced
* Use api versioning - keep it simple. /vX.Y is enough.
* Never respond with the same data you receive.
* Model different Content-Types on the same resource.
* Hide information that can be used for crawling eg:
    * if username does not exist respond in the same way then existing user with incorrect password responds.
    * if routes do not exist or methods on existing routes, simply respond with Forbidden.

## Professionals
* Use HATEOAS.
* Use ETag.
* Use max-retries for failing requests.
* Use random retry-times 
* Use rate limits if you utilize API keys.
* Model pagination using HATEOAS.

## Final note
Always remember: stelessness empowers you with horizontal scalability - if it really is stateless.
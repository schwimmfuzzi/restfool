# ReSTful basics
What is this REST about? It means `representational state transfer`, but the name is not that important for what is covered here. If you are interested what is behind (and seriously you should be), I can highly recommend reading Roy Fieldings dissertation <sup id="a1">[1](#f1)</sup>.

REST builds on the very simple and deeply integrated HTTP principles and its methods.

## HTTP
These methods are what we know as `GET`, `POST`, `PUT`, `PATCH`, `DELETE`, `HEAD`, `OPTIONS` (and two more, not that major for REST). HTTP works on these, so does REST. That is every type of action a REST client can do -- better should do -- and that is far enough. In contrast to other interface paradigms for example `SOAP` or `RPC` interfaces, REST does never use any verb inside its URLs. REST only uses nouns. This can not be repeated enough times :) If you work with real world problems you will face this topic quite a lot. But having a clean REST api means having your URLs perfectly clean.

## HTTP Codes
At this point, I do not want to go to far with HTTP Codes, but remember one thing: HTTP has a lot more (useful) codes than 200, 500 and 404. Your REST api and every developer working with it will be extremely thankful if you use these properly. We will cover this later more precisely.

## Resources and URLs (or Verbs vs Nouns)
Lets go into detail. REST thinks about the content to communicate as resources. Everything you will get from a REST api is **a)** a single resource, **b)** multiple resources or **c)** a status code and a message. There might be some exceptions, but thats the important stuff you need to know for now. Addressing a resource is simply the semantical representation of the abstract data-model your api works with. Let me explain this a little bit more:

I hope I can follow this running example through the complete stuff I write here. Let us think about some api that deals with a company, its department and employees. If you think about how to address the company you might come to the idea of some unique identifier of it in you database or whatsoever. It is not that important what technology you use, lets simply think about a company with an `id`. Addressing this company is very straightforward:
```
api/company/:company-id
```
If you want to receive the information that is saved for this company *42*, you semantically `GET` the data of this resource by:
```
GET api/company/42
```
Now I want to introduce a REST convention that REST-newcomers need to get used to. Resources are **always written in plural**. So the above given URLs are wrong. In a real REST api you would use:
```
GET api/companies/42
```
This is a bit disturbing from time to time. But REST is not made for you, human, but primarily for machine-to-machine interaction. They do not care about incorrect plurals or singulars. Just be sure, to strictly use the plural naming convention. Things might become a bit easier for you if you read how REST addresses the complete list of all companies, that are inside you system.
```
GET api/companies
```
Returns you a so called *index* of you companies. While you only communicate date with your REST api you do not need any verbs or actions inside your URLs. The HTTP verbs are enough to address every action needed on your data. You might have heard about CRUD operations in your previous *stackoverflow* or *googling* time. CRUD is short for a set of transactions, commonly used in database environments, meaning `creating`, `reading`, `updating` and `deleting` content/records.
# footnotes
<b id="f1">[1]</b> [Fielding - dissertation - Chap. 6](https://www.ics.uci.edu/~fielding/pubs/dissertation/evaluation.htm) [↩](#a1)

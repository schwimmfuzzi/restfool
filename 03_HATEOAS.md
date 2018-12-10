# HATEOAS

Hypertext as the engine of application state. Word. Who wants to achieve a solid and clean REST implementation can not ignore this essential feature. In this section we inspect what is behind HATEOAS, what is it used for, and why it absolutely makes sense to use it.

## Levels of RESTfulness
https://martinfowler.com/articles/richardsonMaturityModel.html


## What is behind
***TODO***

## Why Should You Do HATEOAS?
Most of the apis out there only fulfill the second level of REST, as discussed earlier. Thats completely ok, but its not REST. But these apis are working properly and used a lot, so why should you do an overhead for HATEOAS you might ask. Well, I give you one answers (above the academic and trivial one "because definition requires it"): **it saves your time and work**

To be honest, I am lazy. And almost all programmers are, because we do not like to repeat ourselves. This is why we should consider HATEOAS as smart way to stay lazy. In my naive and elegant world you once write a HATEOAS feature for your api. If you modularize it properly, you use it in all your later apis, too. This peace of functionality takes the result you get out of your database and puts some syntactic sugar on it.

You can use this sugar for some pretty awesome things, and this is where the magic (or laziness) kicks in. One could use the HATEOAS information in a frontend to build the rights management on it. Wait. Did he said frontend and rights? All of us have spent tons of work on this in the majority of our projects, I guess. With HATEOAS this becomes pretty simple.

## Hypertext Application Language (HAL)
HAL is a internet draft proposed by Mike Kelly (stateless.co) and can be inspected in detail under [3](#f3).


# footnotes
<b id="f3">[3]</b> [JSON Hypertext Application Language](https://tools.ietf.org/html/draft-kelly-json-hal-08) [↩](#a1)



# links
* http://stateless.co/hal_specification.html
* https://restfulapi.net/hateoas/
* https://medium.com/@andreasreiser94/why-hateoas-is-useless-and-what-that-means-for-rest-a65194471bc8
* https://dzone.com/articles/introduction-hypertext-0
* https://jeffknupp.com/blog/2014/06/03/why-i-hate-hateoas/
* https://nordicapis.com/tools-to-make-hateoas-compliance-easier/
* https://nordicapis.com/designing-a-true-rest-state-machine/

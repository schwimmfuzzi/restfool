# Idempotency and Concurrency
When you are regularly dealing with REST interfaces, concurrency is a term you may not find in most articles. Idempotency on the other hand is a term that is named a lot of times, but often described misleadingly. I want to face both terms in a small dedicated section.

## Idempotency
tba

## Concurrency
A good developer (like we want to be one) should raise one question, when it comes to changing records: concurrency. Are the apis we discuss here free of concurrency? Definitely not. In a lot of cases these apis send information about a resource to be displayed on a UI.

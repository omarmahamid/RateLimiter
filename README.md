# RateLimiter
Design A Rate Limiter


Overview : 

A rate limiter is used to control the rate traffic sent by the client. it limits the number of client requests allowed to be sent over a specified period.
for example : 

* In socialMedia term, a user can't post more than 2 posts per second.
* You can't got more than 1 driving offence per hour.
* You can vote 5 times per day from the same IP address.


Advantages of Rate Limiter :

* Prevent resource starvation.
* Reduce cost.



# Where to put the rate limiter


1. At the server side implementation

![image](https://user-images.githubusercontent.com/59146036/185633638-c96407c2-e2f1-4a4d-a73c-ccc621a370b8.png)

2.Rate Limiter middleware

![image](https://user-images.githubusercontent.com/59146036/185634585-71ab83ba-0585-42e9-a011-ecd848fff6b9.png)


# Algorithms for rate limiter

* Token bucket
* Leaking bucket
* Fixed window counter
* Sliding window log
* Sliding window counter


# Token bucket algorithm
* mapping each request to one token
* Handling container of tokens
* for each request:
* if there are enough tokens, we take one token out for each request, and the request goes through.
* if there aren't enough tokens, the request is dropped

Illustrating diagram

![image](https://user-images.githubusercontent.com/59146036/185647213-706ee953-714c-4cc8-92bc-3cae5babee9c.png)





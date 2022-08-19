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

* 1.Token bucket
* 2.Leaking bucket
* 3.Fixed window counter
* 4.Sliding window log
* 5.Sliding window counter


# 1.Token bucket algorithm
algorithm:
* mapping each request to one token
* Handling container of tokens
* for each request:
* if there are enough tokens, we take one token out for each request, and the request goes through.
* if there aren't enough tokens, the request is dropped

Illustrating diagram:

![image](https://user-images.githubusercontent.com/59146036/185647213-706ee953-714c-4cc8-92bc-3cae5babee9c.png)


implementation:
The token bucket algorithm takes two parameters:
* Bucket size: the maximum number of tokens allowed in the bucket
* Refill rate: number of tokens put into the bucket every second(timeUnit)

pros and cons:
* Pros:
* the algorithm is easy to implement
* memory efficient
* Cons:
* It's hard to tune the token refill rate and the bucket size properly


# 2.Leaking bucket algorithm (Queue)
algorithm:
* when a request arrived the system checks if the queue is full. if it's full then dropp the request, else add them to the queue.
* Requests are pulled from the queue and processed at regular intervals

Illustrating diagram:

![image](https://user-images.githubusercontent.com/59146036/185653233-93e66418-22bc-49fa-ae3b-c0a2afdc3562.png)


implementation:
The leaking bucket algorithm takes two parameters:
* Bucket size: the queue size
* Outflow rate: it defines how many requests can be processed at a fixed rate (timeUnit)


pros and cons:
* Pros:
* the algorithm is easy to implement
* memory efficient
* Cons:
* It's hard to tune the Outflow rate and the bucket size properly

# 3.Fixed window counter algorithm

algorithm:

* the algorithm divide the timeline into fix-sized time wondows, and assign a counter for each window
* each request increments the counter by one
* once the counter reaches the pre-defined threshold, new requests are dropped until a new time window starts.

Illustartion diagram:




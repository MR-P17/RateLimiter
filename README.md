# RateLimiter
In-Memory-Data-Storage Assignment.


We can implement  Rate Limiter by maintaining three variables i.e. "count" and "interval" and "startTime".
INCR and EXPIRE Redis commands will be use to increment count and to check expiry of specified timeframe respectively. 

The "count" will keep track of number of request made by user in certain interval.
The "interval" will hold value of window for which we want to restrict the user request i.e. 60 sec.

Case1:

If the "userKey" is not present in the Redis, insert it and set the "count" to 1 and 
"startTime" to the current time and allow the request.

Case2:

Else, find the record of the "userKey" and if "currentTime – startTime >= interval", 
set the "startTime" to the current time and "count" to 1, and allow the request.

Case3:

If "currentTime – startTime <= interval" and If "count < 10", increment the Count and 
allow the request. If "count >= 10", reject the request with RateLimitExceededException.



# Install Redis on Ubuntu
````
sudo apt-get update
sudo apt-get install redis-server
````
# Start redis
````
redis-server
````

There is a configuration at the root directory of the Redis. 
You can get and set all Redis configurations by Redis CONFIG command.

With syntax:
````
redis 127.0.0.1:6379> CONFIG GET CONFIG_SETTING_NAME
````

For example: 
````
redis 127.0.0.1:6379> CONFIG GET loglevel  
1) "loglevel" 
2) "notice"
````
To get all configuration settings, use * in place of CONFIG_SETTING_NAME

Example:
````
redis 127.0.0.1:6379> CONFIG GET *  
  1) "dbfilename" 
  2) "dump.rdb" 
  3) "requirepass" 
  4) "" 
  5) "masterauth" 
  6) "" 
  7) "unixsocket" 
  8) "" 
  9) "logfile" 
 10) "" 
 11) "pidfile" 
 12) "/var/run/redis.pid" 
 13) "maxmemory" 
 14) "0"
 15) "maxmemory-samples" 
 16) "3" 
 17) "timeout" 
 18) "0" 
 19) "tcp-keepalive" 
 20) "0" 
 21) "auto-aof-rewrite-percentage" 
 22) "100" 
 23) "auto-aof-rewrite-min-size" 
 24) "67108864" 
 25) "hash-max-ziplist-entries" 
 26) "512" 
 27) "hash-max-ziplist-value" 
 28) "64" 
 29) "list-max-ziplist-entries" 
 30) "512" 
 31) "list-max-ziplist-value" 
 32) "64" 
 33) "set-max-intset-entries" 
 34) "512" 
 35) "zset-max-ziplist-entries" 
 36) "128" 
 37) "zset-max-ziplist-value" 
 38) "64" 
 39) "hll-sparse-max-bytes" 
 40) "3000" 
 41) "lua-time-limit" 
 42) "5000" 
 43) "slowlog-log-slower-than" 
 44) "10000" 
 45) "latency-monitor-threshold" 
 46) "0" 
 47) "slowlog-max-len" 
 48) "128" 
 49) "port" 
 50) "6379" 
 51) "tcp-backlog" 
 52) "511" 
 53) "databases" 
 54) "16" 
 55) "repl-ping-slave-period" 
 56) "10" 
 57) "repl-timeout" 
 58) "60" 
 59) "repl-backlog-size" 
 60) "1048576" 
 61) "repl-backlog-ttl" 
 62) "3600" 
 63) "maxclients" 
 64) "4064" 
 65) "watchdog-period" 
 66) "0" 
 67) "slave-priority" 
 68) "100" 
 69) "min-slaves-to-write" 
 70) "0" 
 71) "min-slaves-max-lag" 
 72) "10" 
 73) "hz" 
 74) "10" 
 75) "no-appendfsync-on-rewrite" 
 76) "no" 
 77) "slave-serve-stale-data" 
 78) "yes" 
 79) "slave-read-only" 
 80) "yes" 
 81) "stop-writes-on-bgsave-error" 
 82) "yes" 
 83) "daemonize" 
 84) "no" 
 85) "rdbcompression" 
 86) "yes"
 87) "rdbchecksum" 
 88) "yes" 
 89) "activerehashing" 
 90) "yes" 
 91) "repl-disable-tcp-nodelay" 
 92) "no" 
 93) "aof-rewrite-incremental-fsync" 
 94) "yes" 
 95) "appendonly" 
 96) "no" 
 97) "dir" 
 98) "/home/deepak/Downloads/redis-2.8.13/src" 
 99) "maxmemory-policy" 
100) "volatile-lru" 
101) "appendfsync" 
102) "everysec" 
103) "save" 
104) "3600 1 300 100 60 10000" 
105) "loglevel" 
106) "notice" 
107) "client-output-buffer-limit" 
108) "normal 0 0 0 slave 268435456 67108864 60 pubsub 33554432 8388608 60" 
109) "unixsocketperm" 
110) "0" 
111) "slaveof" 
112) "" 
113) "notify-keyspace-events" 
114) "" 
115) "bind" 
116) "" 
````

# Edit configuration
To update configuration, you can edit redis.conf file directly or you can update ocnfigurations via CONFIG set command.

## Syntax
````
redis 127.0.0.1:6379> CONFIG SET CONFIG_SETTING_NAME NEW_CONFIG_VALUE
Example:
redis 127.0.0.1:6379> CONFIG SET loglevel "notice" 
OK 
redis 127.0.0.1:6379> CONFIG GET loglevel  
1) "loglevel" 
2) "notice" 
````

# Redis - Data Types
Redis supports 5 types of data types
# Strings
Example
````
redis 127.0.0.1:6379> SET name "tutorialspoint" 
OK 
redis 127.0.0.1:6379> GET name 
"tutorialspoint"
````
# Hashes
A Redis hash is a collection of key value pairs. Redis hashes are maps between string fields and string values. 
Hence, they are used to represent objects.
Example:

# Lists
Redis Lists are simply lists of strings, sorted by insertion order.
You can add elements to a Redis List on the head or on the tail.
Example:
````
redis 127.0.0.1:6379> lpush tutoriallist redis 
(integer) 1 
redis 127.0.0.1:6379> lpush tutoriallist mongodb 
(integer) 2 
redis 127.0.0.1:6379> lpush tutoriallist rabitmq 
(integer) 3 
redis 127.0.0.1:6379> lrange tutoriallist 0 10  

1) "rabitmq" 
2) "mongodb" 
3) "redis"
````
# Sets
Redis Sets are an unordered collection of strings.
In Redis, you can add, remove. adn test for the existence of members in O(1)
Example:
````
redis 127.0.0.1:6379> sadd tutoriallist redis 
(integer) 1 
redis 127.0.0.1:6379> sadd tutoriallist mongodb 
(integer) 1 
redis 127.0.0.1:6379> sadd tutoriallist rabitmq 
(integer) 1 
redis 127.0.0.1:6379> sadd tutoriallist rabitmq 
(integer) 0 
redis 127.0.0.1:6379> smembers tutoriallist  

1) "rabitmq" 
2) "mongodb" 
3) "redis" 
````

# Sorted Sets
Redis Sorted Sets are similar to Redis Sets, non-repeating collections of Strings. 
The difference is, every member of a Sorted Set is associated with a score, 
that is used in order to take the sorted set ordered, from the smallest to the greatest score. 
While members are unique, the scores may be repeated.
Example:
````
redis 127.0.0.1:6379> zadd tutoriallist 0 redis 
(integer) 1 
redis 127.0.0.1:6379> zadd tutoriallist 0 mongodb 
(integer) 1 
redis 127.0.0.1:6379> zadd tutoriallist 0 rabitmq 
(integer) 1 
redis 127.0.0.1:6379> zadd tutoriallist 0 rabitmq 
(integer) 0 
redis 127.0.0.1:6379> ZRANGEBYSCORE tutoriallist 0 1000  

1) "redis" 
2) "mongodb" 
3) "rabitmq" 
````

# Redis command
Syntax
````
$redis-cli 
Example
````
$redis-cli 
redis 127.0.0.1:6379> 
redis 127.0.0.1:6379> PING  
PONG

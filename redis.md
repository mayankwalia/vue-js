```console
$ redis-cli
127.0.0.1:6379> SET name abc
OK
127.0.0.1:6379> GET name
"abc"
127.0.0.1:6379> SET age 20
OK
127.0.0.1:6379> GET age
"20"
127.0.0.1:6379> DEL age
(integer) 1     
127.0.0.1:6379> GET age
(nil)
127.0.0.1:6379> EXISTS age
(integer) 0     
127.0.0.1:6379> EXISTS name
(integer) 1     
127.0.0.1:6379> KEYS *
1) "name"       
127.0.0.1:6379> flushall
OK
127.0.0.1:6379> KEYS *
(empty list or set)
127.0.0.1:6379> ttl name
(integer) -2    
127.0.0.1:6379> GET name
(nil)
127.0.0.1:6379> SET name xyz
OK
127.0.0.1:6379> GET name
"xyz"
127.0.0.1:6379> ttl name
(integer) -1    
127.0.0.1:6379> expire name 10
(integer) 1     
127.0.0.1:6379> ttl name
(integer) 7     
127.0.0.1:6379> ttl name
(integer) 5     
127.0.0.1:6379> GET name
"xyz"
127.0.0.1:6379> GET name
(nil)
127.0.0.1:6379> setex name 10 abc
OK
127.0.0.1:6379> ttl name
(integer) 7
127.0.0.1:6379> ttl name
(integer) 4
127.0.0.1:6379> lpush friends ram
(integer) 1
127.0.0.1:6379> lrange friends 0 -1
1) "ram"
127.0.0.1:6379> lpush friends mohan
(integer) 2
127.0.0.1:6379> lrange friends 0 -1
1) "mohan"
2) "ram"
127.0.0.1:6379> rpush friends sita
(integer) 3
127.0.0.1:6379> lrange friends 0 -1
1) "mohan"
2) "ram"
3) "sita"
127.0.0.1:6379> LPOP friends
"mohan"
127.0.0.1:6379> RPOP friends
"sita"
127.0.0.1:6379> lrange friends 0 01
(error) ERR value is not an integer or out of range
127.0.0.1:6379> lrange friends 0 -1
1) "ram"
127.0.0.1:6379> SADD hobbies 'rubik cubes'
(integer) 1
127.0.0.1:6379> SMEMBERS hobbies
1) "rubik cubes"
127.0.0.1:6379> SADD hobbies 'rubik cubes'
(integer) 0
127.0.0.1:6379> SMEMBERS hobbies
1) "rubik cubes"
127.0.0.1:6379> SREM hobbies 'rubik cube'
(integer) 0
127.0.0.1:6379> SMEMBERS hobbies
1) "rubik cubes"
127.0.0.1:6379> SREM hobbies 'rubik cubes'
(integer) 1
127.0.0.1:6379> SMEMBERS hobbies
(empty list or set)
127.0.0.1:6379> HSET persons name raj
(integer) 1
127.0.0.1:6379> HGET persons name
"raj"
127.0.0.1:6379> HSET persons age 22
(integer) 1
127.0.0.1:6379> HGETALL persons
1) "name"
2) "raj"
3) "age"
4) "22"
127.0.0.1:6379> HDEL person age
(integer) 0
127.0.0.1:6379> HDEL persons age
(integer) 1
127.0.0.1:6379> HGETALL persons
1) "name"
2) "raj"
127.0.0.1:6379> HEXISTS persons name
(integer) 1
127.0.0.1:6379> HEXISTS persons age
(integer) 0
```

![image](https://user-images.githubusercontent.com/86161735/224558045-754475c1-5615-4156-933b-0f6bc6debbcd.png)

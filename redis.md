[TOC]

# overall

- 查看key是否存在

  ```
  EXISTS key
  ```

- 设置redis分布式

  ```
  redis-server --slaveof server18 6379 
  ```

- redis指定服务器

  ```
  redis-server -h [server-name]
  ```

# set

```
sismember key value  //判断key的set中是否存在某个value
scard key 			//查看key对应的set数据个数
smembers 			//查看set
```

# Zend_Cache backend using Redis with full support for tags

This Zend_Cache backend allows you to use a Redis server as a central cache storage. Tags are fully supported
without the use of TwoLevels cache so this backend is great for use on a single machine or in a cluster.
Works with any Zend Framework project including all versions of Magento!

## FEATURES

 - Uses the [phpredis PECL extension](https://github.com/nicolasff/phpredis) for best performance (requires **master** branch or tagged version newer than Aug 19 2011).
 - Falls back to standalone PHP if phpredis isn't available using the [Credis](https://github.com/colinmollenhour/credis) library.
 - Tagging is fully supported, implemented using the Redis "set" and "hash" datatypes for efficient tag management.
 - Key expiration is handled automatically by Redis.
 - Supports unix socket connection for even better performance on a single machine.
 - Supports configurable compression for memory savings. Can choose between gzip, lzf and snappy and can change configuration without flushing cache.
 - Uses transactions to prevent race conditions between saves, cleans or removes causing unexpected results.
 - __Unit tested!__

## INSTALLATION (Magento via composer)
```
 "repositories": 
 [
  {
    "type": "vcs",
    "url": "git@github.com:aligent/Cm_RedisSession.git"
  },
  {
    "type": "vcs",
    "url": "git@github.com:aligent/Cm_Cache_Backend_Redis.git"
  },
  {
    "type": "vcs",
    "url": "git@github.com:aligent/credis.git"
  }
],
```
 1. change your `composer.json` to include above repositories. 
 2. `github.com:aligent/Cm_RedisSession` is optional
 3. In require add something like
 ```"require": {
        "colinmollenhour/cache-backend-redis": "~3.1.0",
        "colinmollenhour/redis-session": "~3.1.0"
      },```
4. run `composer update colinmollenhour/*`
4. commit the generated `composer.lock`
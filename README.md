# mongodb redis cache
npm library for using redis read cache with mongoose.

Official npm package for using redis cache with mongodb while using mongoose package.
Your nodejs client will not have to call mongodb repeatedly and can make the calls to redis instead.
This will make your queries about 200% faster.

Recommended to use only on GET requests and not on POST requests. In subsequent versions, I'll also be adding a write through cache. If you want to collaborate - email me on akhil.sharma@myrl.tech or akhilsails@gmail.com

Installation :
```shell
npm i mongodb-redis-cache
```


Usage in your NodeJS Project :
```shell
var mongoose = require('mongoose');
var mongodbCache = require('mongodb-redis-cache');
var cache = mongooseCache(mongoose, "redis://127.0.0.1:6379");
```

#make sure you import mongoose library and pass it to the function along with your redis client address
#even if you don't pass a redis client address, it will consider 127.0.0.1:6379 as the default address

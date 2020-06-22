# mongodb redis cache
npm library for using redis read cache with mongoose.

Official npm package for using redis cache with mongodb while using mongoose package.
Your nodejs client will not have to call mongodb repeatedly and can make the calls to redis instead.
This will make your queries about 200% faster.
Best use case is for reports, analytics, charts, graphs etc. that run complex aggregation queries in the backend.

Recommended to use only on GET requests and not on POST requests, this doesn't mean that it won't work on POST requests, it will work, but it will be slow - all write functions will be slow, but read functions will be lightning fast. In subsequent versions, I'll also be adding a write through cache. If you want to collaborate - email me on akhil.sharma@myrl.tech or akhilsails@gmail.com

Installation :
```shell
npm i mongodb-redis-cache
```


Usage in your NodeJS Project :
include mongoose, then include the package and assign it to a variable and pass it to the variable, along with your redis environment.  like so -
```shell
var mongoose = require('mongoose');
var mongodbCache = require('mongodb-redis-cache');
var cache = mongooseCache(mongoose, "redis://127.0.0.1:6379");
```
instead of passing the address, feel free to pass directly from your environment variables and it can be automatically configured for Dev, QA and Production,
even if you don't pass a redis client address, it will consider 127.0.0.1:6379 as the default address.

Let's assume you are in the article routes and Whenever you wish to call a function in the model, in this case the Article model, you can pass an "expire" variable. This is used as an option in the library. like so - 

```shell
const articles = await Article.find().cache({ expire: 10 });
```
This will flush the cache every 10 seconds. If you don't pass any expire value, it will consider a default value of 60 seconds for flushing the cache.

Future scope - 

In subsequent versions, there will be support for multiple options, in addition to the expire function. Also, since this cache is for read-only functions, I plan to implement write-through as well.

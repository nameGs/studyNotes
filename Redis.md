# Redis

## 缓存

缓存处理流程：

> ​													->取得后返回结果->结束
>
> 前台请求数据->后台从缓存中获取->取不到时从数据库获取->更新缓存并返回结果
>
> ​													->数据库也没取到->返回空结果

1. 缓存击穿

   1. 问题：缓存中没有但是数据库中有的数据，由于并发用户特别多，都没存缓存中获取到，又同时去读取数据库，引起数据库压力瞬间增加，造成过大压力。
   2. 解决办法：
      1. 设置热点数据不过期
      2. 加互斥锁

2. 缓存穿透

   1. 问题：指缓存和数据库中都没有的数据，而用户不断发起请求，导致数据库压力过大。
   2. 解决方法：
      1. 接口层增加校验
      2. 将key-value对写为key-null，缓存有效时间设置为短点。

3. 缓存雪崩

   1. 问题：缓存中数据大批量到过期时间，查询数据量巨大，引起数据库压力过大甚至宕机。
   2. 解决方法：
      1. 缓存数据过期时间设置为随机数，防止同一时间大批量数据过期。
      2. 设置热点数据永不过期。
      3. 将热点数据均匀分布在不同缓存数据库中。

   
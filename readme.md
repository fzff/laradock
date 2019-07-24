
## laradocker的基本配置

##### 1 进入到laradock根目录下，复制 env.example，改成 .env格式的文件（这里我已经处理过了,你进入到根目录后会发现已经有一份.env文件了，那么就不需要在改了）。
##### 2 进入到.env文件修改APP_CODE_PATH_HOST这个变量的值。这个值就是自己实际项目的地址路径。
##### 3 在.env文件里添加这几行代码: 
###### DB_HOST=mysql
###### REDIS_HOST=redis
###### QUEUE_HOST=beanstalkd

##### 4 进入到nginx/sites这个文件里，在里面添加自己的nginx配置文件就好了。里面有示例可以参考。
##### 5 最后执行 docker-composer up -d redis mysql nginx。整个容器就启动了。
###### laradock镜像里几乎完全包含了我们常用的PHP相关的扩展（还有很多其他额外的丰富扩展——如果需要的话，直接引入使用就行了，默认是不会启动的）。因为业务需要，我额外增加了一个PHP的kafka扩展。当容器启动后，直接在代码里使用kafka就行了。

[更多详情，请点击这里](http://laradock.io/)


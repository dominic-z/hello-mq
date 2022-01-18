# p14
queueDeclare的exclusive参数是独占的意思，老师讲错了

# p15
basicConsume的第三个参数是成功消费信息的回调

# p19

重启过docker，之前的队列没持久化，所以hello队列消失了，报错`no queue 'hello' in vhost '/'`
这里重新声明
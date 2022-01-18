# p14
queueDeclare的exclusive参数是独占的意思，老师讲错了

# p15
basicConsume的第三个参数是成功消费信息的回调

# p19

重启过docker，之前的队列没持久化，所以hello队列消失了，报错`no queue 'hello' in vhost '/'`
这里重新声明

# p27
Worker03并不是没接收到信息，接收到了，只不过接收到之后sleep了；

# p31
看文档里的吧，比老师讲的好得多了
mq是预先将消息分配给各个队列的。信道1的qos为2的含义是mq允许这个信道最多有2条未处理的消息；

# p35
发现了一个神奇的事情，只有关闭了channel和connection，java程序才会关闭结束，否则会一直挂着；

# p37
这块视频太忽略multiple字段的功能了，异步处理阶段，返回的deliveryTag不是连续的，实际ackConfirmCallback的参数可能是
(1,false)/(2,false)/(10,true)，
代表的含义就是，第三个入参的含义是从3~10的消息已经确认，所以multiple是true

可以参考basicAck的注释，如下
> deliveryTag – the tag from the received AMQP.Basic.GetOk or AMQP.Basic.Deliver
multiple – true to acknowledge all messages up to and including the supplied delivery tag; false to acknowledge just the supplied delivery tag.

deliveryTag代表的是这次生产或者消费的tag，对于每一个新开启的信道，是从1开始的；
multiple就看注释吧
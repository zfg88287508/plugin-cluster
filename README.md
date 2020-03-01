# clusterplugin
cluster plugin for monibuca
实现了基本的集群功能，里面包含一对发布者和订阅者，分别在主从服务器中启用，进行连接。 起基本原理就是，在主服务器启动端口监听，从服务器收到播放请求时，如果从服务器没有对应的发布者，则向主服务器发起请求，主服务器收到来自从服务器的请求时，将该请求作为一个订阅者。从服务器则把tcp连接作为发布者，实现视频流的传递过程。
## 插件名称

Cluster

## 配置

主服务器的配置是ListenAddr，用来监听从服务器的请求。 从服务器的配置是Master,表示主服务器的地址。 当然服务器可以既是主也是从，即充当中转站。

```toml
[Plugins.Cluster]
Master = "localhost:2019"
ListenAddr = ":2019"
```
# ichunt-micro-registry
## golang微服务网关注册

`import引入`

"github.com/ichunt2019/ichunt-micro-registry/registry"

"github.com/ichunt2019/ichunt-micro-registry/config"

_ "github.com/ichunt2019/ichunt-micro-registry/registry/etcd"



```
func main(){
		nodes := []*registry.Node{
					{
						IP:   "192.168.2.246",//当前服务的ip
						Port: 2004,//当前服务的端口
						Weight:2,//当前服务的权重
					},
				}

		etcdConfig := registry.EtcdConfig{
			Address:  []string{"192.168.2.232:2379"},//etcd的节点ip
			Username: "",//etcd的节点的用户名
			Password: "",//etcd的节点的密码
			Path:"/ichuntMicroService/",//网关前缀，目前固定写即可
		}
		config.Register("sku_server",etcdConfig,nodes)// 第一个参数：服务名，第二个参数etcd配置，第三个参数当前注册节点信息
    

}
```

**注册到etcd中的节点信息 key=》val形式为**

register key:/ichuntMicroService/sku_server/192.168.1.234:60014

register key:/ichuntMicroService/sku_server/192.168.1.235:60014

设计思路：
![Image text](https://img.ichunt.com/images/github.com/beff335d3faa4ace7625c5ce607763ac.png)







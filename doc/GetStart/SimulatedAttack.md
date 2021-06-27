## 确定IP及端口
* 进入Ehoney系统，影子代理-透明代理列表

* **攻击IP**：即列表中的**探针IP**

* **攻击端口**： 即列表中的**转发端口**

** 注意：当未部署探针服务器时，攻击IP为协议转发列表中密网IP，攻击端口为协议转发列表中转发端口 **
## 模拟攻击
### HTTP
```curl http://攻击IP:攻击端口```
![http](https://www.showdoc.com.cn/server/api/attachment/visitfile/sign/280f30a8473ce3e4e2d68a719d5a1a67 "http")
### SSH
 ```ssh root@攻击IP -p 攻击端口``` 
   ** 默认账号密码 root root ** 
![ssh](https://www.showdoc.com.cn/server/api/attachment/visitfile/sign/813da6091c8ea75164c9322d55044600)
### MySQL
```mysql -u root -h 攻击IP -P 攻击端口 -p 123456 -e "show databases"``` 
   ** 默认账号密码 root root ** 
![mysql](https://www.showdoc.com.cn/server/api/attachment/visitfile/sign/ea2da203e977466446d603c6d7c5487a "mysql")
### Redis
```redis-cli -h 攻击IP -p 攻击端口``` 
 ** 默认密码 123 **
![redis](https://www.showdoc.com.cn/server/api/attachment/visitfile/sign/0fc19d603a3cc104e3c5254ebd8fa1c1 "redis")
### Telnet
```telnet 攻击IP 攻击端口``` 
** 默认账号密码 root admin **
![telnet](https://www.showdoc.com.cn/server/api/attachment/visitfile/sign/2eaa3b9b719e92339aeb4ead4b19d459 "telnet")
## 其他
* 注意:**模拟攻击类型要和蜜罐类型对应**
* 使用可视化界面进行连接，也会发起攻击日志。如HTTP可以使用浏览器访问;SSH可以使用Putty工具；MySQL可以使用Navicat工具;Redis可以使用RedisDesktopManager工具。
* 可以进入Ehoney系统，告警管理-告警列表好看是否攻击成功。
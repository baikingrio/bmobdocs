# 推送功能常见问题

Q:推送服务采用的协议是什么
A: `Websocket`

---

Q:会不会限制推送消息的数量
A:没有限制！

推送的用户数量没有限制，每天推送的消息条数也没有限制，所有都没有限制。

---

Q:服务器能支撑的长连接有多大
A:Bmob的推送服务器是耗内存型的，保持1个长连接占用<10KB的内存，64GB的内存能够支撑600万用户的长连接。

---

Q:Android推送收不到消息
A:
1.手机是否连入网络   
2.包名（应用包名，看配置文件）是否正确填写在web后台中  
 
如果还是不能接收到推送，请检查：  

3.手机是否有bmob的推送后台在运行  
4.后台的Installation表有没有该手机对应的设备信息

---

Q:iOS推送接收不到消息
A:
iOS的推送都是用apns。你确认是否操作了几点：  
1.检查推送的代码是否写错;   
2.真机操作；  
3.Bmob后台上传了未加密的p12证书；   
4.Bmob数据后台的Installation表是否可以看到对应数据。  
5.push token是否保存到服务器了

---

Q:推送的耗电和耗流量情况怎样
A:
以下说到的，不考虑推送的内容部分。推送内容的多少是由开发者决定的。

另外，实测电量、流量消耗，与网络状况相关比较大。

所以这里的数据是理论平均值：流量消耗 50K/天，电量消耗 60mAh/天。

---

Q:可以推送富文本到客户端吗
A:不直接支持文件的推送，但可以通过推送 url 来实现。
即先推送文件下载 url，到客户端触发逻辑来通过 url 下载文件。

---

Q:iOS在服务端如何推送有声音和Badge提示
A:需要开发者自己定义JSON格式，格式如下：

```java
{
	"alert" : "You got your emails.",
	"badge" : 9,
	"sound" : "bingbong.aiff"
}
```


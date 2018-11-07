# 数据类型
我遇到的数据类型及其转换问题

## 问题列表
### 1. 明明写入 session 的是 int64，取出来却提示 interface conversion: interface {} is float64, not int64。
案例：
```go
sess := session.GetSession(c)
te, _ := time.ParseDuration("+10m")
//给session写入一个int64值
sess.Set("sms_expire", time.Now().Add(te).Unix())
//取出 int64 值出错，提示  interface conversion: interface {} is float64, not int64。
sessExpire := sess.Get("sms_expire").(int64)

```
原因：Golang 中 JSON 里的数字默认都会转成 float64 类型。
正确的做法：
```go
sessExpire := int64(sess.Get("sms_expire").(float64))
```

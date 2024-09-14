# go dlt645-2007/1997




<img src="https://img.shields.io/github/stars/cqqqq/go645?style=social"/>

用go语言实现的dlt645解析
```shell
    go get github.com/cqqqq/go645
```

1. 读请求
```go
c := go645.NewClient(go645.NewRTUClientProvider(go645.WithEnableLogger(), go645.WithSerialConfig(serial.Config{
    Address:  "/dev/ttyUSB3",
    BaudRate: 19200,
    DataBits: 8,
    StopBits: 1,
    Parity:   "E",
    Timeout:  time.Second * 8,
})))

for {
    time.Sleep(time.Second)
    pr, err := c.Read(go645.NewAddress("3a2107000481", go645.LittleEndian), 0x00_01_00_00)
    if err != nil {
        log.Print(err.Error())
    } else {
        println(pr.GetValue())
}

}

```
2. protocal_test.go 中可查看更多案例

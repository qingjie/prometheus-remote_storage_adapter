# set env in .bash_profile
```
export GOPATH=$HOME/go-workspace # don't forget to change your path correctly!
export GOROOT=/usr/local/opt/go/libexec
export PATH=$PATH:$GOPATH/bin
```
# build remote_storage_adapter
## 获取remote_storage_adapter源码后，go会自动把相关的源码编译成可执行文件，并且保存在$GOPATH/bin/目录下。
```
cd /Users/qzhao/go-workspace/bin
go get github.com/prometheus/prometheus/documentation/examples/remote_storage/remote_storage_adapter
```
启动remote_storage_adapter并且设置Influxdb相关的认证信息：
```
INFLUXDB_PW=prom $GOPATH/bin/remote_storage_adapter --influxdb-url=http://localhost:8086 --influxdb.username=prom --influxdb.database=prometheus --influxdb.retention-policy=autogen
```

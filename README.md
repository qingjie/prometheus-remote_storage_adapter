# set env in .bash_profile
```
export GOPATH=$HOME/go-workspace # don't forget to change your path correctly!
export GOROOT=/usr/local/opt/go/libexec
export PATH=$PATH:$GOPATH/bin
```
# build remote_storage_adapter
## after we get sourcecode of remote_storage_adapter，go will automatically build sourcecode to a exec file，and save it to $GOPATH/bin/
```
cd /Users/qzhao/go-workspace/bin
go get github.com/prometheus/prometheus/documentation/examples/remote_storage/remote_storage_adapter
```
启动remote_storage_adapter并且设置Influxdb相关的认证信息：
```
INFLUXDB_PW=prom $GOPATH/bin/remote_storage_adapter --influxdb-url=http://localhost:8086 --influxdb.username=prom --influxdb.database=prometheus --influxdb.retention-policy=autogen
```

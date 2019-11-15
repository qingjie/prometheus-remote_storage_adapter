## install influxdb and start

### 
```
brew install influxdb
brew services restart/stop/status influxdb
influx
```
```
qzhao-mbp:consul qzhao$ influx
Connected to http://localhost:8086 version v1.7.9
InfluxDB shell version: v1.7.9
> show databases

```

### create database prometheus in influx
```
curl -XPOST http://localhost:8086/query --data-urlencode "q=CREATE DATABASE prometheus"
```

## build remote_storage_adapter

### set go env in .bash_profile
```
export GOPATH=$HOME/go-workspace # don't forget to change your path correctly!
export GOROOT=/usr/local/opt/go/libexec
export PATH=$PATH:$GOPATH/bin
```

### after we get sourcecode of remote_storage_adapter，go will automatically build sourcecode to a file，and save it to $GOPATH/bin/
```
cd /Users/qzhao/go-workspace/bin
go get github.com/prometheus/prometheus/documentation/examples/remote_storage/remote_storage_adapter
```
### start remote_storage_adapter and set username and password of Influxdb：
```
INFLUXDB_PW=prom $GOPATH/bin/remote_storage_adapter --influxdb-url=http://localhost:8086 --influxdb.username=prom --influxdb.database=prometheus --influxdb.retention-policy=autogen
```


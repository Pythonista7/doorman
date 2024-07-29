# Local Setup
Install etcd
```
brew install etcd
```

Start etcd
```sh
$ etcd
```

Clone and `cd` into the repo and run 
```
go mod tidy
```

Run the doorman server 
```
cd go/cmd/doorman
go build
./doorman -logtostderr -config=./config.yml -port=15000 -debug_port=15050 -etcd_endpoints=http://localhost:2379 -master_election_lock=/doorman.master -master_delay=200ms -hostname=localhost
```

Build and run the cli-client 

```
cd go/cmd/doorman_shell
go build
./doorman_shell --server=localhost:15000
```

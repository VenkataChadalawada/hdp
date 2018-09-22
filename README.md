# hdp
## Flume

#### create conf file
vi flume-conf.properties
``` xml
# example.conf: A single-node Flume configuration

# Name the components on this agent
a1.sources = r1
a1.sinks = k1
a1.channels = c1

# Describe/configure the source
a1.sources.r1.type = netcat
a1.sources.r1.bind = localhost
a1.sources.r1.port = 44444

# Describe the sink
a1.sinks.k1.type = logger

# Use a channel which buffers events in memory
a1.channels.c1.type = memory
a1.channels.c1.capacity = 1000
a1.channels.c1.transactionCapacity = 100

# Bind the source and sink to the channel
a1.sources.r1.channels = c1
a1.sinks.k1.channel = c1
```
#### Running the file
Go to flume-server location
` cd /usr/hdp/current/flume-server `
flume-ng agent -n a1 -f /home/horton/solutions/flume-ng.properties -c conf


#### In other terminal
telnet localhost 44444
hello world!

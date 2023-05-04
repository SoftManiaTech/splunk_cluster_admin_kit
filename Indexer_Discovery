In All of the indexers -> $SPLUNK_HOME/etc/system/local/inputs.conf

[splunktcp://9997]
disabled = 0

======================================================
In Manager node -> $SPLUNK_HOME/etc/system/local/server.conf

[indexer_discovery]
pass4SymmKey = my_secret
polling_rate = 10
indexerWeightByDiskCapacity = true


======================================================

In All of the forwarders -> $SPLUNK_HOME/etc/system/local/outputs.conf

[indexer_discovery:manager1]
pass4SymmKey = my_secret
manager_uri = https://10.152.31.202:8089

[tcpout:group1]
autoLBFrequency = 30
forceTimebasedAutoLB = true
indexerDiscovery = manager1
useACK=true

[tcpout]
defaultGroup = group1

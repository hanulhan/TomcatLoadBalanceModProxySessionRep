"TomcatLoadBalancerModProxySessionRep" 

Tomcat cluster definieren --> server.xml (Tomcat Instanzen)
DeltaManager für Kommunikation im Cluster
Multicast alive ping
	--> Multicast port 45564
	--> Enable Multicast
        route add -net 224.0.0.0 netmask 240.0.0.0 dev enp0s8


Session replication durch NioReceiver (Port 4000) Tomcat Instanzen
Damit Port 4000 auch von extern horcht, muss in der /etc/hosts der Rechnername mit der fixen IP verbunden werden
	<fixed-ip>	Rechnername
	e.g. 192.168.20.14	ClusterTest1

	
Kommunikation zum LoadBalancer über AJP (Port 8009)
	--> Enable Connector in Tomcat server.xml

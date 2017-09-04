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
	
	
	
Logging in Tomcat's /var/log/tomcat7/catalina.out

LoadBalancer (apache2 ) is 192.168.20.20

1. Start Instance 1 (192.168.20.14)
2. Start Instance 2 (192.168.20.159
3. Load page (http://192.168.20.20/test-app/)
	Here we have 
	Backend Tomcat: 192.168.20.14
	Session ID: A6CACAB68FDC43031833C3AD61B16831.jvm1
	current counter value is 6
	
4. Stop Instance 1
5. Load Page
   Here we have:
	Backend Tomcat: 192.168.20.15
	Session ID: A6CACAB68FDC43031833C3AD61B16831.jvm2
	current counter value is 7   

	
We see same session id from Instance 2



# openvpnsetup

SCRIPTS FOR VPN SETUP

* Install openvpn on client and server 
~~~
sudo apt-get install openvpn
~~~
* On the server generate shared static key by:
~~~
openvpn --genkey --secret <key file>
~~~
* Securely xfer static key over the client
* On the server, turn on IP forwarding
~~~
echo 1 > /proc/sys/net/ipv4/ip_forward
~~~
* On the server, add an IPTABLE rule to enable NAT for outbound packets coming in over the VPN
~~~
iptables -t nat -A POSTROUTING -s 10.1.0.1/16 -o eth0 -j MASQUERADE
~~~
* On the server, Run the openvpn server daemon
~~~
openvpn server.conf
~~~
* Run the client (on the client)
~~~
openvpn client.conf
~~~



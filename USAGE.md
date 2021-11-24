# Parameters details

## Listen
```
openp2p.exe -d -node OFFICEPC1 -user USERNAME1 -password PASSWORD1  
```
>* -d daemon mode is recommand. When the worker process is found to exit unexpectedly, a new worker process will be automatically started
>* -node Unique node name, unique identification
>* -user Unique user name, the node belongs to this user
>* -password Password
>* -sharebandwidth Provides bandwidth when used as a shared node, the default is 10mbps. If it is a large bandwidth of optical fiber, the larger the setting, the better the effect
>* -loglevel Need to view more debug logs, set 0; the default is 1
>* -noshare Not shared, the node is only used in a private P2P network. Do not join the shared P2P network, which also means that you CAN NOT use other people’s shared nodes

## Connect
```
openp2p.exe -d -node HOMEPC123 -user USERNAME1 -password PASSWORD1 -peernode OFFICEPC1 -dstip 127.0.0.1 -dstport 3389 -srcport 23389 -protocol tcp
```
>* -peernode Target node name
>* -dstip Target service address, default local 127.0.0.1
>* -dstport Target service port, such as windows remote desktop 3389, Linux ssh 22
>* -protocol Target service protocol tcp, udp
>* -peeruser The target user, if it is a node under the same user, no need to set
>* -peerpassword The target password, if it is a node under the same user, no need to set
>* -f Configuration file, if you want to configure multiple P2PApp refer to [config.json](/config.json)

## Client update
```
# update local client
openp2p update  
# update remote client
curl --insecure 'https://openp2p.cn:27182/api/v1/device/YOUR-NODE-NAME/update?user=&password='
```

Windows system needs to set up firewall for this program, the program will automatically set the firewall, if the setting fails, the UDP punching will be affected.  
The default firewall configuration of Linux system (Ubuntu and CentOS7) will not have any effect, if not, you can try to turn off the firewall
```
systemctl stop firewalld.service
systemctl start firewalld.service
firewall-cmd --state
```
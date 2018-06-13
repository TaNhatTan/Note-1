## JxVoLam for Linux

* **[I. Setup Game Server](#I)**
* **[II. Khách hàng thao tác](#II)**
* **[III. Kỹ thuật thao tác](#III)**

<a name="I"></a>
#### I. SETUP GAME SERVER
##### 1. Setup lib:
```
yum install glibc.i686 libuuid.i686 libstdc++.i686 libgcc.i686
```

##### 2. Setup mysql:
```
yum install mysql-server
```
***Pass default: Abcd6789***

<a name="II"></a>
#### II. KHÁCH HÀNG THAO TÁC:  
/sbin/ip addr add ipproxy/32 dev eth1:1

vim /etc/rc.local 

add thêm dòng vào 

/sbin/ip addr add ipproxy/32 dev eth1:1

check xem có nat chưa 

 iptables -nvL

NAt IP 

 iptables -t nat -I PREROUTING -d 10.20.10.x/32 -m tcp -p tcp --dport 6666 -j DNAT --to-destination ipproxy
 
 /etc/init.d/iptables save

check game có chạy port 6666 and 5622 

netstat -ntpl

telnet ipproxy 5622 và 6666 có kí tự đặt biệt là ok

- Phân quyền cho các file sau có quyền execute:
```
chmod +x gateway/goddess_y gateway/bishop_y gateway/s3relay/s3relay_y server1/jx_linux_y
```
- Sửa file `goddess.cfg` phần InternetIp về IP local server
- Sửa file `bishop.cfg` phần MacAddress, Account (account này phải khác các account trước), InternetIp về IP local server
- Sửa file `s3relay/relay_config.ini` với các thông số giống `bishop.cfg`
- Sửa table serverlist (trong MySQL) trên vps window, add thêm IP + MAC IP public của server linux.
- Sửa InternetIp  của file `server1/servercfg.ini` về IP proxy
- Khách hàng bảo trì tất cả server, restart + reboot vps windb

<a name="III"></a>
#### III. KỸ THUẬT THAO TÁC
- Mở port game trên proxy.
- Setup IP Proxy trên GameServer.
- Cấu hình iptables để NAT port game ra proxy.
```
iptables -t nat -I PREROUTING -d <ip-backend>/32 -p tcp -m tcp --dport 6666 -j DNAT --to-destination <ip-proxy>
```

***Note: Port login: 5622 + Port game: 6666, nếu có sự thay đổi port phải báo kỹ thuật để đổi port.***


Nguồn: https://github.com/TraiOi/d7b3560525906f386528ca7d588ee5e9/blob/master/MyNote/JxVoLam-Linux.md

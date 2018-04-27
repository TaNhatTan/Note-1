Config Mail Relay via exim


1. Copy default config

cp /etc/exim.conf /etc/exim.conf.org

vi /etc/exim.conf

2. Tìm section begin routers, thêm hoặc thay thế lookuphost

lookuphost:

  driver = manualroute
  
  domains = ! +local_domains
  
  ignore_target_hosts = 127.0.0.0/8
  
  transport = auth_relay
  
  route_list = * <relay-domain>
  
  no_more
  
3. Cấu hình cho transport, bằng section begin transports, thêm vào
auth_relay:

  driver = smtp
  
  port = 25
  
  hosts_require_auth = $host_address
  
  hosts_require_tls = $host_address
  
Note: Port 25, 587, 465 tuỳ vào cấu hình mail cần sử dụng.

4. Cấu hình begin authenticators bằng cách thêm dòng

auth_login:
  
  driver = plaintext
  
  public_name = LOGIN
  
  hide client_send = : <username> : <password>


Nguồn  https://github.com/TraiOi/d7b3560525906f386528ca7d588ee5e9/blob/master/MyNote/Mail-Relay-Config.md

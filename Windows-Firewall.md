## Windows Firewall

#### Open Ports
```
netsh advfirewall firewall add rule name="Open Port 80" dir=in action=allow protocol=TCP localport=80
netsh advfirewall firewall add rule name="Open Port 80" dir=out action=allow protocol=TCP localport=80
```

#### Allow Ping
```
netsh advfirewall firewall add rule name="ICMP Allow incoming V4 echo request" protocol=icmpv4:8,any dir=in action=allow
```

Nguồn: https://github.com/TraiOi/d7b3560525906f386528ca7d588ee5e9/blob/master/MyNote/Windows-Firewall.md

  drop ip on raw
  
       iptables -t raw -I PREROUTING -s IP -j DROP
  
  Note iptable 
  
  https://gist.github.com/potem/1511984

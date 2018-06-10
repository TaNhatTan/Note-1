  drop ip on raw
  
       iptables -t raw -I PREROUTING -s IP -j DROP
  
  Note iptable 
  
  https://gist.github.com/potem/1511984
  https://gist.github.com/boardstretcher/4a805f3ce76e592780d15252c13226e5

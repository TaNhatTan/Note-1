Check DDos
         
  I. CHECK NUMBER OF CONNECTIONS
   
   
1. All IPs:
        
            netstat -npt | awk '{print $5}' | grep -Eo '([0-9]{1,3}\.){3}[0-9]{1,3}' | cut -d: -f1 | sort | uniq -c | sort -nr | head


2. For 1 IP on Port / Gen 3

        
            ss -nat | grep <IP>:<Port> | awk '{print $5}' | grep -Eo "([0-9]{1,3}\.){3}[0-9]{1,3}" | sort | uniq -c | sort -nr


3. For 1 IP on Port / Gen4

            conntrack -L | grep <IP> | grep <Port> | awk '{print $5}' | grep -Eo "([0-9]{1,3}\.){3}[0-9]{1,3}" | sort | uniq -c | sort -nr


  II. CHECK DENY IPS LOG


 1. Proxy Gen3:
       
                tail -f /var/log/lfd.log

                tail -f /var/log/message


2. Proxy Gen4:

                iptables -I INPUT 1 -p tcp --syn --dport <port-dst> -d <ip-dst> -m connlimit --connlimit-above 3 -j REJECT

                watch -n1 "ipset list | grep timeout"
                
                watch -n1 "ipset list | grep timeout | sed 's/timeout/\|/' | sed 's/ts/ts \|/' | sed 's/tes/tes \|/'"


  III. BLOCK IPS

1. Iptables:
        
   joinbot, syn flood

               iptables -I INPUT 1 -p tcp --syn --dport <port-dst> -d <ip-dst> -m connlimit --connlimit-above 3 -j REJECT



2.CSF 

chan ip on proxy 

        csf -d <IP>

bo chan

        csf -dr <IP>

allow ip

        csf -a <IP>

bo allow 

        csf -ar <IP>


3.IP set gen4

         ipset list -n
         
         ipset add NAME 1.2.3.4
         
         ipset del NAME 1.2.3.4


https://github.com/firehol/firehol/wiki/Working-with-IPSETs

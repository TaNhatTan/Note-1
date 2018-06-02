backup source web 

1/ Xác định source code:

 pwd /home/webserver/sovaco.vn 
 
 ls public_html
 
 2/ Xác định databases:
 
 /usr/bin/mysql -e "show databases;" | grep -v "Database\|admin_default\|information_schema\|mysql\|performance_schema\|roundcube"
 
 Có 2 databases nên có thể grep trong public_html có sử dụng những database nào:

grep "sovacovn_sql" public_html/ -Rl

Kiểm tra thì chỉ có 1 database được dùng là sovacovn_sql, nên dump ra:

mysqldump sovacovn_sql > sovacovn_sql.sql

3/ Nén (nên để cách li source và database, đồng thời compress):

ls -1
  
  public_html 
 
 sovacovn_sql.sql
 
 tar -czvf sdoajfaisofjos-savaco.vn.tar.gz public_html sovacovn_sql.sql
 
 mv sdoajfaisofjos-savaco.vn.tar.gz public_html/

gui link http://sovaco.vn/sdoajfaisofjos-savaco.vn.tar.gz
 
 và vào screen hẹn giờ tự xóa file nén khỏi docroot:
 
 sleep 10800 ; rm /home/webserver/sovaco.vn/public_html/sdoajfaisofjos-savaco.vn.tar.gz

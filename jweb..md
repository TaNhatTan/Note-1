    find /home/*/web/*/public_html -name '42276*'
    B3. Vào server jweb, tìm database tương ứng:
    [root@vip public_html]# pwd /home/vip1/web/xxxx.com/public_html
    root@vip public_html]# grep vip1_ * -Rl application/config/database.php
    import 34179.sql vào.








giờ cấu hình SSL:

1. ssl_certificate /etc/nginx/ssl/jweb/ssl.congnghe123.vn.pem 
là nối của file cert và ca:

congnghe123.vn.crt + congnghe123.vn.ca-bundle


ssl_certificate_key /etc/nginx/ssl/jweb/ssl.congnghe123.vn.key 
là file private key

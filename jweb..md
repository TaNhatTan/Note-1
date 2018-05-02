    find /home/*/web/*/public_html -name '42276*'
    B3. Vào server jweb, tìm database tương ứng:
    [root@vip public_html]# pwd /home/vip1/web/xxxx.com/public_html
    root@vip public_html]# grep vip1_ * -Rl application/config/database.php
    import 34179.sql vào.

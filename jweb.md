IP server cũ: 

Các bước thực hiện:

B1: xin id của database ví dụ 34179.

B2: vào server cũ , tìm database: 

[root@example ~]# find /home/*/web/*/public_html -name '34179*' /home/admin/web/jweb.vn/public_html/db/34179.sql 

B3. Vào server jweb, tìm database tương ứng: 

[root@vip public_html]# pwd /home/vip1/web/phuquycompany.net/public_html

[root@vip public_html]# grep vip1_ * -Rl application/config/database.php 

import 34179.sql vào.

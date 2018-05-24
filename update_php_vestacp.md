  yum update remi-release
  
  yum --enablerepo=remi,remi-php70 update php php-*
  
 có thể thay thế 70 thành 72 nêú là php7.2
 
cách khác


  yum repolist all
  
có repo remi-php56 remi-php70 remi-php71 ....


tương ứng là 5.6, 7.0, 7.1,...


muốn up lên bản nào thì enable repo đó lên

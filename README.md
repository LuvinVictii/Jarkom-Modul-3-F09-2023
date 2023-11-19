# Praktikum Modul 3 Jarkom
### Kelompok F09
|   Nama   |      NRP      |
|:--------:|:-------------:|
| Muhammad Daffa Harits | 5025211005 |
| Muhammad Naufal Baihaqi | 5025211103 |

![Topologi](https://github.com/LuvinVictii/Jarkom-Modul-3-F09-2023/assets/78089862/c680902e-2c04-4089-8b64-ab4d341abbab)
| Node    | Kategori         | Image Docker                     | Konfigurasi IP |
|---------|------------------|----------------------------------|----------------|
| Aura    | Router (DHCP Relay) | danielcristh0/debian-buster:1.1 | DHCP Server    |
| Heiter  | DNS Server       | danielcristh0/debian-buster:1.1 | Static         |
| Denken  | Database Server  | danielcristh0/debian-buster:1.1 | Static         |
| Eisen   | Load Balancer    | danielcristh0/debian-buster:1.1 | Static         |
| Frieren | Laravel Worker   | danielcristh0/debian-buster:1.1 | Static         |
| Flamme  | Laravel Worker   | danielcristh0/debian-buster:1.1 | Static         |
| Fern    | Laravel Worker   | danielcristh0/debian-buster:1.1 | Static         |
| Lawine  | PHP Worker       | danielcristh0/debian-buster:1.1 | Static         |
| Linie   | PHP Worker       | danielcristh0/debian-buster:1.1 | Static         |
| Lugner  | PHP Worker       | danielcristh0/debian-buster:1.1 | Static         |
| Revolte | Client           | danielcristh0/debian-buster:1.1 | Dynamic        |
| Richter | Client           | danielcristh0/debian-buster:1.1 | Dynamic        |
| Sein    | Client           | danielcristh0/debian-buster:1.1 | Dynamic        |
| Stark   | Client           | danielcristh0/debian-buster:1.1 | Dynamic        |


## No 0
>Setelah mengalahkan Demon King, perjalanan berlanjut. Kali ini, kalian diminta untuk melakukan register domain berupa riegel.canyon.yyy.com untuk worker Laravel dan granz.channel.yyy.com untuk worker PHP mengarah pada worker yang memiliki IP \[prefix IP].x.1.


## No 1
>Lakukan konfigurasi sesuai dengan peta yang sudah diberikan.


## No 2
>Client yang melalui Switch3 mendapatkan range IP dari \[prefix IP].3.16 - \[prefix IP].3.32 dan \[prefix IP].3.64 - \[prefix IP].3.80


## No 3
>Client yang melalui Switch4 mendapatkan range IP dari \[prefix IP].4.12 - \[prefix IP].4.20 dan \[prefix IP].4.160 - \[prefix IP].4.168


## No 4
>Client mendapatkan DNS dari Heiter dan dapat terhubung dengan internet melalui DNS tersebut


## No 5
>Lama waktu DHCP server meminjamkan alamat IP kepada Client yang melalui Switch3 selama 3 menit sedangkan pada client yang melalui Switch4 selama 12 menit. Dengan waktu maksimal dialokasikan untuk peminjaman alamat IP selama 96 menit


## No 6
>Pada masing-masing worker PHP, lakukan konfigurasi virtual host untuk website [berikut](https://drive.google.com/file/d/1ViSkRq7SmwZgdK64eRbr5Fm1EGCTPrU1/view?usp=sharing) dengan menggunakan php 7.3.


## No 7
>Kepala suku dari [Bredt](https://frieren.fandom.com/wiki/Bredt_Region) Region memberikan resource server sebagai berikut:<br>
a. Lawine, 4GB, 2vCPU, dan 80 GB SSD.<br>
b. Linie, 2GB, 2vCPU, dan 50 GB SSD.<br>
c. Lugner 1GB, 1vCPU, dan 25 GB SSD.<br>
aturlah agar Eisen dapat bekerja dengan maksimal, lalu lakukan testing dengan 1000 request dan 100 request/second.


## No 8
>Karena diminta untuk menuliskan grimoire, buatlah analisis hasil testing dengan 200 request dan 10 request/second masing-masing algoritma Load Balancer dengan ketentuan sebagai berikut:<br>
a. Nama Algoritma Load Balancer<br>
b. Report hasil testing pada Apache Benchmark<br>
c. Grafik request per second untuk masing masing algoritma.<br> 
d. Analisis


## No 9
>Dengan menggunakan algoritma Round Robin, lakukan testing dengan menggunakan 3 worker, 2 worker, dan 1 worker sebanyak 100 request dengan 10 request/second, kemudian tambahkan grafiknya pada grimoire.


## No 10
>Selanjutnya coba tambahkan konfigurasi autentikasi di LB dengan dengan kombinasi username: “netics” dan password: “ajkyyy”, dengan yyy merupakan kode kelompok. Terakhir simpan file “htpasswd” nya di /etc/nginx/rahasisakita/


## No 11
>Lalu buat untuk setiap request yang mengandung /its akan di proxy passing menuju halaman [its](https://www.its.ac.id). <b>hint: (proxy_pass)</b>


## No 12
>Selanjutnya LB ini hanya boleh diakses oleh client dengan IP \[Prefix IP].3.69, \[Prefix IP].3.70, \[Prefix IP].4.167, dan \[Prefix IP].4.168. <b>hint: (fixed in dulu clinetnya)</b>


## No 13 dan 14
>13. Karena para petualang kehabisan uang, mereka kembali bekerja untuk mengatur riegel.canyon.yyy.com.<br>
>Semua data yang diperlukan, diatur pada Denken dan harus dapat diakses oleh Frieren, Flamme, dan Fern.
>14. Frieren, Flamme, dan Fern memiliki Riegel Channel sesuai dengan [quest guide berikut](https://github.com/martuafernando/laravel-praktikum-jarkom). Jangan lupa melakukan instalasi PHP8.0 dan Composer
Pada `setup.sh` pada setiap laravel worker:
```
echo nameserver 192.168.122.1 > /etc/resolv.conf
apt-get update
apt-get install mariadb-client -y
apt-get install -y lsb-release ca-certificates apt-transport-https software-properties-common gnupg2
curl -sSLo /usr/share/keyrings/deb.sury.org-php.gpg https://packages.sury.org/php/apt.gpg
sh -c 'echo "deb [signed-by=/usr/share/keyrings/deb.sury.org-php.gpg] https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list'
apt-get update
apt-get install php8.0-mbstring php8.0-xml php8.0-cli php8.0-common php8.0-intl php8.0-opcache php8.0-readline php8.0-mysql php8.0-fpm php8.0-curl unzip wget -y
apt-get install nginx -y
apt-get install git -y
wget https://getcomposer.org/download/2.0.13/composer.phar
chmod +x composer.phar
mv composer.phar /usr/bin/composer
composer -V
cp laravel /etc/nginx/sites-available/
```
Jalankan file `setup.sh` dan jalankan perintah-perintah berikut
```
cd /var/www
git clone https://github.com/martuafernando/laravel-praktikum-jarkom.git
cd /var/www/laravel-praktikum-jarkom
composer update
cd ~
cp after-env.sh /var/www/laravel-praktikum-jarkom/after-env.sh
cd /var/www/laravel-praktikum-jarkom
cp .env.example .env
(( setting .env ))
bash after-env.sh
```
Konfigurasi `after-env.sh`
```
php artisan migrate:fresh
php artisan db:seed --class=AiringsTableSeeder
php artisan key:generate
php artisan jwt:secret
service php8.0-fpm start
service nginx restart
```
Lalu jalankan `after-env.sh` di directory `/var/www/laravel-praktikum-jarkom`
```
ln -s /etc/nginx/sites-available/laravel /etc/nginx/sites-enabled/
chown -R www-data.www-data /var/www/laravel-praktikum-jarkom/storage
```
Dan untuk melihat database di worker, tambahkan script berikut di worker
```
mariadb --host=10.56.2.1 --port=3306 --user=kelompokf09 --password
```

## No 15
>Riegel Channel memiliki beberapa endpoint yang harus ditesting sebanyak 100 request dengan 10 request/second. Tambahkan response dan hasil testing pada grimoire. <b>POST /auth/register</b>

Sebelum memulai nomer 15, 16, dan 17, lakukan instalasi jq terlebih dahulu
```
apt-get install jq
```

Lalu untuk nomor 15 lakukan command berikut dari sisi client `Revolte`
```
ab -n 100 -c 10 -T 'application/json' -p register.json -g register.data http://10.56.4.1:8001/api/auth/register
curl -X POST -H "Content-Type: application/json" -d '{"username": "nauff1", "password": "password1"}' http://10.56.4.2:8002/api/auth/register
```

## No 16
>Riegel Channel memiliki beberapa endpoint yang harus ditesting sebanyak 100 request dengan 10 request/second. Tambahkan response dan hasil testing pada grimoire. <b>POST /auth/login</b>

Setelah install jq di nomor 15, lakukan command berikut dari sisi client `Revolte` juga
```
ab -n 100 -c 10 -T 'application/json' -p login.json -g login.data http://10.56.4.1:8002/api/auth/login
curl -X POST -H "Content-Type: application/json" -d '{"username": "kelompokf09", "password": "passwordf09"}' http://10.56.4.2:8002/api/auth/login
curl -X POST -H "Content-Type: application/json" -d '{"username": "kelompokf09", "password": "passwordf09"}' http://10.56.4.2:8002/api/auth/login | jq -r '.token' > token.txt
```

## No 17
>Riegel Channel memiliki beberapa endpoint yang harus ditesting sebanyak 100 request dengan 10 request/second. Tambahkan response dan hasil testing pada grimoire. <b>GET /me</b>

Lakukan set token secara global
```
token=$(cat token.txt); ab -n 100 -c 10 -H "Authorization: Bearer $token" http://10.56.4.2:8002/api/me
```
Lalu testing dengan perintah berikut
```
token=$(cat token.txt); curl -H "Authorization: Bearer $token" http://10.56.4.2:8002/api/me
```

## No 18
>Untuk memastikan ketiganya bekerja sama secara adil untuk mengatur Riegel Channel maka implementasikan Proxy Bind pada Eisen untuk mengaitkan IP dari Frieren, Flamme, dan Fern.

Implementasi `load balancing` dengan mengonfigurasi `nginx`
```
upstream myweb  {
        server 10.56.4.1:8001;
        server 10.56.4.2:8002;
        server 10.56.4.3:8003;
 }

 server {
        listen 80;
        server_name riegel.canyon.f09.com;

        location / {
        proxy_bind 10.56.2.2;
        proxy_pass http://mynode;
        }
 }


cp lb-laravel /etc/nginx/sites-available/

ln -s /etc/nginx/sites-available/lb-laravel /etc/nginx/sites-enabled/
```

## No 19
>Untuk meningkatkan performa dari Worker, coba implementasikan PHP-FPM pada Frieren, Flamme, dan Fern. Untuk testing kinerja naikkan<br>
>- pm.max_children<br>
>- pm.start_servers<br>
>- pm.min_spare_servers<br>
>- pm.max_spare_servers<br>
>sebanyak tiga percobaan dan lakukan testing sebanyak 100 request dengan 10 request/second kemudian berikan hasil analisisnya pada Grimoire.

Lakukan konfigurasi pada masing-masing worker terhadap proses `package manager` untuk testing
```
user = www-data
group = www-data
listen = /run/php/php8.0-fpm.sock
listen.owner = www-data
listen.group = www-data
php_admin_value[disable_functions] = exec,passthru,shell_exec,system
php_admin_flag[allow_url_fopen] = off

; Choose how the process manager will control the number of child processes.

pm = dynamic
pm.max_children = 5
pm.start_servers = 2
pm.min_spare_servers = 1
pm.max_spare_servers = 3
```
Lalu cek di client dengan script
```
ab -n 100 -c 10 -T 'application/json' -p register.json -g register.data http://riegel.canyon.f09.com/api/auth/register
```

## No 20
>Nampaknya hanya menggunakan PHP-FPM tidak cukup untuk meningkatkan performa dari worker maka implementasikan Least-Conn pada Eisen. Untuk testing kinerja dari worker tersebut dilakukan sebanyak 100 request dengan 10 request/second

Tambahkan `least_conn;` di atas server 192.xxxxxxxx seperti soal php
```
ab -n 100 -c 10 -T 'application/json' -p register.json -g register.data http://riegel.canyon.f09.com/api/auth/register
```

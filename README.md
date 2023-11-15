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


## No 13
>Karena para petualang kehabisan uang, mereka kembali bekerja untuk mengatur riegel.canyon.yyy.com.<br>
>Semua data yang diperlukan, diatur pada Denken dan harus dapat diakses oleh Frieren, Flamme, dan Fern.


## No 14
>Frieren, Flamme, dan Fern memiliki Riegel Channel sesuai dengan [quest guide berikut](https://github.com/martuafernando/laravel-praktikum-jarkom). Jangan lupa melakukan instalasi PHP8.0 dan Composer 


## No 15
>Riegel Channel memiliki beberapa endpoint yang harus ditesting sebanyak 100 request dengan 10 request/second. Tambahkan response dan hasil testing pada grimoire. <b>POST /auth/register</b>


## No 16
>Riegel Channel memiliki beberapa endpoint yang harus ditesting sebanyak 100 request dengan 10 request/second. Tambahkan response dan hasil testing pada grimoire. <b>POST /auth/login</b>


## No 17
>Riegel Channel memiliki beberapa endpoint yang harus ditesting sebanyak 100 request dengan 10 request/second. Tambahkan response dan hasil testing pada grimoire. <b>GET /me</b>


## No 18
>Untuk memastikan ketiganya bekerja sama secara adil untuk mengatur Riegel Channel maka implementasikan Proxy Bind pada Eisen untuk mengaitkan IP dari Frieren, Flamme, dan Fern.


## No 19
>Untuk meningkatkan performa dari Worker, coba implementasikan PHP-FPM pada Frieren, Flamme, dan Fern. Untuk testing kinerja naikkan<br>
>- pm.max_children<br>
>- pm.start_servers<br>
>- pm.min_spare_servers<br>
>- pm.max_spare_servers<br>
>sebanyak tiga percobaan dan lakukan testing sebanyak 100 request dengan 10 request/second kemudian berikan hasil analisisnya pada Grimoire.


## No 20
>Nampaknya hanya menggunakan PHP-FPM tidak cukup untuk meningkatkan performa dari worker maka implementasikan Least-Conn pada Eisen. Untuk testing kinerja dari worker tersebut dilakukan sebanyak 100 request dengan 10 request/second


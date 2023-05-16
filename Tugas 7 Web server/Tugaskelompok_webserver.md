
# Tugas Web Server

**Kelompok 8** 

- Wiman Mahroja  (3121600031)

- Bagus Setiyo Pambudi (3121600034)

- Yazid Rizki Eka Darmawan (3121600060) 





## Installasi Apache2

Web Server yang akan digunakan adalah apache. Sehingga untuk melakukan instalasi menjalankan perintah
```bash
sudo apt install apache2
```
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_Web Server/1.jpg">

Setelah Web Server berhasil diinstall, diperlukan perintah untuk memodifikasi pengaturan firewall untuk mengizinkan akses dari luar ke port web default. Ini dilakukan menggunakan UFW, apabila belum memiliki UFW kita bisa melakukan instalasi terlebih dahulu menggunakan perintah
```bash
sudo apt install ufw
```
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_Web Server/2.jpg">

Selanjutnya, kita melihat list dari ufw application menggunakan perintah
```bash
sudo ufw app list
```
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_Web Server/3.jpg">

Selanjutnya melakukan perintah untuk mengijinkan 'WWW' menggunakan perintah
```bash
sudo ufw allow 'WWW'
```
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_Web Server/4.jpg">

untuk melihat hasilnya enable ufw tersebut dan lihat statusnya, gunakan perintah
```bash
sudo ufw enable
sudo ufw status
```
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_Web Server/5.jpg">

Proses instalasi terakhir adalah melakukan pengecekan terhadap status apache / web server menggunakan perintah
```bash
sudo systemctl status apache2
```
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_Web Server/6.jpg">

Untuk memastikan berjalan, kita membuka server ip kita ke browser seperti chrome, mozilla atau edge. Berikut tampilan ketika web server sudah berjalan

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_Web Server/7.jpg">


## Instalasi PROFTPD
Melakukan instalasi PROFTPD menggunakan perintah
```bash
sudo apt install proftpd -y
```
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_Web Server/8.jpg">

Kemudian menjalankan PROFTPD menggunakan perintah start dan status untuk melihatnya
```bash
systemctl start proftpd
systemctl status proftpd
```
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_Web Server/9.jpg">

## Installasi PHP
Menggunakan perintah
```bash
sudo apt install php
php -v
```
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_Web Server/10.jpg">

## Installasi mysql
Sebelum melakukan instalasi mysql, menambahkan repository mysql dengan cara
```bash
cd tmp
wget https://dev.mysql.com/get/mysql-apt-config_0.8.22-1_all.deb
```
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_Web Server/11.jpg">

Setelah itu, mysql sudah siap untuk diinstal menggunakan dpkg yang berfungsi untuk install, remove dan inspect software packages.
```bash
sudo dpkg -i mysql-apt-config*
```
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_Web Server/12.jpg">

Setelah itu, package siap diinstal menggunakan perintah
```bash
sudo apt install mysql-server
```
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_Web Server/13.jpg">

Dan melakukan pengecekan menggunakan perintah systemctl status
```bash
sudo systemctl status mysql
```
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_Web Server/14.jpg">

Terakhir, menjalankan perintah
```bash
mysqladmin -u root -p version
```
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_Web Server/15.jpg">









































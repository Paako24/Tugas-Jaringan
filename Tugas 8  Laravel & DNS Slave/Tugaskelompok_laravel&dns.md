
# Tugas Laravel & DNS Slave

**Kelompok 8** 

- Wiman Mahroja  (3121600031)

- Bagus Setiyo Pambudi (3121600034)

- Yazid Rizki Eka Darmawan (3121600060) 


## Config DNS Master

Buka konfigurasi zone dns
```bash
sudo nano /etc/bind/named.conf.local
```
tambahkan allow-transfer { 10.252.108.10;}; didalam baris zone forward & reverse

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_Laravel/21.png">

jangan lupa untuk restart service dns master
```bash
sudo systemctl reload named
```

## Config DNS Slave

Buka direktori 
```bash
sudo nano /etc/bind/named.conf.default-zones
```
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_Laravel/22.png">

jangan lupa untuk restart service dns master
```bash
sudo systemctl reload named
```

## Installasi Laravel
Install curl untuk mengirim atau menerima data melalui protokol seperti HTTP, HTTPS, FTP
```bash
sudo apt install curl
```
Gunakan curl command berikut untuk mendownload file Composer
```bash
url -sS https://getcomposer.org/installer | php
```
kemudian pindah composer.phar ke /usr/local/bin/composer
```bash
sudo mv composr.phar /usr/local/bin/composer
```
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_Laravel/16.jpg">

Jalankan perintah berikut untuk menginstall Laravel lewat bantuan Composer dengan folder bernama kelompok8
```bash
composer create-project --prefer-dist laravel/laravel kelompok8
```
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_Laravel/17.jpg">

Jika sudah, lanjutkan dengan perintah di bawah untuk menjalankan laravel dengan host 192.168.8.10 dan prt 800
```bash
php artisan serve --host 192.168.8.10 --port 8000
```
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_Laravel/19.jpg">

Berikut tampilan kerika sudah dijalamkan

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_Laravel/20.jpg">








# Tugas DNS

**Kelompok 8** 

- Wiman Mahroja  (3121600031)

- Bagus Setiyo Pambudi (3121600034)

- Yazid Rizki Eka Darmawan (3121600060) 





## Domain Name Service (DNS)

Domain Name Service (DNS) adalah layanan Internet yang memetakan alamat IP dan nama domain yang memenuhi syarat (FQDN) satu sama lain. Dengan cara ini, DNS mengurangi kebutuhan untuk mengingat alamat IP. Komputer yang menjalankan DNS disebut name servers. Ubuntu dilengkapi dengan BIND (Berkley Internet Naming Daemon), program yang paling umum digunakan untuk mengelola name servers di Linux.

## Instalasi

Install BIND9 dengan menjalankan perintah berikut:

sudo apt install bind 9


## Direktori DNS

Pada menu pilih IP kemudian akan muncul opsi pilih DHCP Server

Direktori DNS
File konfigurasi DNS disimpan dalam direktori dibawah ini:
  /etc/bind : Direktori penyimpanan file konfigurasi DNS
  
  /etc/bind/named.conf : File konfigurasi utama
  
  /etc/bind/named.conf.options : Opsi DNS global
  
  /etc/bind/named.conf.local : Untuk zona user
  
  /etc/bind/named.conf.default-zones : Zona default seperti localhost


## Caching Nameserver

Hapus komentar lalu edit bagian forwarders di /etc/bind/named.conf.options untuk mengatur alamat IP server DNS ISP. Kemudian aktifkan konfigurasi dengan memulai ulang server DNS pada terminal dengan perintah berikut : 

sudo systemctl restart bind9.service

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum3/1.png">


##  Forward Zone File

Edit bagian /etc/bind/named.conf.local untuk menambahkan zona DNS ke BIND9

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum3/2.png">

Buat berkas /etc/bind/db.example.com dengan perintah berikut:

sudo cp /etc/bind/db.local /etc/bind/db.kelompok-08.takehome.com

Dibawah ini adalah Forward Zone File setelah diedit

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum3/3.png">


## Reverse Zone File (IP ke Domain)

Zona Reverse perlu ditambahkan untuk memungkinkan DNS mengubah Alamat IP menjadi nama. Edit bagian /etc/bind/named.conf.local dan tambahkan syntax berikut:

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum3/7.png">

Kemudian buat file /etc/bind/db.192 dengan perintah:

sudo cp /etc/bind/db/127 /etc/bind/db.192

Setelah itu edit /etc/bind/db.192 dengan mengubah opsi yang sama dengan /etc/bind/db.example.com:

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum3/4.png">

## Testing

Langkah pertama dalam menguji BIND9 adalah menambahkan Alamat IP nameserver ke host resolver. Nameserver utama harus dikonfigurasi seperti halnya host lain untuk memeriksa ulang berbagai hal. Buka DNS client untuk mengetahui detail tentang cara menambahkan alamat nameserver ke network client. Edit nameserver dan parameter untuk domain pada file /etc/resolv.conf:

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum3/5.png">

Pada kali ini kelompok kami menggunakan metode ping untuk mengetahui apakah konfigurasi sudah berhasil atau belum.

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum3/6.png">





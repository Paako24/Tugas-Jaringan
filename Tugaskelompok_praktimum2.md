
# Tugas Routing & Hostname

**Kelompok 8** 

- Wiman Mahroja  (3121600031)

- Bagus Setiyo Pambudi (3121600034)

- Yazid Rizki Eka Darmawan (3121600060) 





## Setting IP dan Interface

Untuk setting IP dan interface menggunakan winbox. Winbox sendiri merupakan sebuah aplikasi yang digunakan untuk konfigurasi Mikrotik RouterOS menggunakan GUI. langkah pertama yang dilakukan menjalankan winbox melalui terminal menggunakan perintah wine winbox64.exe
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image3.jpg">

Setelah menjalankan perintah diatas maka akan muncul tampilan seperti gambar dibawah

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image20.jpg">

Kemudian akan muncul tampilan seperti gambar dibawah, Selanjutnya tambahkan ip address pada tanda plus yang diberi panah

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image9.jpg">

Masukkan address 192.168.8.1 dengan Network 192.168.8.0 dan pilih inteface ethernet 2 selanjutnya click Apply, maka IP yang telah dimasukkan akan tampil pada address list

##  Setting Default Gateway 0.0.0.0/0 IP Route Gateway 10.252.108.212

Masukkan Default Gateaway yaitu 0.0.0.0/0

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image19.jpg">

## Setting DHCP Server via DHCP setup [192.168.X.100 - 254]

Pada menu pilih IP kemudian akan muncul opsi pilih DHCP Server

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image21.jpg">

Selanjutnya pada bagian DHCP pilih DHCP Setup seperti pada gambar yang diberi tanda panah, kemudian pilih ethernet2 pada interface, Masukkan Address, dan Gateway serta masukkan range yakni 192.168.8.100 - 192.168.8.254

Masukkan Gateway

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image13.jpg">

Masukkan Range  antara 192.168.8.100 - 192.168.8.254

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image16.jpg">

Masukkan DNS Server

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image18.jpg">

## Sambungkan PC/Laptop ke jaringan, Check IP Address Pastikan IP Address dari PC mendapatkan IP Address dan DHCP server

Hasil cek Ip address di windows 

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image2.jpg">


##  Power Up, Nyalakan PC VM anda pastikan konfigurasi BRIDGE, Pastikan mendapatkan IP Address dari DHCP Server

Pada VM pergi ke settings kemudian pada network bagian attached to pilih Bridged Adapter

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image15.png">

## Konfigurasi IP VM menjadi static, IP: 192.168.X.10

Untuk mengkonfigurasi, buka menu pengaturan lalu pilih Network

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image7.png">

Masuk ke pengaturan wired

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image5.png">

Selanjutnya pilih IPv4 lalu pilih manual dan isikan Address, Netmask, dan Gateway.

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image8.jpg">

Pada tab details centang Connect automatically dan Make available for other users

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image6.jpg">

## Konfigurasi NTP ke 0.id.pool.ntp.org, 1.id.pool.ntp.org

1. Set Up Timezone

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image23.jpg">

2. Aktifkan klien NTP dan buka file timesyncd.conf


<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image12.jpg">

3. Tambahkan NTP=0. id.pool.ntp.org 1.id.pool.ntp.org lalu simpan


<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image17.jpg">

4. Jalankan systemctl restart untuk merestart sinkronisasi waktu dan jalankan systemctl status untuk mengkonfirmasi apakah NTP service telah aktif


<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image4.jpg">

5. Hasil cek pengaturan waktu dan tanggal

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image11.jpg">

## Konfigurasi Sudo

1. Masuk ke root dan install sudo

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image22.jpg">

2. Masuk ke nano /etc/sudoers lalu tambahkan kalimat yang berwarna putih, tekan save dan exit maka konfigurasi dapat digunakan

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image17.jpg">

## Konfigurasi Sudo

1. Buka file hostname

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image14.jpg">

2. Masukkan server10.kelompok8.takehome.com

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugaskelompok_praktikum2/image10.jpg">




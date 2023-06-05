
# Tugas Mail Server

**Kelompok 8** 

- Wiman Mahroja  (3121600031)

- Bagus Setiyo Pambudi (3121600034)

- Yazid Rizki Eka Darmawan (3121600060) 


## Konfigurasi Postfix dan Dovecot

Sebelum memulai install mail server, ada baiknya siapkan domain khusus yang akan digunakan untuk konfigurasi mail server. Dalam contoh konfigurasi kali ini akan menggunakan nama domain mail.kampus-02.takehome.com yang dibuat menggunakan bind9 secara lokal.

1.Update repository dan install package postfix. 
```bash
apt update
apt install postfix dovecot-imapd dovecot-pop3d
```
2.Konfigurasi Postfix

Setelah installasi selesai akan muncul message box, kemudian pilih internet site agar komunikasi email menggunakan protokol SMTP secara langsung.

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_mail/2.png">

Selanjutnya masukkan nama domain yang akan digunakan.

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_mail/3.png">

Setelah itu, postfix akan menyelesaikan installasinya. Setelah Installasi selesai, edit file di /etc/postfix/main.cf dan tambahkan home_mailbox = Maildir/ pada baris paling bawah.

```bash
sudo nano /etc/postfix/main.cf
```

```bash
inet_interfaces = all
inet_protocols = all

#tambahkan baris berikut pada baris paling bawah
home_mailbox = Maildir/
```

buat mail directory di directory /etc/skel

```bash
maildirmake.dovecot /etc/skel/Maildir
```

Setelah itu masukkan perintah berikut

```bash
dpkg-reconfigure postfix
```

Pilih beberapa pilihan dan isikan beberapa input yang akan muncul, sesuaikan dengan topology/konfigurasi sistem dan kebutuhan.

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_mail/5.png">
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_mail/6.png">
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_mail/7.png">
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_mail/8.png">
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_mail/9.png">
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_mail/10.png">
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_mail/11.png">
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_mail/12.png">
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_mail/13.png">

Restart postfix service.

```bash
systemctl restart postfix
```

3.Konfigurasi Dovecot
Edit file konfigurasi /etc/dovecot/dovecot.conf.

```bash
systemctl restart postfix
```

Uncomment dan edit baris berikut.

```bash
...
# If you want to specify non-default ports or anything more complex,
# edit conf.d/master.conf.
listen = *
...
```

Edit file konfigurasi /etc/dovecot/conf.d/10-auth.conf.

```bash
sudo nano /etc/dovecot/conf.d/10-auth.conf
```

Uncomment dan ganti dari yes ke no.

```bash
...
# connection is considered secure and plaintext authentication is allowed.
# See also ssl=required setting.
disable_plaintext_auth = no
...
```

Edit file konfigurasi /etc/dovecot/conf.d/10-mail.conf.

```bash
sudo nano /etc/dovecot/conf.d/10-mail.conf
```

Uncomment pada baris berikut

```bash
...
mail_location = maildir:~/Maildir
...
```

Beri comment pada baris berikut.

```bash
...
# mail_location = mbox:~/mail:INBOX=/var/mail/%u
...
```

Restart dovecot service.

```bash
systemctl restart dovecot
```


## Konfigurasi RoundCube

1. Install Mariadb dan Roundcube
Install roundcube sebagai webmail yang akan digunakan oleh client, dan package mariadb yang nantinya akan digunakan sebagai database dari roundcube.

```bash
apt install mariadb-server roundcube
```

Pilih yes untuk membuat database secara otomatis oleh roundcube.

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_mail/19.png">

Masukkan password database roundcube.

<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_mail/20.png">
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_mail/21.png">

Edit file /etc/roundcube/config.inc.php.

```bash
sudo nano /etc/roundcube/config.inc.php
```

Isikan default host dengan nama domain mail server.
```bash
...
// For example %n = mail.domain.tld, %t = domain.tld
$config['default_host'] = 'mail.kampus-02.takehome.com';
...
```

Ganti smtp server dengan nama domain mail server.
```bash
...
// For example %n = mail.domain.tld, %t = domain.tld
$config['smtp_server'] = 'mail.kampus-02.takehome.com';
...
```

Ganti smtp port dari 587 ke 25.
```bash
...
// SMTP port. Use 25 for cleartext, 465 for Implicit TLS, or 587 for STARTTLS (default)
$config['smtp_port'] = 25;
...
```

Kosongkan value dari smtp user.
```bash
...
// will use the current username for login
$config['smtp_user'] = '';
...
```

Kosongkan value dari smtp password
```bash
....
// will use the current user's password for login
$config['smtp_pass'] = '';
...
```

Configure ulang roundcube (langkah ini bisa dilewati).

```bash
dpkg-reconfigure roundcube-core
```

Kosongkan karena kita tidak menggunakan tls.
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_mail/27.png">

Pilih bahasa untuk roundcube.
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_mail/28.png">

Pilih no jika tidak ingin reinstall database yang telah dibuat.
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_mail/30.png">

Check pada pilihan apache dan uncheck lighttpd.
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_mail/31.png">

Pilih yes untuk merestart web server.
<img src="https://github.com/Xkonz/Tugas-Jaringan/blob/main/pic/Tugas_mail/32.png">

Edit apache config untuk memasukkan konfigurasi tambahan dari roundcube ke apache config.
```bash
dpkg-reconfigure roundcube-core
```

Tambahkan pada baris paling bawah.
```bash
Include /etc/roundcube/apache.conf
```

Selanjutnya, masuk ke directory website apache dan tambahkan file baru untuk mail server.
```bash
cd /etc/apache2/sites-available
touch mail.conf
nano mail.conf
```
```bash
<VirtualHost *:80>
ServerName mail.kampus-02.takehome.com
DocumentRoot /usr/share/roundcube
</VirtualHost>
```

Disable apache default config dan enable kan mail config.
```bash
a2dissite 000-default.conf
a2ensite mail.conf
```

Restart apache service.
```bash
sudo systemctl restart apache2
```








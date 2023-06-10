# UAP_Adsis


1. Buat direktori dengan nama UAP-Adsis, isi dengan file txt dengan format penamaan catatannya-<nama kamu>.txt, kemudian isi file txt tersebut dengan nama dan NIM kamu. Kemudian atur permission view-only pada file tersebut untuk user biasa. Tunjukkan bukti berupa screenshot yang menunjukkan bahwa file tersebut berhasil diatur permissionnya menjadi view-only untuk user biasa.
  
  **Screenshot :**
  <p align="center">
  <img src="https://github.com/garr007/UAP_Adsis/blob/main/Images/Aspose.Words.f39e40ac-573f-4559-b2e7-d24427e0ee76.001.png" >
</p>


![](https://github.com/garr007/UAP_Adsis/blob/main/Images/Aspose.Words.f39e40ac-573f-4559-b2e7-d24427e0ee76.001.png?raw=true)

Gambar 1.1

![](images/Aspose.Words.f39e40ac-573f-4559-b2e7-d24427e0ee76.002.png)

\

Gambar 1.2

![](images/Aspose.Words.f39e40ac-573f-4559-b2e7-d24427e0ee76.003.png)

Gambar 1.3

**Penjelasan :**

Pada Gambar 1.1 menggunakan perintah mkdir untuk membuat directory baru dan isi dengan file txt dengan format penamaan catatannya-tegar.txt, kemudian isi file txt tersebut dengan nama dan NIM saya seperti pada gambar 1.2. Kemudian mengatur permission view-only pada file tersebut untuk user biasa menggunakan perintah chmod 400 catatannya-harsya.txt dan untuk melihat apakah sudah benar permission file tersebut sesuai dengan perintah soal, maka kita gunakan ls -l catatannya harsya.txt. Dapat dilihat permission nya telah berubah menjadi read only.


2. Lakukan konfigurasi alamat IP address sementara pada sistem dan default gateway. (petunjuk 192.168.56.x | x adalah nomor absen)

Nomor Absen saya 1


![](images/Aspose.Words.f39e40ac-573f-4559-b2e7-d24427e0ee76.004.png)**Screenshot :**

Gambar 2.1

![](images/Aspose.Words.f39e40ac-573f-4559-b2e7-d24427e0ee76.005.png)

Gambar 2.2

![](images/Aspose.Words.f39e40ac-573f-4559-b2e7-d24427e0ee76.006.png)

Gambar 2.3


**Penjelasan :**

Pada gambar 2.1 dapat dilihat IP saya awalnya 192.168.188.132 pada antarmuka jaringan “ens33” lalu dengan menjalankan perintah ifconfig “ens33” 192.168.56.1 netmask 255.255.255.0 up yang artinya kita akan mengganti alamat ip dari antarmuka jaringan “ens33” menjadi 192.168.56.1 dengan netmask 255.255.255.0 seperti pada gambar 2.2.

Dapat dilihat juga pada gambar 2.2 untuk mengkonfigurasi default gateway kita perlu menjalankan perintah sudo route add default gw 192.168.56.1 ens 33 yang mana kita akan mengganti default gateway dari antarmuka jaringan “ens33” menjadi 192.168.56.1. Kita dapat melakukan ping ke alamat ip baru jika ingin mengecek apakah ip berfungsi seperti gambar 2.3


3. Lakukan Instalasi Webmin lalu buatlah user bernama nama anda, lalu buat group Adsis\_(kelas masing-masing) dan masukkan nama anda di group

**ScreenShot :**

![](images/Aspose.Words.f39e40ac-573f-4559-b2e7-d24427e0ee76.007.png)

Gambar 3.1

![](images/Aspose.Words.f39e40ac-573f-4559-b2e7-d24427e0ee76.008.png)

Gambar 3.2

![](images/Aspose.Words.f39e40ac-573f-4559-b2e7-d24427e0ee76.009.png)Gambar 3.3


**Penjelasan :**

Karena saya sudah menginstall Webmin jadi bisa langsung membukanya di browser dengan “alamat IP”:10000 dan melakukan login.Setelah berhasil login lihat dipojok kiri dan klik pilihan system dan cari users and groups.Setelah itu klik tombol create group maka akan muncul tampilan seperti gambar 3.1 dengan group yang akan dibuat diberi nama dengan nama “Adsis-E”.

Lalu kita juga dapat membuat user baru dengan menekan tombol create user seperti gambar 3.2 disini saya membuat user dengan nama tegar dan memasukkan ke group yang Adsis-E yang telah dibuat.

Dapat dilihat pada gambar 3.3 ada user dengan nama tegar dengan groupnya adalah Adsis-E yang artinya telah berhasil memasukkan user tegar kedalam group Adsis-E

1. Lakukan ping ke alamat ip anda dan coba lakukan reject dan drop di webmin, lalu analisis apa yang terjadi?

![](images/Aspose.Words.f39e40ac-573f-4559-b2e7-d24427e0ee76.010.png)**Screenshot :**

Gambar 4.1

`	`**![](images/Aspose.Words.f39e40ac-573f-4559-b2e7-d24427e0ee76.011.png)**

Gambar 4.2

![](images/Aspose.Words.f39e40ac-573f-4559-b2e7-d24427e0ee76.012.png)

Gambar 4.3



**Penjelasan :**

Pertama-tama pilih menu networking dan pilih linux firewall lalu tekan tombol add rule dan lakukan konfigurasi seperti gambar 4.2 maka jika kita melakukan ping 192.168.56.1 tidak akan muncul apa-apa karena penolakan drop artinya sistem tidak mengirimkan respons apa pun ke pengirim paket. Dalam hal ini, pengirim tidak menerima tanda-tanda bahwa paket telah ditolak sistem.


5. Buatlah perintah otomatis yang berfungsi untuk ping [www.filkom.ub.ac.id](http://www.filkom.ub.ac.id/)

**Screenshot :**

![](images/Aspose.Words.f39e40ac-573f-4559-b2e7-d24427e0ee76.013.png)

Gambar 5.1

![](images/Aspose.Words.f39e40ac-573f-4559-b2e7-d24427e0ee76.014.png)

Gambar 5.2

**Penjelasan :**

Untuk membuat printah otomatis kita harus menjalankan perintah sudo crontab -e untuk mengakses dan mengedit crontab system.Lalu menambahkan perintah konfigurasi sepergi gambar 5.1 lalu save dan keluar.Dengan menjalankan perintah ps -aux | grep ping kita dapat melihat bahwa setiap 2 menit system akan meng-ping ke filkom.ub.ac.id seperti pada gambar 5.2

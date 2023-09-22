# Jarkom-Modul-1-E21-2023
Laporan Resmi Praktikum Jaringan Komputer Modul 1

## Nama Anggota:
- [Yoel Mountanus Sitorus](https://github.com/zemetia) - 5025211078
- [Java Kanaya Prada](https://github.com/javakanaya) - 5025211112

## Soal

### Soal 1
User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah mengunggah suatu file.

**Penyelesaian:**

Pertama melakukan filter untuk mendapatkan paket data yang menggunakan protokol FTP dengan kueri filter ```ftp```, berikutinya mencari paket data yang menggunakan perintah STOR, yaitu perintah yang digunakan untuk mengunggah suatu file, didapatkan yaitu nomor paket 147. Lalu untuk mendapatkan sequence number (raw) dan acknowledge number (raw), dengan meng-klik paket tersebut, dan pada bagian kiri bawah, membuka _dropdown_ Transmission Control Protocol, pada bagian kiri bawah.

![1a](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/2222cb16-2ee2-4163-83c3-fafc6b709b89)

Berikutnya, yaitu mendapatkan respon dari aktivitas tersebut. Kita melihat melalui wireshark (paket 147, kolom info) bahwa file yang diunggah adalah file _.zip_, Maka pada kita perlu mencari paket data yang juga mengandung file _.zip_ tersebut. Karena merupakan respon, maka paket tersebut berada setelah dari paket 147, dan ternyata paket tersebut bersebelahan dengan paket 147. Lalu untuk mendapatkan sequence number (raw) dan acknowledge number (raw), sama seperti pada langkah sebelumnya.

![1b](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/b238a51e-7c46-4486-bbd4-6216783db273)

- Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut? 

    **Jawab:** 258040667
    
- Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut? 

    **Jawab:** 1044861039

- Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?

    **Jawab:** 1044861039

- Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?
  
    **Jawab:** 258040696

![1c](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/5ca8b91b-a7cc-43ee-a7d9-0492b9dbbd83)

### Soal 2
Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!

**Penyelesaian:**

Pertama melakukan filter untuk mendapatkan paket yang memiliki alamat IP portal praktikum, ```10.21.78.111```, menggunakan kueri filter ```ip.addr == 10.21.78.111```.

![2a](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/88a3746c-04c7-4606-81e7-34c926079d58)

Kemudian pilih, salah satu paket, disini kami memilih paket dengan protokol HTTP, klik-kanan lalu pilih follow, lalu klik HTTP Stream. Lalu akan muncul tampilan jendela baru, dan detail web server yang digunakan pada portal praktikum akan muncul pada bagian berikut:

![2b](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/5b2b3c99-9135-4d5c-9408-dc0ff17cca5a)

**Jawab:** ___Gunicorn___

### Soal 3
Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:

- Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702?

   **Penyelesaian:**

   Pertama kita mencari paket dengan IP Source/destination 239.255.255.250, menggunakan kueri filter ```ip.src == 239.255.255.250 || ip.dst == 239.255.255.250```. Dari hasil yang didapat kita mencari paket dengan port 3702, dan terlihat bahwa protokolnya adalah protokol ___UDP___.
  
   ![3a](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/f4d90462-c700-4e1c-8dea-dc000f9b73ac)

   Kemudian, karena telah mengetahui protokol yang digunakan, kita memperbarui kueri filter kita menjadi seperti berikut ```(ip.src == 239.255.255.250 && udp.srcport == 3702) || (ip.dst = 239.255.255.250 && up.dstport == 3702)```

   ![3b](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/f31ee309-dc16-4c98-8075-db1426cdb202)

   Hasil filter tersebut merupakan paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702, dan jumlah paket tersebut adalah 21
  
   **Jawab:** 21

- Protokol layer transport apa yang digunakan?

   **Penyelesaian:**

  Didapatkan dari langkah sebelumnya, protokolnya yaitu ___UDP___

   **Jawab:** UDP
  
![3c](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/01495586-ff4f-4357-95c8-27bb02c5063a)

### Soal 4
Berapa nilai checksum yang didapat dari header pada paket nomor 130?

**Jawab:**

### Soal 5
Elshe menemukan suatu file packet capture yang menarik. Bantulah Elshe untuk menganalisis file packet capture tersebut.

- Berapa banyak packet yang berhasil di capture dari file pcap tersebut?

    **Jawab:**

- Port berapakah pada server yang digunakan untuk service SMTP?

    **Jawab:**

- Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP?

    **Jawab:**

### Soal 6
Seorang anak bernama Udin Berteman dengan SlameT yang merupakan seorang penggemar film detektif. sebagai teman yang baik, Ia selalu mengajak slamet untuk bermain valoranT bersama. suatu malam, terjadi sebuah hal yang tak terdUga. ketika udin mereka membuka game tersebut, laptop udin menunjukkan sebuah field text dan Sebuah kode Invalid bertuliskan "server SOURCE ADDRESS 7812 is invalid". ketika ditelusuri di google, hasil pencarian hanya menampilkan a1 e5 u21. jiwa detektif slamet pun bergejolak. bantulah udin dan slamet untuk menemukan solusi kode error tersebut.

**Jawab:**

### Soal 7
Berapa jumlah packet yang menuju IP 184.87.193.88?

**Jawab:**

### Soal 8
Berikan kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80! (Jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad)

**Jawab:**

### Soal 9
Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34!

**Jawab:**

### Soal 10
Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet

**Jawab:**

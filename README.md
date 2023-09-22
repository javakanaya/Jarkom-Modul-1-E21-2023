# Jarkom-Modul-1-E21-2023

Laporan Resmi Praktikum Jaringan Komputer Modul 1

## Nama Anggota:

- [Yoel Mountanus Sitorus](https://github.com/zemetia) - 5025211078
- [Java Kanaya Prada](https://github.com/javakanaya) - 5025211112

## Soal

### Soal 1

User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah mengunggah suatu file.

**Penyelesaian:**

Pertama melakukan filter untuk mendapatkan paket data yang menggunakan protokol FTP dengan kueri filter `ftp`, berikutinya mencari paket data yang menggunakan perintah STOR, yaitu perintah yang digunakan untuk mengunggah suatu file, didapatkan yaitu nomor paket 147. Lalu untuk mendapatkan sequence number (raw) dan acknowledge number (raw), dengan meng-klik paket tersebut, dan pada bagian kiri bawah, membuka _dropdown_ Transmission Control Protocol, pada bagian kiri bawah.

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

Pertama melakukan filter untuk mendapatkan paket yang memiliki alamat IP portal praktikum, `10.21.78.111`, menggunakan kueri filter `ip.addr == 10.21.78.111`.

![2a](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/88a3746c-04c7-4606-81e7-34c926079d58)

Kemudian pilih, salah satu paket, disini kami memilih paket dengan protokol HTTP, klik-kanan lalu pilih follow, lalu klik HTTP Stream. Lalu akan muncul tampilan jendela baru, dan detail web server yang digunakan pada portal praktikum akan muncul pada bagian berikut:

![2b](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/5b2b3c99-9135-4d5c-9408-dc0ff17cca5a)

**Jawab:** **_Gunicorn_**

### Soal 3

Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:

- Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702?

  **Penyelesaian:**

  Pertama kita mencari paket dengan IP Source/destination 239.255.255.250, menggunakan kueri filter `ip.src == 239.255.255.250 || ip.dst == 239.255.255.250`. Dari hasil yang didapat kita mencari paket dengan port 3702, dan terlihat bahwa protokolnya adalah protokol **_UDP_**.

  ![3a](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/f4d90462-c700-4e1c-8dea-dc000f9b73ac)

  Kemudian, karena telah mengetahui protokol yang digunakan, kita memperbarui kueri filter kita menjadi seperti berikut `(ip.src == 239.255.255.250 && udp.srcport == 3702) || (ip.dst = 239.255.255.250 && up.dstport == 3702)`

  ![3b](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/f31ee309-dc16-4c98-8075-db1426cdb202)

  Hasil filter tersebut merupakan paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702, dan jumlah paket tersebut adalah 21

  **Jawab:** 21

- Protokol layer transport apa yang digunakan?

  **Penyelesaian:**

  Didapatkan dari langkah sebelumnya, protokolnya yaitu **_UDP_**

  **Jawab:** UDP

![3c](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/01495586-ff4f-4357-95c8-27bb02c5063a)

### Soal 4

Berapa nilai checksum yang didapat dari header pada paket nomor 130?

**Penyelesaian:**

Sesuai Perintah soal, yaitu menuju ke paket nomor 130. Lalu diklik, dan pada dropdown _User Datagram Protocol_ akan terdapat nilai Checksum

![4](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/a09f4cd5-1284-4764-8755-d31bc7d8e712)

**Jawab:** 0x18e5

### Soal 5

Elshe menemukan suatu file packet capture yang menarik. Bantulah Elshe untuk menganalisis file packet capture tersebut.

**Penyelesaian:**

Sebelumnya saya sudah mencoba mencari-cari mana yang aneh tapi ga dapet dapet eh tau nya malah salah pcap (Saddd mbakk sadddd). \
Saat Pcap yang baru sudah di update Aneh nya itu langsung ada didepan mata. Saya coba Follow salah satu dari beberapa SMTP yang aneh tersebut. Lalu ketika di scroll kita dapat langsung menemukan sebuah pesan yang berisikan password untuk zip dalam bentuk base64 encrypted message. Setelah itu kita decode passwordnya dengan online base64 decoder lalu memasukkan password tersebut dalam zip filenya

![5a](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/75ea640e-b59d-4070-9fc9-25c240f98850)

![5b](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/49cb7e80-5383-4c1e-a6db-edc535d736a0)

![5c](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/489bb932-3789-4c56-ad00-d35d305240eb)

Setelah password dimasukkan ternyata didalam text file terdapat IP netcut untuk soalnya dan untuk mendapatkan Flagnya.

![5d](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/0cba4f8f-fab1-4ae1-9dfe-1a73645c5dc5)

- Berapa banyak packet yang berhasil di capture dari file pcap tersebut?

  ![5f](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/5405ec6e-6191-4077-ae57-beb791e26122)

  **Jawab: 60**

- Port berapakah pada server yang digunakan untuk service SMTP?

  ![5g](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/0ab6a0ff-378f-493b-a670-d395e82c44b2)

  **Jawab: 25**

- Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP?

  ![5h](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/5865f0b9-b8e3-4785-8f02-51773403899c)

  **Jawab: 74.53.140.153**

![5e](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/8683ed13-8650-4ba2-909c-ae250fc5ebe8)

### Soal 6

Seorang anak bernama Udin Berteman dengan SlameT yang merupakan seorang penggemar film detektif. sebagai teman yang baik, Ia selalu mengajak slamet untuk bermain valoranT bersama. suatu malam, terjadi sebuah hal yang tak terdUga. ketika udin mereka membuka game tersebut, laptop udin menunjukkan sebuah field text dan Sebuah kode Invalid bertuliskan "server SOURCE ADDRESS 7812 is invalid". ketika ditelusuri di google, hasil pencarian hanya menampilkan a1 e5 u21. jiwa detektif slamet pun bergejolak. bantulah udin dan slamet untuk menemukan solusi kode error tersebut.

**Penyelesaian:**

Terdapat huruf kapital yang cukup `sus` pada soal. Dan jika huruf-huruf kapital tersebut disatukan akan membentuk sebuah kata perintah `S U B T I T U S I SERVER ADDRESS`. Setelah kata `SERVER ADDRESS` ada angka 7812 yang kemungkinan besar menunjukkan nomor sebuah paket dari pcap yang tersedia. \
Dari perintah tersebut kita diminta untuk menSubtitusikan Server Address (Alamat IP) dari paket no. 7812 tersebut dengan chiper pada clue selanjutnya yaitu `a1 e5 u21` atau simplenya nama chiper ini adalah chiper `a1z26`

![Alt text](image.png)

Dari gambar diatas kita dapat bahwa IP address dari paket nomor 7812 adalah `104.18.14.101`. Sesuai dengan ketentuan dari chiper a1z26 maka tidak mungkin angka tersebut lebih dari 26. semua angka dari IP paket tersebut akan digabungkan tetapi harus tetap lebih kecil sama dengan 26.

```
10 (J)
4  (D)
18 (R)
14 (N)
10 (J)
1  (A)
```

Maka kita mendapat jawabannya yaitu JDRNJA

**Jawab: JDRNJA**

### Soal 7

Berapa jumlah packet yang menuju IP 184.87.193.88?

**Penyelesaian:**

Lakukan filter untuk mendapatkan paket yang menuju ke IP tersebut, dengan menggunakan kueri filter berikut `ip.src == 184.87.193.88`. Terlihat hanya terdapat 6 paket yang menuju ke IP tersebut.

![7](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/87474722/38ecfb66-ae57-4d1e-b34b-65faf867bf86)

**Jawab:** 6

### Soal 8

Berikan kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80! (Jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad)

**Jawab:**

### Soal 9

Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34!

**Penyelesaian:**

Kita menggunakan `ip.src == 10.51.40.1` untuk mendapatkan paket yang berasal dari alamat tersebut. dan `ip.dst != 10.39.55.34` untuk mendapatkan paket yang tidak menuju ke alamat tersebut. Keduanya digabungkan dengan operator logika `&&` yang berarti kedua kondisi harus terpenuhi, maka hasil filter akan menampilkan paket-paket yang berasal dari alamat `10.51.40.1` dan tidak menuju ke alamat `10.39.55.34`.

**Jawab:** `ip.src == 10.51.40.1 && ip.dst != 10.39.55.34`

### Soal 10

Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet

**Penyelesaian:**

Lakukan display filter hanya untuk paket yang menggunakan protocol "Telnet" dengan sesimple mengetik "telnet" pada display filter bar.

![image](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/27951856/35d4a993-e5ac-4c2b-8fdd-2ee0f53d8229)

Pada paket-paket telnet tersebut ada banyak percobaan untuk login tetapi kita hanya ingin mencari paket yang mengindikasi sukses Login. Jika paket login berhasil ditemukan kemungkinan paket paket sebelumnya yang berasal dari IP client merupakan paket yang dikirimkan dan berupa kredensial dari user yang tepat dan berhasil login.

![image](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/27951856/e37f522b-a0e3-465e-9ae7-d531c5ec5ed7)

Kita coba lihat 1 paket diatasnya dan ada data berupa text yaitu `kesayangannyak0k0``

![image](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/27951856/da25f7cb-6b23-474f-bd30-ae03e4c22429)

Dan beberapa data diatasnya merupakan 1 char, tetapi char ini memiliki pola yang menarik dan tidak random yang tersebar pada paket yang ada pada screenshot dibawah.

![image](https://github.com/javakanaya/Jarkom-Modul-1-E21-2023/assets/27951856/55f338d2-10e6-48aa-b752-5756ead34e2d)

yang kira kira berisi.

```
d
d
h
h
a
a
f
f
i
i
n
n
```

dengan beberapa paket sebelumnya yang juga ada mengirim user:pass berupa dhafin:kesayangannyak0k0
**Jawab: dhafin:kesayangannyak0k0**

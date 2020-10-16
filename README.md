# Jarkom_Modul1_Lapres_D07
Laporan Resmi Modul 1 Praktikum Jaringan Komputer
#
1. Naufal Adam Kuncoro (05111740000155)
2. Sheinna Yendri (05111840000038)
#
## A. Display Filter
1. [Soal1](#soal1)
2. [Soal2](#soal2)
3. [Soal3](#soal3)
4. [Soal4](#soal4)
5. [Soal5](#soal5)
6. [Soal6](#soal6)
7. [Soal7](#soal7)
8. [Soal8](#soal8)
9. [Soal9](#soal9)
10. [Soal10](#soal10)
## B. Capture Filter
11. [Soal11](#soal11)
12. [Soal12](#soal12)
13. [Soal13](#soal13)
14. [Soal14](#soal14)
15. [Soal15](#soal15)
#

### Soal1
1.	Sebutkan webserver yang digunakan pada "testing.mekanis.me"!
-	Filter menggunakan filter command ```http contains “testing.mekanis.me”```.
-	Kemudian klik kanan, pilih ```Follow > TCP Stream```, dan dapat terlihat bahwa webserver yang digunakan adalah **nginx/1/14/0 (Ubuntu)**, dengan destination port 80 (HTTP).

![image](https://user-images.githubusercontent.com/48936125/95944718-0d957c00-0e13-11eb-9b10-abdc716069ae.png)

![image](https://user-images.githubusercontent.com/48936125/95887559-30d81100-0daa-11eb-822f-78e0a6e2a755.png)

- Dapat lebih spesifik dengan ```http.host == "testing.mekanis.me"```

![image](https://user-images.githubusercontent.com/48936125/96250135-901b6880-0fd8-11eb-8469-6aa331c7ae7c.png)
#

### Soal2
2.	Simpan gambar "Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg"!
-	Pilih ```File > Export Objects > HTTP```.
-	Kemudian pada text filter dituliskan nama file **Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg**.
-	Pilih file tersebut dan langsung Save pada direktori yang diinginkan.
-	Gambar tersimpan dapat terlihat di bawah.

![image](https://user-images.githubusercontent.com/48936125/95887798-78f73380-0daa-11eb-9add-9eec4bb75b88.png)

Gambar **Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg**:
![image](https://user-images.githubusercontent.com/48936125/95887809-7b598d80-0daa-11eb-9ea4-b2607cc26742.png)
#

### Soal3
3.	Cari username dan password ketika login di "ppid.dpr.go.id"!
-	Menggunakan command filter: ```http.host == “ppid.dpr.go.id”```
-	Kemudian mencari di mana Info berisi perintah **POST**, dilihat detail paketnya, dan terlihat username serta password untuk login.
-	Username: **10pemuda**
-	Password: **guncangdunia**

![image](https://user-images.githubusercontent.com/48936125/95887950-aa6fff00-0daa-11eb-96c8-ec42646d5e6d.png)

- Dapat lebih spesifik dengan ```http.host == "ppid.dpr.go.id" && http.request.method == "POST" && http.request.uri contains "login"```

![image](https://user-images.githubusercontent.com/48936125/96250216-b0e3be00-0fd8-11eb-9b6e-ba238972e1bf.png)
#

### Soal4
4.	Temukan paket dari web-web yang menggunakan basic authentication method!
-	Host: ```aku.pengen.pw``` merupakan web yang menggunakan basic authentication method.

![image](https://user-images.githubusercontent.com/48936125/95888181-f6bb3f00-0daa-11eb-8839-c7dd76f6ed8f.png)

- Command seharusnya: ```http.authbasic```

![image](https://user-images.githubusercontent.com/48936125/96250280-ce188c80-0fd8-11eb-9a56-b4b10cc96897.png)
#

### Soal5
5.	Ikuti perintah di aku.pengen.pw! Username dan password bisa didapatkan dari file .pcapng!
- Pertama-tama melakukan filter command ```ip.dst == 157.245.50.224``` yang merupakan IP Address dari host **aku.pengen.pw**.

![5-2](https://user-images.githubusercontent.com/48936125/96234144-3fe5db80-0fc3-11eb-8d01-4e8db99760c7.jpg)

- Kemudian klik paket yang memiliki info ```GET```, dan ditemukan pada bagian ```Credential```, username dan password:
- Username: **kakakgamtenk**
- Password: **hartatahtabermuda**

![5-3](https://user-images.githubusercontent.com/48936125/96234146-41170880-0fc3-11eb-82d0-679f0d742730.jpg)

![5-1](https://user-images.githubusercontent.com/48936125/96234141-3e1c1800-0fc3-11eb-9189-030df777afcb.jpg)
#

### Soal6
6.	Seseorang menyimpan file zip melalui FTP dengan nama "Answer.zip". Simpan dan Buka file "Open This.pdf" di Answer.zip. Untuk mendapatkan password zipnya, temukan dalam file zipkey.txt (passwordnya adalah isi dari file txt tersebut).
- Pertama-tama melakukan filter menggunakan string **Answer.zip**, filter ini dapat ditemukan melalui ```Edit > Find Packets``` kemudian pada filter, pilih opsi ```String```, kemudian klik button ```Find```.

![image](https://user-images.githubusercontent.com/48936125/95888943-fa9b9100-0dab-11eb-8617-47fe19ad78f1.png)

- Setelah itu ditemukan paket yang diinginkan, klik kanan pilih ```Follow > TCP Stream```, kemudian kita pilih menjadi tipe ```Raw``` dan ```Save As``` di mana mengikuti nama dan tipe file sebenarnya yaitu **Answer.zip** pada direktori yang diinginkan.
- Kemudian kami mencoba mengekstrak file zip tersebut. Ternyata file zip tersebut bertipe password protected, di mana berdasarkan soal password tersimpan pada file **zipkey.txt**.

![image](https://user-images.githubusercontent.com/48936125/95888949-fcfdeb00-0dab-11eb-9a69-e8e9859d7a47.png)

- Sehingga hal yang sama kami lakukan untuk mencari paket bernama **zipkey.txt**, kami melakukan filter berdasarkan string tersebut, kemudian ```Follow > TCP Stream```, ```Save As``` dengan tipe ```Raw``` sesuai yang kita inginkan.

![image](https://user-images.githubusercontent.com/48936125/95888958-ff604500-0dab-11eb-83db-d8d64124969d.png)

- Setelah mendapatkan file bertipe ```.txt``` tersebut, kami dapat memasukkan password untuk membuka file zip tadi.

![image](https://user-images.githubusercontent.com/48936125/95888964-01c29f00-0dac-11eb-8137-99dc884ac6d0.png)

- Dan akhirnya dapat membuka file PDF yang diinginkan yaitu **Open This.pdf**.

![image](https://user-images.githubusercontent.com/48936125/95888969-04bd8f80-0dac-11eb-982d-af0eb85948b6.png)

- Command dapat lebih spesifik ```ftp-data.command contains "Answer.zip"``` untuk mencari file ZIP dan melakukan download, serta command ```ftp-data.command contains "zipkey.txt"``` untuk mencari file text password dari file ZIP tadi.

![image](https://user-images.githubusercontent.com/48936125/96251199-4d5a9000-0fda-11eb-80fc-b42bd28826c4.png)

![image](https://user-images.githubusercontent.com/48936125/96251230-59dee880-0fda-11eb-96ed-1a4564f399d1.png)
#

### Soal7
7.	Ada 500 file zip yang disimpan ke FTP Server dengan nama 1.zip, 2.zip, ..., 500.zip. Salah satunya berisi pdf yang berisi puisi. Simpan dan Buka file pdf tersebut.
Your Super Mega Ultra Rare Hint = nama pdf-nya "Yes.pdf"
-	Pertama menggunakan filter command ```tcp contains “Yes.pdf”``` untuk mencari file pdf yang diinginkan.
-	Kemudian untuk download file tersebut, klik kanan, ```Follow > TCP Stream```, kemudian pilih ```Raw``` dan ```Save As```, nama file dituliskan **Yes.zip**.

![image](https://user-images.githubusercontent.com/48936125/95889423-94633e00-0dac-11eb-96e2-9d8789b8db61.png)

-	Kemudian dapat di-unzip dan muncul file **Yes.pdf**, dibuka dan hasil seperti pada screenshot.

![image](https://user-images.githubusercontent.com/48936125/95889427-962d0180-0dac-11eb-9e3b-2f61d34bd3db.png)

- Command dapat lebih spesifik: ```ftp-data contains "Yes.pdf"```.

![image](https://user-images.githubusercontent.com/48936125/96251333-7bd86b00-0fda-11eb-89c9-28a690f0b483.png)
#

### Soal8
8.	Cari objek apa saja yang didownload (RETR) dari koneksi FTP dengan Microsoft FTP Service!
-	Objek yang didownload dari koneksi FTP adalah file **Readme** dan file **text (.txt)**.

![image](https://user-images.githubusercontent.com/48936125/95889626-d42a2580-0dac-11eb-84c9-698ddb49b63f.png)

- Command dapat menjadi lebih spesifik: ```(ftp contains "Microsoft FTP Service" || ftp.request.command contains "RETR") && ip.src == 192.168.0.128```.

![image](https://user-images.githubusercontent.com/48936125/96251379-90b4fe80-0fda-11eb-8345-cb9a42b63f09.png)
#

### Soal9
9.	Cari username dan password ketika login FTP pada localhost!
-	Pertama filter ```ftp``` untuk mendapatkan paket-paket menggunakan protocol FTP.

![image](https://user-images.githubusercontent.com/48936125/95889728-fcb21f80-0dac-11eb-80bd-4018ff92ca20.png)

-	Lalu mencari ```Response : 331```, lalu klik kanan, ```Follow > TCP Stream```.
-	Akan muncul:
1.	Username: **dhana**
2.	Password: **dhana123**

![image](https://user-images.githubusercontent.com/48936125/95889730-ff147980-0dac-11eb-9c6b-dc81b118e34a.png)

- Command dapat menjadi lebih spesifik: ```ftp.request.command == "USER" || ftp.request.command == "PASS"```.

![image](https://user-images.githubusercontent.com/48936125/96251485-bfcb7000-0fda-11eb-8bb4-e5e7aaebe413.png)
#

### Soal10
10.	Cari file .pdf di wireshark lalu download dan buka file tersebut!
clue: "25 50 44 46" 
-	Menggunakan ```Edit > Find Packet```, kemudian memilih filter ```Hex value```, dan masukkan clue ```25 50 44 46```.
-	Ditemukan sebuah file PDF, kemudian klik kanan, ```Follow > TCP Stream```.

![image](https://user-images.githubusercontent.com/48936125/95889955-5581b800-0dad-11eb-8ab5-a91897441124.png)

-	Ubah tipe menjadi ```Raw```, kemudian ```save as``` **file.pdf** (nama bebas, tipe file: PDF). Simpan di direktori yang diinginkan.

![image](https://user-images.githubusercontent.com/48936125/95889961-57e41200-0dad-11eb-9b6b-18ad5fa30846.png)

![image](https://user-images.githubusercontent.com/48936125/95889970-5a466c00-0dad-11eb-90bf-fb3222767ab9.png)

-	Setelah dibuka, file tersebut berupa UU RI, seperti pada screenshot terlampir.

![image](https://user-images.githubusercontent.com/48936125/95889973-5c102f80-0dad-11eb-90ed-3121a67502f8.png)
#

### Soal11
11.	Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!
-	Filter command: ```port 21```.

![image](https://user-images.githubusercontent.com/48936125/95891566-73501c80-0daf-11eb-9f90-76da15e632a1.png)
#

### Soal12
12.	Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!
-	Filter command: ```src port 80```.

![image](https://user-images.githubusercontent.com/48936125/95891907-eeb1ce00-0daf-11eb-9a07-324855f3ee52.png)
#

### Soal13
13.	Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!
-	Filter command: ```dst port 443```.

![image](https://user-images.githubusercontent.com/48936125/95891993-08531580-0db0-11eb-828a-5ec540f2df0b.png)
#

### Soal14
14.	Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!
-	Untuk mencari ip kami, menggunakan command prompt, kemudian mengetikkan command ```ipconfig```. Dari situ, kami temukan bahwa ip kami adalah ```192.168.1.107```.
-	Sehingga untuk mengambil paket yang berasal dari ip kami, menggunakan capture filter: ```ip src 192.168.1.107```.

![image](https://user-images.githubusercontent.com/48936125/96251827-3b2d2180-0fdb-11eb-8011-07af4ba07a57.png)
#

### Soal15
15.	Filter sehingga wireshark hanya mengambil paket yang tujuannya ke monta.if.its.ac.id!
-	Menggunakan capture filter: ```dst host monta.if.its.ac.id```.

![image](https://user-images.githubusercontent.com/48936125/96252023-821b1700-0fdb-11eb-83c6-1eb7a675d2c0.png)
#

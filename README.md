# Jarkom_Modul1_Lapres_T8
### Anggota Kelompok:
1. Kadek Nesya Kurniadewi (05311840000009)
2. Agung Mulyono (05311840000035)


## A. DISPLAY FILTER
### 1.  Sebutkan webserver yang digunakan pada "testing.mekanis.me"!
**Penyelesaian**
- Menggunakan command `http.host == "testing.mekanis.me"`.
#### Jawaban : ***menggunakan server nginx/1.14.0 (Ubuntu)***

![A.1](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/A.1.png)

### 2.  Simpan gambar "Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg"!
**Penyelesaian**
- Menggunakan command `http.host == "ppid.dpr.go.id"`

![A.2.1](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/A.2.1.png)

- Kemudian export object -> HTTP -> Cari file sesuai nama ***Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg*** 

![A.2.2](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/A.2.2.png)

- Save gambar, sehingga akan menampilkan gambar sesuai dengan image dibawah ini :
**Gambar "Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg"**
![gambar](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.png)

### 3.  Cari username dan password ketika login di "ppid.dpr.go.id"!
**Penyelesaian**
- Menggunakan command `http.host == "ppid.dpr.go.id" && http.request.method == "POST"`
![A.3.1](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/A.3.1.png)

- Kemudian cari username dan password pada bagian HTML Form URL encoded seperti gambar dibawah
![A.3.2](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/A.3.2.png)
### 4.  Temukan paket dari web-web yang menggunakan basic authentication method!
**Penyelesaian**
- Untuk mencari web yang menggunakan basic authentication menggunakan command `http.authbasic`
- Dengan tampilan seperti dibawah ini, yang dapat dipastikan dengan melihat keterangan pada body wireshark : ***"Authorization: Basic xxx..."***

![authbasic1](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/authbasic1.png)
![authbasic2](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/authbasic.2.png)

### 5.  Ikuti perintah di aku.pengen.pw! Username dan password bisa didapatkan dari file .pcapng!
**Penyelesaian**
- Untuk bisa login pada web ***aku.pengen.pw*** kita memerlukan ***username dan password***. Dengan menggunakan display filter menggunakan command `http.host == "aku.pengen.pw"`

![A.5.1](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/A.5.1.png)

- Kemudian mencari pada bagian body wireshark pada ***Hypertext Transfer Protocol -> dibawah Authorization dengan nama :CREDETIALS***

![A.5.2](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/A.5.2.png)

- Setelah menemukan username dan password, kemudian buka web "aku.pengen.pw" pada browser kemudian login menggunakan username dan password yang sudah didapatkan, sehingga akan menampilkan page sesuai dengan gambar dibawah ini :

![A.5.3](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/A.5.3.png)

### 6.  Seseorang menyimpan file zip melalui FTP dengan nama "Answer.zip". Simpan dan Buka file "Open This.pdf" di Answer.zip. Untuk mendapatkan password zipnya, temukan dalam file zipkey.txt(passwordnya adalah isi dari file txt tersebut).
**Penyelesaian**
1. Mencari file zip dengan nama ***Answer.zip***
- Disini saya menggunakan Hex Value dari file "zip" ***(1F 9D)*** untuk mencari file tersebut

![A.6.1](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/A.6.1.png)

- Kemudian follow -> TCP Stream -> kemudian save as data dengan ***"RAW"*** kemudian save dengan extensi ***".zip"***

![A.6.2](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/A.6.2.png)

- Buka file .zip kemudian buka file .pdf yang ada di dalam file zip tersebut. Untuk mencari key dari file pdf tersebut, dilanjutkan dengan langkah mencari password zip

![A.6.3](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/A.6.3.png)

2. Mencari password zip dengan nama file ***zipkey.txt***
- Mencari file .txt yang berisi password mengunakan ***"Regullar Expression"*** dengan kata kunci ***zipkey***
- Kemudian melakukan follow -> TCP Stream pada header dengan info ***FTP Data: 15 bytes (PASV) (STOR zipkey.txt)***, sehingga key dapat ditemukan pada TCP Stream

![A.6.4](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/A.6.4.png)

![A.6.5](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/A.6.5.png)

### 7. Ada 500 file zip yang disimpan ke FTP Server dengan nama 1.zip, 2.zip, ..., 500.zip. Salah satunya berisi pdf yang berisi puisi. Simpan dan Buka file pdf tersebut. Your Super Mega Ultra Rare Hint = nama pdf-nya "Yes.pdf"
**Penyelesaian**
- Sebelum mencari file "Yes.pdf", saya melakukan convert dari TEXT to HEX VALUE sehingga menghasilkan HEX VALUE dari "Yes.pdf" adalah 59 65 73 2e 70 64 66

![A.7.1](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/A.7.1.png)

- Setelah menemukan file tersebut, lakukan TCP Stream kemudian save as "RAW" dan save dengan extensi ".zip"

![yespdf](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/yespdf.png)

- Export file pdf tersebut, kemudian buka file pdf dan akan menampilkan seperti gambar dibawah ini :

![isiyespdf](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/isiyespdf.png)

### 8. Cari objek apa saja yang didownload (RETR) dari koneksi FTP dengan Microsoft FTP Service!
**Penyelesaian**
- Mencari IP Addres dari Microsoft FTP Service dengan menggunakan "find" -> "Regular Expression", sehingga menemukan IP Addressnya yaitu : 198.246.117.106
- Kemudian mencari FTP Request Command RETR dengan menggunakan command `ftp.request.command == "RETR"`
- IP Destination yang menggunakan IP diatas (Microsoft FTP Service) adalah hasil yang paling atas yang menunjukkan ***melakukan dowload/RETR Readme***

![A.8.1](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/A.8.1.png)
![A.8.2](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/A.8.2.png)
### 9. Cari username dan password ketika login FTP pada localhost!
**Penyelesaian**
- Menggunakan command `ftp.request.command == "USER" || ftp.request.command == "PASS"`
![A.9.1](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/A.9.1.png)

- Hasilnya seperti gambar dibawah
![A.9.2](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/A.9.2.png)
### 10. Cari file .pdf di wireshark lalu download dan buka file tersebut! clue: "25 50 44 46" 
**Penyelesaian**
- Disini saya menggunakan hex value dari clue yaitu: ***25 50 44 46***

![A.10.1](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/A.10.1.png)

- Kemudian ***klik kanan*** pada paket yang sudah ditemukan lalu pilih ***follow -> tcp stream***
![A.10.2](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/A.10.2.png)
![A.10.3](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/A.10.3.png)

- Kemudian ubah data kedalam bentuk ***raw*** lalu simpan file tersebut dengan ekstensi ***.pdf***
![A.10.4](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/A.10.4.png)

## B. CAPTURE FILTER
### 11. Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!
**Penyelesaian**
- Menggunakan command `port 21` pada bagian capture filter

![B.11.1](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/B.11.1.png)
![B.11.2](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/B.11.2.png)
### 12. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!
**Penyelesaian**
- Menggunakan command `src port 80` pada bagian capture filter

![B.12.1](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/B.12.1.png)

![B.12.2](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/B.12.2.png)
### 13. Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!
**Penyelesaian**
- Untuk Display Filter menggunakan command `tcp.dstport == 443`

![B.13.1](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/B.13.1.png)

![B.13.2](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/B.13.2.png)

- Untuk Capture Filter menggunakan command `dst port 443`

![B.13.3](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/B.13.3.png)

![B.13.4](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/B.13.4.png)

### 14. Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!
**Penyelesaian**
- Menggunakan command `src net IPyangdimiliki`

![B.14.1](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/B.14.1.png)
![B.14.2](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/B.14.2.png)
### 15. Filter sehingga wireshark hanya mengambil paket yang tujuannya ke monta.if.its.ac.id!
**Penyelesaian**
- Menggunakan command `dst host monta.if.its.ac.id`

![B.15.1](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/B.15.1.png)
![B.15.2](https://github.com/agung56/Jarkom_Modul1_Lapres_T8/blob/main/img/B.15.2.png)

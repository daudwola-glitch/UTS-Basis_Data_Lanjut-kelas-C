# UTS-Basis_Data_Lanjut-kelas-C

<img width="768" height="274" alt="image" src="https://github.com/user-attachments/assets/4330396f-b51b-4eef-bde7-dee292bc782b" />

* Nama : Daud Gollu Wola 
* NIM : 2501010343 
* Kelas : Basis Data Lanjut

# A. Deskripsi Database
Database yang dibuat bernama db_game_rpg dengan tema game RPG (role playing game) sederhana. Dalam game ini, seorang pemain dapat membuat beberapa karakter dengan kelas yang berbeda, membeli dan menyimpan item, serta mengambil quest untuk mendapatkan hadiah. Database dibuat menggunakan MySQL dan terdiri dari 7 tabel yang saling berelasi.

# B. Relasi Antar Tabel
1. Tabel pemain ke karakter berelasi one to many, karena satu pemain dapat memiliki banyak karakter.
2. Tabel kelas ke karakter berelasi one to many, karena satu kelas dapat dipakai oleh banyak karakter.
3. Tabel karakter dan item berelasi many to many melalui tabel inventori.
4. Tabel karakter dan quest berelasi many to many melalui tabel karakter_quest.

# C. Fungsi Tabel dan Kolom

# 1. Tabel pemain
Menyimpan data akun orang yang bermain game. Setiap pemain bisa memiliki lebih dari satu karakter.

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

<img width="543" height="135" alt="Cuplikan layar 2026-11-16 022339" src="https://github.com/user-attachments/assets/eea7ef04-d8c8-4495-a2e5-9f5d7264e4b9" />

# 2. Tabel kelas
Menyimpan jenis atau profesi karakter, misalnya Pendekar, Penyihir, dan Pemanah, beserta bonus statusnya.

<img width="546" height="146" alt="Cuplikan layar 2026-11-16 023021" src="https://github.com/user-attachments/assets/68aeb7b6-88e5-4284-991f-9c8610ac517b" />

# 3. Tabel karakter
Menyimpan tokoh yang dibuat dan dimainkan oleh pemain. Tabel ini terhubung ke pemain dan kelas.

<img width="553" height="196" alt="Cuplikan layar 2026-11-16 024116" src="https://github.com/user-attachments/assets/1414d73b-fc63-426d-94fa-1fc04e861120" />

# 4. Tabel item
Menyimpan daftar seluruh barang yang ada di dalam game, seperti senjata, armor, dan potion

<img width="546" height="149" alt="Cuplikan layar 2026-11-16 024827" src="https://github.com/user-attachments/assets/9667bc6a-88fe-4c1c-8bae-984edfe36459" />

# 5. Tabel inventori
Menyimpan barang yang dimiliki setiap karakter. Tabel ini menjadi penghubung relasi many-to-many antara karakter dan item.

<img width="635" height="140" alt="Cuplikan layar 2026-11-16 032101" src="https://github.com/user-attachments/assets/4ac36c51-89f6-4396-bc20-b47cf714a1ba" />

# 6. Tabel quest
Menyimpan daftar misi yang dapat diambil karakter beserta syarat dan hadiahnya.

<img width="552" height="143" alt="Cuplikan layar 2026-11-16 032334" src="https://github.com/user-attachments/assets/8999a1d1-4f4c-4505-992f-14d02ea754b6" />

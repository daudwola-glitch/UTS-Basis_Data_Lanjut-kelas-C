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

# 7. Tabel karakter_quest
Menyimpan riwayat misi yang diambil karakter. Tabel ini menjadi penghubung relasi many-to-many antara karakter dan quest.

<img width="560" height="138" alt="Cuplikan layar 2026-11-16 032731" src="https://github.com/user-attachments/assets/4a680eb3-b39d-4db2-a231-6b049f3ca640" />



-- database game rpg sederhana

create database if not exists game_rpg;
use game_rpg;

-- tabel pemain (akun orang yang main)
create table pemain (
    id_pemain int auto_increment primary key,
    username varchar(30) not null,
    email varchar(50) not null,
    tgl_daftar date
);

-- tabel kelas (job karakter)
create table kelas (
    id_kelas int auto_increment primary key,
    nama_kelas varchar(20) not null,
    hp int,
    serangan int
);

-- tabel karakter, 1 pemain bisa punya lebih dari 1 karakter
create table karakter (
    id_karakter int auto_increment primary key,
    id_pemain int,
    id_kelas int,
    nama_karakter varchar(30) not null,
    level int default 1,
    gold int default 100,
    foreign key (id_pemain) references pemain(id_pemain),
    foreign key (id_kelas) references kelas(id_kelas)
);

-- tabel item (barang di game)
create table item (
    id_item int auto_increment primary key,
    nama_item varchar(40) not null,
    jenis varchar(20),
    harga int
);

-- tabel inventaris, isi tas tiap karakter
create table inventaris (
    id_inventaris int auto_increment primary key,
    id_karakter int,
    id_item int,
    jumlah int default 1,
    foreign key (id_karakter) references karakter(id_karakter),
    foreign key (id_item) references item(id_item)
);

-- tabel quest (misi)
create table quest (
    id_quest int auto_increment primary key,
    nama_quest varchar(50) not null,
    level_minimal int default 1,
    hadiah_gold int
);

-- tabel quest_karakter, misi yang diambil karakter
create table quest_karakter (
    id int auto_increment primary key,
    id_karakter int,
    id_quest int,
    status varchar(15) default 'berjalan',
    foreign key (id_karakter) references karakter(id_karakter),
    foreign key (id_quest) references quest(id_quest)
);

-- isi data

insert into pemain (username, email, tgl_daftar) values
('budi_gamer', 'budi@gmail.com', '2026-01-10'),
('sari_mage', 'sari@gmail.com', '2026-02-05'),
('andi99', 'andi99@gmail.com', '2026-03-18');

insert into kelas (nama_kelas, hp, serangan) values
('Warrior', 150, 20),
('Mage', 90, 35),
('Archer', 110, 28);

insert into karakter (id_pemain, id_kelas, nama_karakter, level, gold) values
(1, 1, 'Garrus', 5, 350),
(1, 2, 'Merlinn', 2, 120),
(2, 2, 'Aurelia', 8, 780),
(3, 3, 'Sylva', 6, 410);

insert into item (nama_item, jenis, harga) values
('Pedang Besi', 'senjata', 150),
('Tongkat Sihir', 'senjata', 200),
('Armor Kulit', 'armor', 100),
('Potion HP', 'potion', 30);

insert into inventaris (id_karakter, id_item, jumlah) values
(1, 1, 1),
(1, 4, 5),
(2, 2, 1),
(3, 2, 1),
(3, 4, 3),
(4, 3, 1);

insert into quest (nama_quest, level_minimal, hadiah_gold) values
('Basmi Slime', 1, 50),
('Antar Surat ke Desa', 2, 80),
('Kalahkan Raja Goblin', 6, 500);

insert into quest_karakter (id_karakter, id_quest, status) values
(1, 1, 'selesai'),
(1, 2, 'berjalan'),
(3, 3, 'berjalan'),
(4, 1, 'selesai');

-- cek data

-- karakter + pemilik + kelasnya
select karakter.nama_karakter, pemain.username, kelas.nama_kelas, karakter.level
from karakter
join pemain on karakter.id_pemain = pemain.id_pemain
join kelas on karakter.id_kelas = kelas.id_kelas;

-- isi tas karakter
select karakter.nama_karakter, item.nama_item, inventaris.jumlah
from inventaris
join karakter on inventaris.id_karakter = karakter.id_karakter
join item on inventaris.id_item = item.id_item;

-- quest yang sudah selesai
select karakter.nama_karakter, quest.nama_quest
from quest_karakter
join karakter on quest_karakter.id_karakter = karakter.id_karakter
join quest on quest_karakter.id_quest = quest.id_quest
where quest_karakter.status = 'selesai';


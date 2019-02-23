C:\Users\Notbook>cd/xampp/mysql

C:\xampp\mysql>cd bin

C:\xampp\mysql\bin>mysql -u root


MariaDB [(none)]> create database latihan5;
Query OK, 1 row affected (0.01 sec)

MariaDB [(none)]> use latihan5;
Database changed

MariaDB [latihan5]> create table mobil (
    -> kode varchar(5) primary key,
    -> jenis varchar(15),
    -> merk varchar(20),
    -> tarif int(20),
    -> nopol varchar(20) );
Query OK, 0 rows affected (0.60 sec)

MariaDB [latihan4]> insert into mobil (kode, jenis, merk, tarif, nopol) values
    -> ("M001","SEDAN","BMW ES","500000","BG1234AA"),
    -> ("M002","SEDAN","HONDA CRU","350000","BG2345BB"),
    -> ("M003","BUS","MERCEDEZ","1000000","BG3456CC"),
    -> ("M004","BUS","DYNA","800000","BG8443DD"),
    -> ("M005","TRUCK","HYNO ZX","1500000","BG4638EE"),
    -> ("M006","TRUCK","DYNA X1","1500000","GB8473FF");
Query OK, 6 rows affected (0.07 sec)
Records: 6  Duplicates: 0  Warnings: 0


MariaDB [latihan4]> create table pelanggan (
    -> kode varchar (20) null,
    -> nama varchar (50) null,
    -> kontak varchar (20) null,
    -> alamat (12) null,
    -> kota varchar (10) null,
    -> kode_pos int (10) null,
    -> tlp varchar (10) null);

MariaDB [latihan4]> insert into pelanggan(kode, kontak, alamat, kota, kode_pos, tlp) value
    -> ("F001","PT FOX RIVER","HENDAR","Jl Jendral Sudirman 657","BENGKULU","30245","1234567"),
    -> ("F002","CV FOXCON","IWAN","Jl Wahid Hasyim 743","JAKARTA","74329","234567"),
    -> ("F003","PT FARMACON","YANI","Jl Ahmad Dahlan 45","LAMPUNG","28349","3334445");

MariaDB [latihan4]> create table sewa (
    -> nofaktursewa varchar (5),
    -> kodepelanggan varchar (5),
    -> tglsewa date
    -> kodemobil varchar (10),
    -> lamasewa int (20),
    -> uangmuka int (50) );
Query OK, 0 rows affected (0.32 sec)

MariaDB [latihan4]> insert into sewa (nofaktursewa, kodepelanggan, tglsewa, kodemobil, lamasewa, uangmuka) values
    -> ("F001","P001","2008-12-01","M001","2","200000"),
    -> ("F001","P001","2008-12-01","M003","2","200000"),
    -> ("F002","P002",,"2008-12-02","M002","1","100000");



1. menampilkan query table mobil
select mobil.kode, mobil.jenis, mobil.merk, sewa.no_faktursewa, sewa.tgl_sewa, sewa.lama_sewa
-> from mobil left join sewa on mobil.kodemobil order by mobil.kode asc;


2. menampilkan query table pelangan
> select
-> sewa.no_faktursewa,
-> pelanggan.nama,
-> sewa.tgl_sewa,
-> mobil.jenis,
-> mobil.merk,
-> sewa.lama_sewa,
-> sewa.uang_muka
-> from sewa left join mobil on mobil.kode=sewa.kodemobil
-> left join pelanggan on pelanggan.kode=sewa.kodepelanggan;

3. menampilkan query table sewa
> select
-> pelanggan.nama,
-> pelanggan.kota,
sewa.no_faktursewa,
sewa.tgl_sewa,
sewa.kodemobil,
sewa.lama_sewa,
sewa.uang_muka
from pelanggan left jion sewa on pelanggan.kode=sewa.kodepelanggan;

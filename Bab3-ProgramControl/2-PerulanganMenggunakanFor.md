[<< Materi Sebelumnya (Pemilihan dengan "switch") <<](1-PemilihanDenganSwitch.md)
# Perulangan Menggunakan For Statement

Perulangan (atau dalam bahasa inggris disebut dengan **loop**) adalah instruksi kode program yang bertujuan untuk mengulang beberapa baris perintah. Pada materi sebelumnya telah dipelajari tentang perulangan menggunakan **while statement**, kali ini kita akan mempelajari perulangan menggunakan for statement.

## For Statement
For Statement adalah salah satu jenis **Counted Loop**, artinya perulangan ini sudah jelas berapa banyak perulangannya akan dilakukan. For Statemen memiliki tiga komponen yaitu inisialisasi, kondisi, dan update.

## Syntax
Berikut merupakan syntax untuk For Statement.
```c
for(/* inisialisasi */ ; /* kondisi */ ; /* update */){
    /* program yang ingin diulang... */
}
```
- Inisialisasi: menentukan kondisi awal perulangan. Biasanya kondisi awal ini berisi perintah untuk memberikan nilai kepada variabel counter. Variabel counter sendiri adalah sebuah variabel yang akan menentukan berapa banyak perulangan dilakukan (biasanya variabel bertipe `in.t` dan bernama `i`,`j`,`k`, dll. Namun, kalian tetap bebas akan memakai tipe data / nama apa saja)
- Kondisi: merupakan kondisi yang harus dipenuhi agar perulangan berjalanakan. Perulangan akan dilakukan apabila kondisi adalah BENAR atau TRUE dan berhenti apabila kondisi adalah SALAH atau FALSE.
- Update: digunakan untuk meng-update nilai dari pencacah (biasanya berupa increment/decrement). Proses ini akan dieksekusi setelah isi dari `for statement` habis.

**CATATAN!!!**

Perhatikan urutan dalam penulisan ketiga komponen karena ketiganya harus berurutan dan perhatikan pula tanda pemisah antara komponen yaitu menggunakan `;` bukan `,`!

## Contoh Penggunaan
```c
for (int i = 0; i < 3; i++){
  printf("Ini adalah perulangan For ke-%d\n", i);
}
```
Output:
```
Ini adalah perulangan For ke-0
Ini adalah perulangan For ke-1
Ini adalah perulangan For ke-2
```
Analisa program : 
1. Variabel `i` **diinisialisasi** sebagai variabel counter dengan nilai awal `i` adalah 0.
2. **Kondisi** `i < 3` adalah **BENAR** (0 lebih kecil daripada 3) sehingga isi dari `for statement` dieksekusi.
3. Setelah dieksekusi, dilakukan proses **update** sehingga nilai dari `i` adalah 1.
4. **Kondisi** `i < 3` adalah **BENAR** (1 lebih kecil daripada 3) sehingga isi dari `for statement` dieksekusi.
5. Setelah dieksekusi, dilakukan proses **update** sehingga nilai dari `i` adalah 2.
6. **Kondisi** `i < 3` adalah **BENAR** (2 lebih kecil daripada 3) sehingga isi dari `for statement` dieksekusi.
7. Setelah dieksekusi, dilakukan proses **update** sehingga nilai dari `i` adalah 3.
8. **Kondisi** `i < 3` adalah **SALAH** (3 TIDAK lebih kecil daripada 3) sehingga proses perulangan `for statement` selesai.

Flowchart : 
<p align ="center">  <img width = "480" height "380" src = "https://github.com/XnoahR/KP2022/blob/main/Material/For.png" </p>

**CATATAN!!!**

Perhatikan nilai dari variabel counter dan kondisi serta tanda pertidaksamaan yang digunakan!
- apabila `i = 0` dan kondisi `i < 5` maka akan dilakukan perulangan sebanyak 5 kali, yaitu saat `i = 0, 1, 2, 3, 4`.
- apabila `i = 0` dan kondisi `i <= 5` maka akan dilakukan perulangan sebanyak 6 kali, yaitu saat `i = 0, 1, 2, 3, 4, 5`.
- apabila `i = 1` dan kondisi `i < 5` maka akan dilakukan perulangan sebanyak 4 kali, yaitu saat `i = 1, 2, 3, 4`.

## Source code

<details>
<summary>Contoh source code (full)</summary>

```c
#include <stdio.h>

int main(){
    int count;

    printf("Masukkan jumlah perulangan yang diinginkan : ");
    scanf("%d", &count);
    
    for (int i = 1; i <= count; i++){
        printf("Ini adalah perulangan For ke-%d\n", i);
    }
    return 0;
}

/*
Output:

Masukkan jumlah perulangan yang diinginkan : 4
Ini adalah perulangan For ke-1
Ini adalah perulangan For ke-2
Ini adalah perulangan For ke-3
Ini adalah perulangan For ke-4
*/
```
</details>
    
## Tambahan
1. Pastikan nilai yang ada pada variabel counter dan kondisi benar, sehingga program dapat berhenti.\
Berikut merupakan contoh program yang gagal :
```c
for( int i=10; i>=0; i++ ){
    printf("Hello World!\n");
}
```
Pada kode di atas, sampai kapanpun `i` di_increment_ pasti akan selalu lebih besar dari 0 sehingga akan menghasilkan _infinite loop_ dan program kalian tidak akan berhenti melakukan perulangan.\
Kode di atas dapat diperbaiki dengan cara mengubah nilai update menjadi _decrement_, sehingga program dapat berjalan.
```c
for( int i=5; i>=0; i-- ){
    printf("Hello World!\n");
}
```
Output:
```
Hello World!
Hello World!
Hello World!
Hello World!
Hello World!
Hello World!
```

2. Variabel yang dideklarasi pada bagian **inisialisasi** HANYA bisa digunakan di dalam `for statement` saja
```c
for (int i = 0; i < 3; i++){
    printf("Ini adalah perulangan For ke-%d\n", i);
}

printf("nilai variabel i di luar loop = %d", i); // Kode di samping akan menyebabkan error
```
Dapat dilihat bahwa variabel `i` dideklarasi pada komponen **inisialisasi** di `for statement` sehingga setelah perulangan selesai variabel `i` akan _dihancurkan_  atau dihapus.

[>> Materi Selanjutnya (Perulangan menggunakan "do while") >>](3-PerulanganMenggunakanDoWhile.md)

[<< Materi Sebelumnya (Daftar Materi) <<](../DaftarMateri.md)
# 3.1 - Pemilihan dengan Switch

Kondisi SWITCH CASE adalah percabangan kode program dimana kita membandingkan isi sebuah variabel dengan beberapa nilai. Jika proses perbandingan tersebut menghasilkan nilai true, maka block kode program akan dijalankan. Switch case sangat berguna ketika ingin melakukan perbandingan untuk banyak kasus.

Kondisi SWITCH CASE terdiri dari 2 bagian, yakni perintah SWITCH dimana terdapat nama variabel yang akan diperiksa, serta 1 atau lebih perintah CASE, masing-masing untuk setiap nilai yang ingin diperiksa.

Berikut format dasar penulisan kondisi SWITCH CASE dalam bahasa C:

## Syntax:

```c
switch (/* expression */)
{
    case /* konstanta */:
        /* perintah... */
        break; /* opsional */

    case /* konstanta */:
        /* perintah... */
        break; 
        
    default:  /* opsional */
        break; 
}
```

## Penjelasan:

Contoh penggunaan switch dalam program C adalah sebagai berikut:
- ketika `pilihan` bernilai 1 maka potongan kode dibawah akan menampilkan **Kamu mengetik angka 1**
- ketika `pilihan` bernilai 2 maka potongan kode dibawah akan menampilkan **Kamu mengetik angka 2**
- ketika `pilihan` **tidak** bernilai 1 atau 2 maka potongan kode dibawah akan menampilkan **Kamu tidak mengetik angka 1 atau 2**

```c
switch (pilihan)
{
    case 1:
        printf("Kamu mengetik angka 1\n");
        break; 

    case 2:
        printf("Kamu mengetik angka 2\n");
        break; 
        
    default:  
        printf("Kamu tidak mengetik angka 1 atau 2\n");
        break; 
}
```

**switch** statement bisa memiliki **case: labels** sebanyak-banyaknya asalkan setiap **label** bernilai konstan dan unik.

**break** merupakan hal yang penting dalam switch, karena jika tidak ada **break** maka semua pernyataan setelah **label yang sesuai**, akan dijalankan atau dieksekusi sampai ketemu **break**. contohnya: 

- ketika `pilihan` bernilai 1 maka potongan kode dibawah akan menampilkan <br> **Angka 1** <br> **Angka 2**
- ketika `pilihan` bernilai 2 maka potongan kode dibawah akan menampilkan <br> **Angka 2**
- ketika `pilihan` bernilai 3 maka potongan kode dibawah akan menampilkan <br> **Angka 3** <br> **Angka 4** <br> **Default (tidak ada case yang cocok)**


```c
switch (pilihan)
{
    case 1:
        printf("Angka 1\n");

    case 2:
        printf("Angka 2\n");
        break;

    case 3:
        printf("Angka 3\n");

    case 4:
        printf("Angka 4\n");
        
    default:  
        printf("Default (tidak ada case yang cocok)\n");
}
```

### Kelemahan SWITCH CASE:
Struktur SWITCH CASE ini terlihat lebih rapi daripada struktur IF ELSE IF, dan kadang kala bisa lebih efisien. Namun SWITCH CASE juga memiliki batasan, yakni tidak bisa dipakai untuk kondisi yang lebih kompleks seperti perbandingan dengan tanda lebih besar dari ” > “, maupun penggabungan kondisi.

Kita tidak bisa membuat struktur CASE seperti berikut:

 ```c
 case > '90':
  printf("Pertahankan! \n");
  break;
  ```
Kondisi perbandingan di atas hanya bisa ditulis menggunakan struktur IF.

Sehingga jika kondisi yang diperiksa cukup rumit, tetap harus menggunakan struktur IF ELSE IF. Struktur SWITCH CASE hanya cocok dipakai untuk operasi perbandingan sederhana, dimana nilai yang diperiksa hanya terdiri dari nilai yang tetap.

### Case Ranges:
Case Ranges adalah ekstension dari bahasa C yang berarti ini bukan C standar (tidak bisa digunakan pada semua compiler C)

Cara menggunakannya seperti ini:
```
case rendah ... tinggi
```
Dengan menggunakan Case Ranges penulisan code menjadi lebih cepat dan mudah dibaca.<br> Berikut perbandingannya:
- Tidak menggunakan Case Ranges
  ```c
    switch (pilihan)
    {
        case 1:
        case 2:
        case 3:
        case 4:
        case 5:
            printf("angkamu diantara 1 - 5\n");
            break;
    }
  ```
- Menggunakan Case Ranges
  ```c
    switch (pilihan)
    {
        case 1 ... 5:
            printf("angkamu diantara 1 - 5\n");
            break;
    }
    ```

### Source code
<details>
  <summary>Contoh Source Code</summary>

  ```c
#include <stdio.h>

int main() {
    double angkaPertama, angkaKedua, hasil;
    char op;
    printf("Masukkan Angka Pertama, Operator, Angka Kedua. yang mana Operatornya diantara (+, -, *, /): ");
    scanf("%lf %c %lf", &angkaPertama, &op, &angkaKedua);

    switch (op) {
        case '+':
            hasil = angkaPertama + angkaKedua;
            break;
        case '-':
            hasil = angkaPertama - angkaKedua;
            break;
        case '*':
            hasil = angkaPertama * angkaKedua;
            break;
        case '/':
            hasil = angkaPertama / angkaKedua;
            break;
        default:
            printf("Operator mu salah");
    }
    printf("%.1lf %c %.1lf = %.1lf\n", 
        angkaPertama, op, angkaKedua, hasil);
}
  ```
</details>

[>> Materi Berikutnya (Perulangan menggunakan "for") >>](2-PerulanganMenggunakanFor.md)

[<<Materi Sebelumnya(Robomind Basic Instructions)](1-BasicInstructions.md)
# 2.2 - Robomind Programming structures

Di dalam materi ini, Anda akan menemukan berbagai struktur gramatikal yang diperbolehkan untuk mendefinisikan perilaku robot, yang akan membantu Anda memahami cara mengendalikan robot dengan lebih baik.

## Comments
Semua teks yang muncul setelah tanda pagar, '#', tidak akan diinterpretasikan sebagai instruksi. Robot akan melanjutkan untuk membaca baris berikutnya dalam skrip. Gunakan kemungkinan ini untuk memberikan catatan pada bagian-bagian skrip, hanya untuk diri Anda sendiri, sebagai dokumentasi tentang bagaimana bagian-bagian ini bekerja.

```
# teks tidak berpengaruh dalam kode
```

## Loops
	
### 1. repeat(n){...instructions...}
Mengulangi instruksi di antara tanda kurung kurawal tepat sebanyak n kali, di mana n adalah jumlah kali pengulangan yang diinginkan.

```py
# a square of 2x2
repeat(4)
{
	forward(2)
	right()
}
```

### 2. repeat{...instructions...}
Terus ulangi instruksi di antara tanda kurung kurawal tanpa henti, sehingga robot akan menjalankannya secara terus-menerus contohnya dapat dilihat di bawah ini:

```py
# just goes forward
# (but eventually will stay hitting a wall)
repeat
{
	forward(1)
}

```

### 3. repeatWhile(condition){...instructions...}
Mengulangi instruksi di antara tanda kurung kurawal selama kondisinya terpenuhi. Kondisi ini harus berupa instruksi persepsi/penglihatan contoh `frontIsClear`

```py
# keeps going forward,
# but stops when it can't go any further
repeatWhile(frontIsClear)
{
	forward(1)
}
```
## Source Code

Yang terakhir adalah source code. **Source code** merupakan wujud implementasi dari suatu algoritma atau pseudocode dalam **sintaks yang formal** sehingga instruksi-instruksinya dapat dimengerti dan dijalankan oleh komputer. Source code dapat ditulis menggunakan bahasa pemrograman apapun (C/C++/Java/Python/dll) sehingga dapat dicompile dan/atau dijalankan oleh komputer.

Berikut merupakan contoh source code program berdasarkan **Algoritma/Pseudocode 1** dalam bahasa C
```c
#include <stdio.h>

int main() {
    int A, B;

    printf("Masukkan angka pertama: ");
    scanf("%d", &A);

    printf("Masukkan angka kedua: ");
    scanf("%d", &B);

    printf("Nilai dari %d + %d = %d\n", A, B, A + B);

    return 0;
}
```

Berikut merupakan contoh source code program berdasarkan **Algoritma/Pseudocode 2** dalam bahasa C
```c
#include <stdio.h>

int main() {
    int nilaiMahasiswa;

    printf("Masukkan nilai anda: ");
    scanf("%d", &nilaiMahasiswa);

    if (nilaiMahasiswa >= 75) {
        printf("Selamat!\n");
        printf("Anda dinyatakan lulus\n");
    } else if (nilaiMahasiswa < 75) {
        printf("Maaf!\n");
        printf("Anda harus mengikuti remidiasi\n");
    }

    return 0;
}
```
[>> Materi Berikutnya(Operasi Assignment dan Aritmatika)](3-OperasiAssignmentdanAritmatika.md)

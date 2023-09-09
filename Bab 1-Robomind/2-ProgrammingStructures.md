[<<Materi Sebelumnya(Robomind Basic Instructions)](1-BasicInstructions.md)
# 2.2 - Robomind Programming structures

Di dalam materi ini, Anda akan menemukan berbagai struktur gramatikal yang diperbolehkan untuk mendefinisikan perilaku robot, yang akan membantu Anda memahami cara mengendalikan robot dengan lebih baik.

## Comments
Semua teks yang muncul setelah tanda pagar, '#', tidak akan diinterpretasikan sebagai instruksi. Robot akan melanjutkan untuk membaca baris berikutnya dalam skrip. Gunakan kemungkinan ini untuk memberikan catatan pada bagian-bagian skrip, hanya untuk diri Anda sendiri, sebagai dokumentasi tentang bagaimana bagian-bagian ini bekerja.

```py
# teks tidak berpengaruh dalam kode
```

## Loops
### 1. repeat(n){...instructions...}
Mengulangi instruksi di antara tanda kurung kurawal tepat sebanyak n kali, di mana n adalah jumlah kali pengulangan yang diinginkan.

```py
# a square of 2x2
repeat(4) {
	forward(2)
	right()
}
```

### 2. repeat{...instructions...}
Terus ulangi instruksi di antara tanda kurung kurawal tanpa henti, sehingga robot akan menjalankannya secara terus-menerus contohnya dapat dilihat di bawah ini:

```py
# just goes forward
# (but eventually will stay hitting a wall)
repeat {
	forward(1)
}

```

### 3. repeatWhile(condition){...instructions...}
Mengulangi instruksi di antara tanda kurung kurawal selama kondisinya terpenuhi. Kondisi ini harus berupa instruksi persepsi/penglihatan contoh `frontIsClear`

```py
# keeps going forward,
# but stops when it can't go any further
repeatWhile(frontIsClear) {
	forward(1)
}
```
### 4. break
Memungkinkan kode untuk keluar dari loop (misalnya bagian yang berulang) sehingga berhenti menjalankan instruksi di antara tanda kurung kurawal. Robot akan melanjutkan melakukan instruksi yang tersisa setelah tanda kurung kurawal penutup dari loop.

```py
# keep going forward, until you can't go any further
repeat() {
	if(frontIsObstacle) {
		break
	}
	else {
		forward(1)
	}
}
```

## If-structures
### 1. if(condition){...instructions...}
Akan menjalankan instruksi di antara tanda kurung kurawal, hanya jika kondisinya terpenuhi. Jika tidak, robot akan segera mengikuti instruksi yang tertulis setelah tanda kurung kurawal penutup. Kondisi tersebut harus berupa instruksi persepsi/melihat contoh: frontIsClear,


```py
# if you see white paint on your left, make it black
if(leftIsWhite) {
	left
	forward(1)
	paintBlack
	stopPainting
	backward(1)
	right
}
```

### 2. if(condition){...instructions...}else{...instructions...}
Akan menjalankan instruksi di antara pasangan tanda kurung kurawal pertama, hanya jika kondisinya terpenuhi. Maka ia tidak akan menjalankan instruksi dari blok else (instruksi pasangan kedua). Bila kondisi tidak terpenuhi, robot hanya akan menjalankan instruksi di antara tanda kurung kurawal kedua. Setelah menjalankan salah satu blok instruksi, ia akan membaca instruksi setelah tanda kurung kurawal terakhir. Kondisi tersebut harus berupa instruksi persepsi/melihat (contoh: frontIsClear),

```py
# if you see white paint on your left, make it black
# else drive a few steps forward
if(leftIsWhite) {
	left
	forward(1)
	paintBlack
	stopPainting
	backward(1)
	right
}
else {
	forward(3)
} 
```

## Logical Expressions
Kondisi struktur if- dan repeatWhile adalah apa yang disebut ekspresi logis. Ekspresi seperti itu akan menghasilkan nilai benar atau salah, yang kemudian digunakan untuk memutuskan langkah ke bagian kode yang sesuai untuk melanjutkan eksekusi.

Ekspresi logis dapat berupa [Instruksi Persepsi](1-BasicInstructions.md), misalnya: leftIsWhite. Instruksi dasar juga dapat dibuat dengan operator boolean not, and, or.

Contoh:
```py
if(leftIsWhite) {
    left
    forward(1)
}
```

Namun kondisi ini juga dapat disempurnakan agar lebih menunjukkan dengan lebih tepat kapan instruksi terkait harus dieksekusi dengan menggunakan (kombinasi) operator berikut.

|Operation	|Notation	|Keterangan	|Penjelasan	|
|:-----:  	|:----:		|:------:	|-----------	|
|`not`		|`~`		|tidak(NOT)	|Dijalankan apabila kondisi A tidak bernilai benar |
|`and`		|`&`		|dan(AND)	|Dijalankan apabila kondisi A dan B semuanya benar |
|`or`		|`\|`		|atau(OR)	|Dijalankan apabila salah satu dari A dan B bernilai benar|


[>> Materi Berikutnya(Operasi Assignment dan Aritmatika)](3-OperasiAssignmentdanAritmatika.md)

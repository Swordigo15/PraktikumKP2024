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
		break()
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
	left()
	forward(1)
	paintBlack()
	stopPainting()
	backward(1)
	right()
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
	paintBlack()
	stopPainting()
	backward(1)
	right()
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
    left()
    forward(1)
}
```

Namun kondisi ini juga dapat disempurnakan agar lebih menunjukkan dengan lebih tepat kapan instruksi terkait harus dieksekusi dengan menggunakan (kombinasi) operator berikut.

|Operation	|Notation	|Keterangan	|Penjelasan	|
|:-----:  	|:----:		|----------	|-----------	|
|`not`		|`~`		|tidak(NOT)	|Dijalankan apabila kondisi A tidak bernilai benar |
|`and`		|`&`		|dan(AND)	|Dijalankan apabila kondisi A dan B semuanya benar |
|`or`		|`\|`		|atau(OR)	|Dijalankan apabila salah satu dari A dan B bernilai benar|

Nilai benar dan salah juga dapat diterapkan secara langsung seolah-olah merupakan instruksi persepsi.

Urutan operator itu penting (seperti perkalian dan penjumlahan bilangan). Operasi tidak mengikat paling kuat, diikuti oleh dan, diikuti oleh atau. Tanda kurung dapat digunakan untuk mempengaruhi urutan evaluasi.

Contoh:
```py
repeatWhile(not frontIsClear and (leftIsWhite or rightIsWhite)) {
    forward(1)
}

if(flipCoin and not rightIsWhite) {
    right()
    backward(1)
}

if(true and false) {
    # this instruction is never executed
    forward(1)
}

```

### Comparing numbers
Jenis ekspresi logis lainnya adalah perbandingan angka. Kemudian Anda dapat membuat keputusan berdasarkan nilai yang diberikan. Misalnya, hanya ke kanan jika variabel tertentu kurang dari 5.

Contoh:
```py
forward()
maybeToRight(8)
forward()

procedure maybeToRight(n){
    if(n < 5){
        right
    }
}
```

Ini adalah daftar lengkap pembanding yang akan membantu Anda memahami perbedaan antara berbagai hal yang dibahas dalam materi ini.
|Operator	|Keterangan				|Penjelasan					|
|:----:		|--					|--						|
|A == B		|sama dengan				|Cek jika A sama dengan B			|
|A ~= B		|tidak sama dengan			|Cek jika A tidak sama dengan B			|
|A > B		|lebih besar dari			|Cek jika A lebih besar dari B			|
|A >= B		|lebih besar dari atau sama dengan	|Cek jika A lebih besar dari atau sama dengan B	|
|A < B		|kurang dari				|Cek jika A kurang dari B			|
|A <= B		|kurang dari atau sama dengan		|Cek jika A kurang dari atau sama dengan B	|

## Procedures
### 1. procedure name(par1, par2, ... , parN){...instructions...}
Mendefinisikan prosedur baru dengan nama yang Anda inginkan. Prosedur ini dapat memiliki nol atau lebih parameter, yang juga dapat Anda beri nama yang berguna. Di sini mereka disebut par1, par2, . . . , parN. Ini adalah variabel yang dapat Anda gunakan dalam instruksi di antara tanda kurung kurawal. Kode dalam suatu prosedur tidak akan dijalankan secara otomatis, Anda harus menulis 'panggilan prosedur' setiap kali Anda ingin menjalankan instruksi dalam definisi (Lihat instruksi selanjutnya).

**Tip: buat prosedur baru ketika Anda menggunakan serangkaian instruksi lebih dari sekali.**

Contoh:
```py
# define how to draw a rectangle
procedure rectangle(width, height) {
	paintWhite()
	repeat(2) {
		forward(height)
		right()
		forward(width)
		right()
	}
	stopPainting()
}
```

### 2. name(arg1, arg2, . . . , argN)
Adalah panggilan ke prosedur dengan nama yang sesuai dan parameter jumlah yang sama dengan argumen Anda. Argumennya, di sini disebut arg1, arg2, . . . , argN, adalah nilai tertentu yang akan digunakan dalam definisi prosedur.

Contoh:
```py
# these instructions will be performed
forward(1)
rectangle(3,2) # a call to the 'rectangle' procedure
forward(3)
rectangle(1,4) # another call with other arguments

# this is the definition of 'rectangle'
procedure rectangle(width, height) {
	paintWhite()
	repeat(2) {
		forward(height)
		right()
		forward(width)
		right()
	}
	stopPainting()
}
```

### 3. return
Untuk menghentikan eksekusi suatu prosedur sebelum mencapai akhir, gunakan return dari dalam definisi prosedur. Program terus menjalankan perintah setelah panggilan terkait.

Contoh:
```py
# these instructions will be performed
toWall()
right()
forward()

# go forward until you reach a wall
procedure toWall() {
    repeat() {
        if(frontIsObstacle) {
            # stop "toWall" procedure,
            # continue with right and forward
            return()
        }
        else {
            forward()
        }
    }
}  
```

### 4. return(arg)
Untuk menghentikan eksekusi suatu prosedur sebelum mencapai akhir, gunakan return dari dalam definisi prosedur. Program terus menjalankan perintah setelah panggilan terkait.

Secara default, prosedur mengembalikan nilai nol. Anda dapat mengubahnya dengan mengembalikan ekspresi.

Contoh:
```py
# this instruction will be performed
forward(double(3))

# double the given amount
procedure double(n) {
    return(2 * n)
} 
```

### 5. Recursion
Prosedur dapat didefinisikan secara rekursif. Itu berarti Anda menggunakan prosedur yang Anda definisikan dalam definisi prosedur itu sendiri, dengan memanggilnya. Butuh beberapa saat untuk memahaminya, namun ternyata menjadi alat yang ampuh.

Contoh:
```py
# these instructions will be performed
toWall()
right()
forward()

# go forward until you reach a wall
procedure toWall() {
      # notice that no loops are used
      if(frontIsObstacle) {
          # stop "toWall" procedure
          return()
      }
      else {
          # do one step
          forward()
          # and do a recursive call!
          toWall()
      }
}   
```

## Arithmetic
Pada dasarnya, operasi aritmatika yang didukung robomind meliputi beberapa operator seperti yang dijelaskan pada tabel di bawah ini. Mari kita buat dua variabel sebagai contoh, `a = 20` dan `b = 15`.
|Operator	|Nama		|Contoh		|
|:------:	|----		|------		|
|+		|Penambahan	|`a + b = 35`	|
|-		|Pengurangan	|`a - b = 5`	|
|*		|Perkalian	|`a * b = 300`	|
|/		|Pembagian	|`b / a = 0.75`	|

Dengan operasi ini, Anda dapat menjumlahkan, mengurangi, mengalikan, dan membagi angka. Perhatikan bahwa angkanya harus berupa bilangan bulat (bilangan bulat).

Contoh :
```py
# using some arithmetic in expressions
forward(2+3)
if(3*4 < 13) {
	x = 3
	left(x-2)
}
backward(-(3+4)/2)
```

## Variables
Dengan variabel Anda dapat mengingat nilai-nilai di bawah nama yang dapat Anda pilih sendiri. Nilai-nilai variabel ini tersedia nanti di seluruh skrip. Anda bisa mendapatkan nilai-nilai ini, dengan menggunakan kembali namanya. Anda dapat mengingat nilai ekspresi apa pun (jadi: angka, perhitungan, ekspresi logis, lihat perintah, kembalikan nilai).

Contoh:
```py
# store a number
x = 42

# store another number, based on x
y = x / 2

# store a logical expression
clear = leftIsClear & frontIsClear & rightIsClear

# store the actual number of steps taken
# until you bumped (returned by "forward")
actual = forward(100)

if(clear){
     right(2)
     forward(actual) # go back
}
left(y)
```

## End

Akan menyebabkan seluruh program berhenti ketika instruksi ini dijalankan.

Contoh:
```py
# stop after 5 steps, or earlier when you encounter a beacon on the right
repeat(5) {
	forward(1)
	if(rightIsBeacon) {
		end # stops execution of the program
	}
}
# normal end of the program
```

[>> Materi Berikutnya(Operasi Assignment dan Aritmatika)](3-OperasiAssignmentdanAritmatika.md)

# Robomind
![img](https://github.com/Swordigo15/PraktikumKP2023/blob/main/Material/Screenshot%20(193).png)

<br>

<p>RoboMind adalah sebuah aplikasi pemrograman sederhana untuk tujuan pendidikan. Aplikasi ini memiliki berbagai aturan pemrogramannya sendiri untuk melatih para pemula dalam mempelajari dasar-dasar logika pemrograman. Aplikasi ini menunjukkan simulasi robot yang dapat digerakkan dengan perintah-perintah yang tersedia. Selain untuk memperkenal teknik-teknik pemrograman, aplikasi ini juga bertujuan untuk mengenalkan robotika dan intelegensi artifisial. </p>

Pada aplikasi ini terdapat bebrapa instruksi dasar, yaitu : 
+ Move
+ See
+ Paint
+ Grab

Ada beberapa cara untuk memberikan instruksi pada aplikasi ini :
1. Menekan Tombol
2. Menyeret mouse
3. Mengetik perintah

Untuk materi kali ini kita hanya akan memberikan perintah dengan tulisan. Berikut daftar instruksi yang dapat diberikan.

| Tipe      | Command        | Deskripsi                                                 |
| ---       | ---            | ---                                                       |
| Move      | forward(n)     | Berjalan n langkah ke depan                               |
|           | backward(n)    | Berjalan n langkah kebelakang                             |
|           | left()         | Berputar ke kiri 90 derajat                               |
|           | right()        | Berputar ke kanan 90 derajat                              |
|           | north(n)       | Berputar ke arah utara dan berjalan n langkah             |
|           | south(n)       | Berputar ke arah selatan dan berjalan n langkah           |
|           | east(n)        | Berputar ke arah timur dan berjalan n langkah             |
|           | west(n)        | Berputar ke arah barat dan berjalan n langkah             |
| Paint     | paintWhite()   | Mengecat tanah dengan warna putih                         |
|           | paintBlack()   | Mengecat tanah dengan warna hitam                         |
|           | stopPainting() | Berhenti mengecat                                         |
| Grab      | pickUp()       | Mengambil beacon yang ada didepan robot                   |
|           | putDown()      | Menaruuh beacon yang ada didepan robot                    |
|           | eatUp()        | Mengambil dan menghancurkan beacon yang ada didepan robot |
| Flip Coin | flipCoin()     | Menghasilkan pilihan secara random (true atau false)      |

| see       | Kiri             | Depan             | Kanan             |
| ---       | ---              | ---               | ---               |
|           | leftIsObstacle() | frontIsObstacle() | rightIsObstacle() |
|           | leftIsClear()    | frontIsClear()    | rightIsClear()    |
|           | leftIsBeacon()   | frontIsBeacon()   | rightIsBeacon()   |
|           | leftIsWhite()    | frontIsWhite()    | rightIsWhite()    |
|           | leftIsBlack()    | frontIsBlack()    | rightIsBlack()    |

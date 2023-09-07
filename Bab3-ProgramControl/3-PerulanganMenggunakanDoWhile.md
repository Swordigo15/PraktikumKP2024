[<< Materi Sebelumnya (Perulangan menggunakan "for") <<](2-PerulanganMenggunakanFor.md)
# 3.3 - Do While Loop
Merupakan bentuk variasi dari `while` loop. Cara kerja dari `do...while` mirip dengan `while`, perbedaan yang membedakan dengan while adalah `do...while` akan menjalankan perintah yang ada di kode blok sekali sebelum melakukan pengecekan kondisi.


Perhatikan potongan kode dibawah ini
    
    int i = 0;
    while(i>0) {
        printf("saya berhasil dijalankan");
        i++;
    }

Saat potongan kode dijalankan maka tidak ada nilai yang ditampilkan pada terminal, hal ini dikarenakan kondisi yang dimasukan pada `while` bernilai false. Bandingkan dengan potongan kode `do...while` dibawah ini

    int i = 0;
    do {
        printf("saya berhasil dijalankan");
        i++;
    } while(i>0);

Output

    saya berhasil dijalankan

Berbeda dengan kode `while` kode `do..while` diatas akan menampilkan teks sekali meskipun kondisi pada while bernilai salah. Hal ini dikarenakan pada `do...while` program pada blok do akan dijalankan sekali sebelum mengecek kondisi yang ada.

[>> Materi Berikutnya ("break" dan "continue") >>](4-BreakAndContinue.md)

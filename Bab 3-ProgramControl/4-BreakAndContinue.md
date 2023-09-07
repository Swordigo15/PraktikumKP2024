[< Materi Sebelumnya (Perulangan menggunakan "do...while")](3-PerulanganMenggunakanDoWhile.md)
# 3.4 - Break and Continue

## Break

Break digunakan untuk keluar/berhenti dari suatu perulangan sebelum saatnya perulangan tersebut selesai. Break dapat digunakan pada semua jenis perulangan (for, while, do...while) dan juga switch case.

    int i = 0;
    while(i<10) {
        printf("hallo saya berhasil dijalankan\n");
        i++;
        if(i==6)  
            break;

    }

Output

    hallo saya berhasil dijalankan
    hallo saya berhasil dijalankan
    hallo saya berhasil dijalankan
    hallo saya berhasil dijalankan
    hallo saya berhasil dijalankan
    hallo saya berhasil dijalankan
    hallo saya berhasil dijalankan

## Continue

Continue digunakan untuk melakukan skip atau melompati suatu iterasi dan melanjutkan ke iterasi selanjutnya.

    int i = 0;
    while(i<10) {
        printf("perulangan ke %d kali\n",i);
        i++;
        if(i==6) 
            continue;
    }

Output

    perulangan ke 0 kali
    perulangan ke 1 kali
    perulangan ke 2 kali
    perulangan ke 3 kali
    perulangan ke 4 kali
    perulangan ke 5 kali
    perulangan ke 6 kali
    perulangan ke 7 kali
    perulangan ke 8 kali
    perulangan ke 9 kali
    
    
Bab 2 selesai. [Kembali ke Daftar Materi](../DaftarMateri.md)

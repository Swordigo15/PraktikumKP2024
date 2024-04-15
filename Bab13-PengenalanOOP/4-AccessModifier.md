[<< Class Pointer](3-ClassPointer.md)

# 13.4 Access Modifier

## Pendahuluan _Access Modifier_

Dalam praktiknya, sebuah atribut dalam sebuah kelas tidak selalu dibuat _public_. Hal ini disebabkan, jika atribut dibuat _public_, dengan mudah nilai dari atribut tersebut dapat diubah di luar _scope_-nya, misalnya di fungsi `main`. Padahal, terkadang kita ingin membuat atribut tersebut tidak bisa dengan mudah diubah. Untuk itu, kita akan menggunakan _access modifier_ lain seperti `private` atau `protected`.

## _Access Modifier Public_

Seperti telah dijelaskan sebelumnya, atribut yang dibuat _public_ dapat diakses dari _scope_ yang lain, misalnya di fungsi `main`. Contoh penggunaanya adalah sebagai berikut:

```cpp
#include <iostream>
using namespace std;

class Hero {
    // Access Modifier Public
    public:
        // Atribut bersifat public
        char name[50];
        int health;
        float defensePower;
        int level;

    // Constructor
    Hero(const char* name, int health, float defensePower, int level){
        this->name = name;
        this->health = health;
        this->defensePower = defensePower;
        this->damagePower = 1;
    }

    // Method untuk mengubah level
    void changeLevel(int level){
        this->level = level;
    }
};

```

Berikut program dalam fungsi `main`:

```cpp
int main(){
    // Instansiasi kelas Hero
    Hero* saber = new Hero("Layla", 80, 32.5);

    // Mengakses atribut public
    cout << "Hero Name : " << saber->name << endl;
    cout << "Level saber adalah " << saber->level << endl;

    // Memodifikasi atribut public
    saber->name = "Sabar"; // nama saber kini berubah menjadi "Sabar"
    saber->health = 85; // health saber kini berubah menjadi 85 
    saber->level = 3; // level saber kini berubah menjadi 3
    cout << "Level saber sekarang adalah " << saber->level << endl;

    // Mengakses method changeLevel
    saber->changeLevel(5); // level berubah menjadi 5
    cout << "Level saber sekarang adalah " << saber->level << endl;
    return 0;
}
```  

### Penjelasan Kode Di Atas

Permasalahannya adalah `name` dari objek kelas `Hero` bisa dengan mudah diubah. Padahal, atribut `name` dari objek `Hero` tentu saja seharusnya tidak dapat diubah. Selain itu, adanya _method_ _public_ `changeLevel()`, level dari objek `Hero` dapat berubah seperti contoh di atas. Tentunya, level dari objek `Hero` tidak bisa berubah dari 1 langsung ke 3 dan dari 3 langsung ke 5. Oleh karena itu, untuk memproteksi atribut dan _method_ supaya tidak bisa diakses atau diubah dari _scope_ lain,  dapat digunakan _access modifier_ `private` atau `protected`.

## _Access Modifier Private_

_Access modifier_ `private` digunakan jika terdapat atribut atau _method_ yang telah dibuat, di-_setting_ supaya tidak dapat diakses di luar _scope-nya_. Sebagai contoh, penggunaan _access modifier_ `private` adalah sebagai berikut :

```cpp
#include<iostream>
using namespace std;

class Hero {
    // Atribut akan bersifat private
    private:
        char name[50];
        int attackPower;
        float defensePower;
        int level;

    // Constructor harus bersifat public
    public:
        Hero(const char* name, int attackPower, float defensePower){
            this->name = name;
            this->attackPower = attackPower;
            this->defensePower = defensePower;
            this->level = 1;
        }
    
    // Private Method untuk menambahkan attackPower dan defensePower
    private:
        void addPower(){
            this->attackPower += 10 * this->level;
            this->defensePower += 5 * this->level;
        }
    
    // Public Method 
    public:
        // Method untuk menaikkan level Hero
        void levelUp(){
            this->level++;
            this->addPower(); // private method addPower masih bisa diakses di dalam scope kelas Hero
        }

        // Method untuk menampilkan semua atribut Hero
        void displayHero(){
            cout << "Hero's Name\t: " << this->name << endl;
            cout << "Attack Powert \t: " << this->attackPower << endl;
            cout << "Defense Power \t: " << this->defensePower << endl;
            cout << "Hero's Level \t: " << this->level << endl; 
            // Private attributes hanya dapat diakses di dalam scope kelas Hero
        }
};

```

Kode dalam fungsi `main` adalah sebagai berikut :

```cpp
int main(){
    // Instansiasi 
    Hero* mbakMiya = new Hero("Miya", 80, 65);

    // Mencoba mengakses atribut Hero secara langsung
    // cout << "Hero's Name\t: " << mbakMiya->name << endl; 
    // Menghasilkan ERROR, karena name adalah atribut private

    // Menampilkan properti dari hero
    mbakMiya->displayHero(); // dapat akses karena method bersifat public

    // Mencoba menaikkan level Hero secara langsung
    // mbakMiya->level = 2;
    // Menghasilkan ERROR karena level adlah atribut private

    // Menaikkan level hero dengan method levelUp
    mbakMiya->levelUp();

    // Menampilkan kembali properti dari hero
    mbakMiya->displayHero(); 

    return 0;
}

```

### Penjelasan Kode di Atas

Dengan _access modifier_ `private`, atribut atau _method_ tidak bisa dengan mudah diakses dari _scope_ luar. Selain itu, atribut juga tidak bisa diubah secara langsung seperti pada _access modifier_ `public`.

Atribut yang bersifat privat hanya dapat diakses di dalam _scope_ kelasnya saja. Namun, bagaimana jika kita perlu mengakses atau mengubah nilai dari atribut privat? Jawabannya adalah dengan membuatkan _method_ yang bersifat `public` seperti contoh di atas. _Method_ `addPower()` bersifat privat, _method_ ini akan mengubah nilai dari atribut `attackPower` dan `defensePower`. _Method_ `addPower()` yang bersifat privat ini akan dipanggil di dalam _method_ `levelUp()` yang bersifat publik. Dengan begitu, jika _method_ `levelUp()` dipanggil di `main`, _method_ `addPower()` juga otomatis dijalankan. Hal ini disebabkan _method_ `addPower()` berada di dalam _method_ `addPower()`.

Sementara untuk menampilkan properti-properti dari kelas Hero, tidak bisa dilakukan secara langsung seperti pada _access modifier_ `public`. Kita harus membuatkan sebuah _method_ yang bersifat publik yang di dalamnya kita dapat mengakses atribut privat dari kelas `Hero` sebab masih di dalam _scope_ kelas `Hero`.

**Catatan : Jika atribut di atas konstruktor tidak diberikan keyword `private`, atribut tersebut secara _default_ akan menjadi `private`.**

## _Access Modifier Protected_

_Access Modifier_ `protected` memiliki kemiripan dengan `private`, yaitu sama-sama tidak bisa diakses dari luar _scope_ kelasnya. Perbedaan utama antara _access modifier_ `private` dengan `protected` adalah atribut atau _method_ yang bersifat privat tidak dapat diwariskan ke kelas lain. Sementara pada _access modifier_ `protected`, atribut atau _method_-nya dapat diwariskan ke kelas lain. 

**Catatan :**

1. Konsep pewarisan akan dibahas lebih lanjut pada bagian _inheritance_.
2. Dalam C++, _method_ yang bersifat private, aksesnya masih dapat diberikan ke kelas lain degan menggunakan _friend function_.
3. Dalam C++, atribut yang bersifat privat, aksesnya masih dapat diberikan ke kelas lain degan menggunakan _friend class_.

[>> Daftar Materi](../DaftarMateri.md)

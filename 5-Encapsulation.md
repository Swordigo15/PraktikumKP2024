[<< Access Modifier](4-AccessModifier.md)

# 13.5 Enkapsulasi

## Pendahuluan

Pada materi sebelumnya, telah dibahas bahwa pada _access modifier_ _private_ dan _protected_, atribut dan _method_-nya tidak dapat diakses dari luar _scope_-nya secara langsung seperti pada _access modifier_ _public_. Namun, terkadang kita tetap ingin mengakses atau memanipulasi nilai atribut tersebut dari _scope_ luar. Bagaimana caranya? Kita dapat membuat _method_ yang bersifat _public_ untuk mengakses atribut tersebut (biasa disebut fungsi _getter_) atau untuk memanipulasi nilai dari atribut tersebut (biasa disebut fungsi _setter_).

## Getter Function

Fungsi _getter_ adalah _public method_ yang digunakan untuk mendapatkan suatu atribut tertentu yang bersifat _private_ atau _protected_. Umumnya, _method_ ini memiliki nama `get` diikuti dengan nama atributnya, misalkan nama atributnya adalah `health`, nama _getter function_-nya adalah `getHealth()` atau `get_health()`. _Return type_ dari _method_ ini akan menyesuaikan dengan tipe data dari atributnya. Berikut contoh penggunaan _getter function_ :

```cpp
#include <iostream>
using namespace std;

class Hero {
    private:
        int health;
        float powerAttack;
        float defensePower;
    
    // Constructor
    public:
        Hero(int health, float powerAttack, float defensePower){
            this->health = health;
            this->powerAttack = powerAttack;
            this->defensePower = defensePower;
        }
    
        // Getter untuk health
        int getHealth(){
            return this->health;
        }

        // Getter untuk powerAttack
        float getPowerAttack(){
            return this->powerAttack;
        }
};

int main(){
    // Instansiasi Hero akai
    Hero akai = Hero(80, 15, 35);

    // Mengakses health dan powerAttack dari akai dengan getter function
    cout << "Health \t\t: " << akai.getHealth() << endl;
    cout << "Power Attack \t: " << akai.getPowerAttack() << endl;

    return 0;
}

```

## Setter Functions

Fungsi _setter_ adalah _public method_ yang digunakan untuk mendapatkan suatu atribut tertentu yang bersifat _private_ atau _protected_. Umumnya, _method_ ini memiliki nama `set` diikuti dengan nama atributnya, misalkan nama atributnya adalah `health`, nama _setter function_-nya adalah `setHealth()` atau `set_health()`. _Method_ ini umumnya adalah _method_ tanpa _return_ atau `void`. _Setter method_ ini akan memiliki argumen dengan tipe data sama dengan atribut yang akan dimanipulasi nilainya. Berikut contoh penggunaan _setter function_ :

```cpp
#include <iostream>
using namespace std;

class Hero {
    private:
        int health;
        float powerAttack;
        float defensePower;
    
    // Constructor
    public:
        Hero(int health, float powerAttack, float defensePower){
            this->health = health;
            this->powerAttack = powerAttack;
            this->defensePower = defensePower;
        }

        // Getter untuk health
        int getHealth(){
            return this->health;
        }

        // Getter untuk powerAttack
        float getPowerAttack(){
            return this->powerAttack;
        }
    
        // Setter untuk health
        void setHealth(int newHealth){
            this->health = newHealth;
        }

        // Setter untuk powerAttack
        void setPowerAttack(float newPowerAttack){
            this->powerAttack = newPowerAttack;
        }
};

int main(){
    // Instansiasi Hero akai
    Hero akai = Hero(80, 15, 35);

    // Mengakses health dan powerAttack dari akai dengan getter function
    cout << "Health \t\t: " << akai.getHealth() << endl;
    cout << "Power Attack \t: " << akai.getPowerAttack() << endl;

    // Mengubah health dan powerAttack dari akai dengan setter
    akai.setHealth(85); // health berubah menjadi 85
    akai.setPowerAttack(20); // powerAttack berubah menjadi 20

    // Mengakses kembali health dan powerAttack dari akai dengan getter function
    cout << "Health \t\t: " << akai.getHealth() << endl;
    cout << "Power Attack \t: " << akai.getPowerAttack() << endl;

    return 0;
}

```

[>> Daftar Materi](../DaftarMateri.md)

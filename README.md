# Tas-Kag-t-Makas-Oyunu
Bu kod örneği, kullanıcıdan "Taş-Kağıt-Makas" oyunu için seçimler yapmasını ister ve bilgisayarın rastgele bir seçim yapmasını simüle etmesini sağlar.
#include <iostream>
#include <ctime>
#include <cstdlib>

using namespace std;

int main() {
    srand(time(0)); // Rastgele sayı üretimi için zamanı kullan

    int oyuncuSkor = 0;
    int bilgisayarSkor = 0;
    int tur = 1;

    while (true) {
        cout << "Tur " << tur << endl;
        cout << "Oyuncu Skoru: " << oyuncuSkor << "  Bilgisayar Skoru: " << bilgisayarSkor << endl;

        cout << "Seciminizi yapin: (1: Tas, 2: Kagit, 3: Makas, 0: Cikis): ";
        int oyuncuSecim;
        cin >> oyuncuSecim;

        if (oyuncuSecim == 0) {
            cout << "Oyun sona erdi. Sonuçlar:" << endl;
            cout << "Oyuncu Skoru: " << oyuncuSkor << "  Bilgisayar Skoru: " << bilgisayarSkor << endl;
            break;
        }

        if (oyuncuSecim < 1 || oyuncuSecim > 3) {
            cout << "Geçersiz seçim. Lütfen tekrar deneyin." << endl;
            continue;
        }

        int bilgisayarSecim = rand() % 3 + 1; // Bilgisayarın seçimi

        cout << "Bilgisayar " << bilgisayarSecim << " (1: Tas, 2: Kagit, 3: Makas) seciyor." << endl;

        if (oyuncuSecim == bilgisayarSecim) {
            cout << "Berabere!" << endl;
        } else if ((oyuncuSecim == 1 && bilgisayarSecim == 3) ||
                   (oyuncuSecim == 2 && bilgisayarSecim == 1) ||
                   (oyuncuSecim == 3 && bilgisayarSecim == 2)) {
            cout << "Oyuncu kazandi!" << endl;
            oyuncuSkor++;
        } else {
            cout << "Bilgisayar kazandi!" << endl;
            bilgisayarSkor++;
        }

        tur++;
    }

    return 0;
}

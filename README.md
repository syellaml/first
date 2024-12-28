#include <iostream>
#include <string>
#include <iomanip>
using namespace std;

struct Mahasiswa {
    string nim;
    string nama;
    float ipk;
};

Mahasiswa mahasiswa[100];
int jumlah = 0;

void isimahasiswa() {
    cout << "Masukkan jumlah mahasiswa: ";
    cin >> jumlah;
    cin.ignore();
    for (int i = 0; i < jumlah; i++) {
        cout << "Data mahasiswa ke-" << i + 1 << endl;
        cout << "NIM  : ";
        getline(cin, mahasiswa[i].nim);
        cout << "Nama : ";
        getline(cin, mahasiswa[i].nama);
        cout << "IPK  : ";
        cin >> mahasiswa[i].ipk;
        cin.ignore();
    }
}

void printmahasiswa() {
    cout << left << setw(10) << "NIM" << setw(20) << "Nama" << "IPK" << endl;
    for (int i = 0; i < jumlah; i++) {
        cout << left << setw(10) << mahasiswa[i].nim << setw(20) << mahasiswa[i].nama << mahasiswa[i].ipk << endl;
    }
}

void cariNIM() {
    string cari;
    cout << "Masukkan NIM yang dicari: ";
    cin >> cari;
    bool ditemukan = false;
    for (int i = 0; i < jumlah; i++) {
        if (mahasiswa[i].nim == cari) {
            cout << "mahasiswa ditemukan: " << endl;
            cout << "Nama: " << mahasiswa[i].nama << ", IPK: " << mahasiswa[i].ipk << endl;
            ditemukan = true;
            break;
        }
    }
    if (!ditemukan) {
        cout << "Data tidak ditemukan." << endl;
    }
}

void cariNama() {
    string cari;
    cout << "Masukkan nama yang dicari: ";
    cin.ignore();
    getline(cin, cari);
    bool ditemukan = false;
    for (int i = 0; i < jumlah; i++) {
        if (mahasiswa[i].nama == cari) {
            cout << "Data ditemukan: " << endl;
            cout << "NIM: " << mahasiswa[i].nim << ", IPK: " << mahasiswa[i].ipk << endl;
            ditemukan = true;
            break;
        }
    }
    if (!ditemukan) {
        cout << "Data tidak ditemukan." << endl;
    }
}

void printIPKTerkecil() {
    if (jumlah == 0) {
        cout << "Data kosong!" << endl;
        return;
    }
    int idx = 0;
    for (int i = 1; i < jumlah; i++) {
        if (mahasiswa[i].ipk < mahasiswa[idx].ipk) {
            idx = i;
        }
    }
    cout << "Mahasiswa dengan IPK terkecil: " << endl;
    cout << "Nama: " << mahasiswa[idx].nama << ", NIM: " << mahasiswa[idx].nim << ", IPK: " << mahasiswa[idx].ipk << endl;
}

void printIPKTerbesar() {
    if (jumlah == 0) {
        cout << "Data kosong!" << endl;
        return;
    }
    int idx = 0;
    for (int i = 1; i < jumlah; i++) {
        if (mahasiswa[i].ipk > mahasiswa[idx].ipk) {
            idx = i;
        }
    }
    cout << "Mahasiswa dengan IPK terbesar: " << endl;
    cout << "Nama: " << mahasiswa[idx].nama << ", NIM: " << mahasiswa[idx].nim << ", IPK: " << mahasiswa[idx].ipk << endl;
}

void sortNIM() {
    for (int i = 0; i < jumlah - 1; i++) {
        for (int j = i + 1; j < jumlah; j++) {
            if (mahasiswa[i].nim > mahasiswa[j].nim) {
                swap(mahasiswa[i], mahasiswa[j]);
            }
        }
    }
    cout << "Data berhasil diurutkan berdasarkan NIM." << endl;
}

void sortNama() {
    for (int i = 0; i < jumlah - 1; i++) {
        for (int j = i + 1; j < jumlah; j++) {
            if (mahasiswa[i].nama > mahasiswa[j].nama) {
                swap(mahasiswa[i], mahasiswa[j]);
            }
        }
    }
    cout << "Data berhasil diurutkan berdasarkan nama." << endl;
}

void sortIPK() {
    for (int i = 0; i < jumlah - 1; i++) {
        for (int j = i + 1; j < jumlah; j++) {
            if (mahasiswa[i].ipk > mahasiswa[j].ipk) {
                swap(mahasiswa[i], mahasiswa[j]);
            }
        }
    }
    cout << "Data berhasil diurutkan berdasarkan IPK." << endl;
}

int main() {
    int pilihan;
    do {
        cout << "\nMenu Aplikasi Array Record\n";
        cout << "1. Isi Data\n";
        cout << "2. Print Data\n";
        cout << "3. Cari NIM\n";
        cout << "4. Cari Nama\n";
        cout << "5. Print IPK Terkecil\n";
        cout << "6. Print IPK Terbesar\n";
        cout << "7. Sort NIM\n";
        cout << "8. Sort Nama\n";
        cout << "9. Sort IPK\n";
        cout << "10. Selesai\n";
        cout << "Pilihan: ";
        cin >> pilihan;

        switch (pilihan) {
            case 1: isimahasiswa(); break;
            case 2: printmahasiswa(); break;
            case 3: cariNIM(); break;
            case 4: cariNama(); break;
            case 5: printIPKTerkecil(); break;
            case 6: printIPKTerbesar(); break;
            case 7: sortNIM(); break;
            case 8: sortNama(); break;
            case 9: sortIPK(); break;
            case 10: cout << "Program selesai." << endl; break;
            default: cout << "Pilihan tidak valid!" << endl;
        }
    } while (pilihan != 10);

    return 0;
}


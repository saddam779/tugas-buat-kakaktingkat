# tugas-buat-kakaktingkat
game tebak angka

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// Fungsi untuk membersihkan layar alternatif
void clearScreen() {
    for(int i = 0; i < 30; i++) printf("\n");
}

// Fungsi untuk delay alternatif
void delay(int seconds) {
    clock_t start = clock();
    while((clock() - start) < seconds * CLOCKS_PER_SEC);
}

int main() {
    srand(time(0));
    int round = 1;
    int score = 0;
    
    while(1) {
        int jumlah_angka = 2 + round;
        int angka[jumlah_angka];
        int tebakan[jumlah_angka];
        
        printf("Ronde %d:\n", round);
        printf("Angka: ");
        for(int i = 0; i < jumlah_angka; i++) {
            angka[i] = rand() % 10;
            printf("%d ", angka[i]);
        }
        
        printf("\n(Menunggu 3 detik...)\n");
        delay(3); // Menggunakan delay alternatif
        clearScreen(); // Menggunakan clear alternatif
        
        printf("Masukkan angka-angka tadi (pisah dengan spasi): ");
        for(int i = 0; i < jumlah_angka; i++) {
            scanf("%d", &tebakan[i]);
        }
        
        int benar = 1;
        for(int i = 0; i < jumlah_angka; i++) {
            if(tebakan[i] != angka[i]) {
                benar = 0;
                break;
            }
        }
        
        if(benar) {
            printf("Benar! Lanjut ke ronde berikutnya.\n\n");
            score++;
            round++;
        } else {
            printf("Salah! Game over.\n");
            printf("Skor akhir: %d\n", score);
            break;
        }
    }
    
    return 0;
}

SOURCE CODE 

    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    
    #define MAX_LENGTH 2024
    #define MIN_LENGTH 1945
    
    void lessThanRequired (int* lengthOfText){
        printf("The length of your text is less than specified, please update your text\n");
        *lengthOfText = MIN_LENGTH;
    }
    
    void equalThanRequired (int* lengthOfText){
        printf("Thank you, Your text length is correct\n");
    }
    
    void moreThanRequired (int* lengthOfText){
        printf("Your text is too long, please reduce the text\n");
        *lengthOfText = MIN_LENGTH;
    }
    
    int checkLenghtRequirement(char* text){
        int length = strlen(text);
        if (length < MIN_LENGTH)
            return 0;
        else if (length == MIN_LENGTH)
            return 1;
        else
            return 2;
    }
    
    int main() {
        int lengthOfText, selectOption;
        FILE *fptr = NULL;
        char text[MAX_LENGTH];
    
        fptr = fopen("ilham.txt", "r");
    
        if(fptr == NULL){
            printf("Error");
            exit(1);
        }
    
        fgets(text, MAX_LENGTH, fptr);
    
        fclose(fptr);
    
        selectOption = checkLenghtRequirement(text);
    
        // TODO: Use function pointers to call the appropriate function based on selectOption
        // HINT: Create an array of function pointers and call the appropriate function using selectOption
        void (*functionArray[3])(int*) = {lessThanRequired, equalThanRequired, moreThanRequired};
        functionArray[selectOption](&lengthOfText);
    
        printf("\nThe Length is updated to %d", lengthOfText);
    
        return 0;
    }

PENJELASAN CODE :

Mari kita bahas setiap baris kode:

1. `#include <stdio.h>`: Mengimpor standar input-output library untuk fungsi `printf()` dan `fgets()`.

2. `#include <stdlib.h>`: Mengimpor library standar untuk alokasi memori dinamis dan fungsi umum lainnya seperti `exit()`.

3. `#include <string.h>`: Mengimpor library standar untuk fungsi-fungsi yang berhubungan dengan string seperti `strlen()`.

4. `#define MAX_LENGTH 2024`: Mendefinisikan konstanta `MAX_LENGTH` yang menyimpan panjang maksimum dari teks yang dapat diterima.

5. `#define MIN_LENGTH 1945`: Mendefinisikan konstanta `MIN_LENGTH` yang menyimpan panjang minimum dari teks yang diharapkan.

6. `void lessThanRequired (int* lengthOfText)`: Mendefinisikan fungsi `lessThanRequired` yang mengambil pointer ke variabel integer yang mewakili panjang teks. Fungsi ini mencetak pesan bahwa panjang teks kurang dari yang diharapkan dan mengubah panjang teks menjadi nilai minimum.

7. `void equalThanRequired (int* lengthOfText)`: Mendefinisikan fungsi `equalThanRequired` yang juga mengambil pointer ke variabel integer yang mewakili panjang teks. Fungsi ini mencetak pesan bahwa panjang teks sudah sesuai dengan yang diharapkan.

8. `void moreThanRequired (int* lengthOfText)`: Mendefinisikan fungsi `moreThanRequired` yang mengambil pointer ke variabel integer yang mewakili panjang teks. Fungsi ini mencetak pesan bahwa panjang teks terlalu panjang dan mengubah panjang teks menjadi nilai minimum.

9. `int checkLengthRequirement(char* text)`: Mendefinisikan fungsi `checkLengthRequirement` yang mengambil string sebagai argumen dan mengembalikan nilai berdasarkan panjang string tersebut. Jika panjangnya kurang dari `MIN_LENGTH`, kembali 0. Jika sama dengan `MIN_LENGTH`, kembali 1. Jika lebih besar dari `MIN_LENGTH`, kembali 2.

10. `int main() {...}`: Fungsi utama dari program.

11. `int lengthOfText, selectOption;`: Deklarasi dua variabel integer `lengthOfText` dan `selectOption`.

12. `FILE *fptr = NULL;`: Deklarasi pointer ke objek FILE dan inisialisasi dengan NULL.

13. `char text[MAX_LENGTH];`: Deklarasi array karakter `text` dengan panjang maksimum `MAX_LENGTH`.

14. `fptr = fopen("ilham.txt", "r");`: Membuka file "ilham.txt" untuk dibaca.

15. `if(fptr == NULL){...}`: Memeriksa apakah file berhasil dibuka atau tidak. Jika tidak, mencetak pesan kesalahan dan keluar dari program.

16. `fgets(text, MAX_LENGTH, fptr);`: Membaca isi file ke dalam array `text`.

17. `fclose(fptr);`: Menutup file setelah selesai membacanya.

18. `selectOption = checkLengthRequirement(text);`: Memanggil fungsi `checkLengthRequirement` untuk memeriksa apakah panjang teks sesuai dengan persyaratan.

19. `void (*functionArray[3])(int*) = {lessThanRequired, equalThanRequired, moreThanRequired};`: Mendefinisikan array dari pointer fungsi yang masing-masing menunjuk ke fungsi yang sesuai. Ada tiga elemen dalam array ini, masing-masing untuk kasus panjang teks kurang dari, sama dengan, dan lebih dari yang diharapkan.

20. `functionArray[selectOption](&lengthOfText);`: Memanggil fungsi yang sesuai dari array `functionArray` berdasarkan nilai `selectOption`.

21. `printf("\nThe Length is updated to %d", lengthOfText);`: Mencetak panjang teks yang telah diubah, baik itu menjadi nilai minimum atau tidak.

    
OUTPUT :

<img width="772" alt="image" src="https://github.com/Santosyouknow/PINARINGAN-IMAN-SANTOSO1/assets/161540041/8929b8e9-c7ba-47ca-a1b0-da4003e4af0a">


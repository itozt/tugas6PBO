# Tugas Pertemuan 6 - Tech Support System

![Screenshot 2024-10-01 110152](https://github.com/user-attachments/assets/add9594a-4dc0-4c89-a030-fd751ca26bc6)

### Penjelasan Keseluruhan Kelas :
1. `SupportSystem` : Mengelola alur program, memproses input pengguna, dan menampilkan respons.
2. `InputReader` : Mengambil input dari pengguna melalui konsol.
3. `Responder` : Menyediakan respons acak untuk ditampilkan pada pengguna.

## Kelas SupportSystem
Kelas ini akan menjadi inti dari sistem dan mengatur alur program, termasuk menerima input dari pengguna dan mendapatkan respons dari objek Responder.
```
import java.util.Scanner;

public class SupportSystem {
    private InputReader reader;
    private Responder responder;
    
    public SupportSystem(){
        reader = new InputReader();
        responder = new Responder();
    }

    public void start(){
        boolean finished = false;
        System.out.println("Selamat datang di Christo Support System.");
        System.out.println("Silakan ceritakan masalah Anda.");
        System.out.println("Kami akan membantu dengan masalah apa pun yang Anda miliki.");
        System.out.println("Ketik 'bye' untuk keluar dari sistem kami.");

        while (!finished){
            String input = reader.getInput();
            if (input.equals("bye")){
                finished = true;
            } else {
                String response = responder.generateResponse();
                System.out.println(response);
            }
        }

        System.out.println("Goodbye! Thank you for using the support system.");
    }

    public static void main(String[] args){
        SupportSystem support = new SupportSystem();
        support.start();
    }
}
```

### Penjelasan
1. `SupportSystem()` : Konstruktor untuk membuat objek InputReader dan Responder sebagai bagian dari sistem.
2. `start()` :
- Memulai program dengan menampilkan pesan selamat datang dan instruksi kepada pengguna.
- Menginisialisasi loop yang terus berjalan hingga pengguna mengetik "bye".
- Mengambil input pengguna melalui objek InputReader.
- Jika input adalah "bye", program keluar dari loop.
- Jika input bukan "bye", program akan meminta objek Responder untuk menghasilkan respons acak.
- Menampilkan respons dari Responder ke konsol.
- Setelah loop selesai, program menampilkan pesan selamat tinggal.
3. `main(String[] args)` : Metode utama untuk menjalankan program, di mana objek SupportSystem dibuat dan metode start() dipanggil.

## Kelas InputReader
Kelas ini bertanggung jawab untuk mengambil input dari pengguna.
```
import java.util.Scanner;

public class InputReader {
    private Scanner scanner;

    public InputReader(){
        scanner = new Scanner(System.in);
    }

    public String getInput(){
        System.out.print("> ");
        return scanner.nextLine();
    }
}
```
### Penjelasan 
1. Scanner scanner: Objek Scanner digunakan untuk membaca input dari konsol.
2. InputReader(): Konstruktor yang menginisialisasi objek Scanner untuk membaca input dari sistem (konsol).
3. getInput():
- Meminta pengguna memasukkan teks dengan menampilkan prompt "> ".
- Mengambil input dari pengguna menggunakan scanner.nextLine().
- Mengembalikan input yang dimasukkan oleh pengguna.

## Kelas Responder
Kelas ini bertugas untuk menghasilkan respons umum terhadap input yang diberikan oleh pengguna.
```
import java.util.Random;

public class Responder {
    private String[] responses;

    public Responder(){
        responses = new String[]{
            "Itu terdengar menarik. Ceritakan lebih lanjut...",
            "Oh, saya mengerti. Bisakah Anda menjelaskan lebih lanjut?",
            "Hmm, itu cukup rumit. Mari kita bahas lebih dalam.",
            "Menarik. Bisakah Anda memberikan lebih banyak detail?",
            "Biarkan saya berpikir... Bisakah Anda memperjelas sedikit lebih banyak?"
        };
    }

    public String generateResponse(){
        Random random = new Random();
        int index = random.nextInt(responses.length);
        return responses[index];
    }
}
```
### Penjelasan
1. `String[] responses` : Array yang berisi beberapa kalimat respons standar yang akan diberikan oleh sistem untuk menanggapi masalah pengguna.
2. `Responder()` : Konstruktor yang menginisialisasi array responses dengan kalimat-kalimat respons default.
3. `generateResponse()` :
- Membuat objek Random untuk memilih respons secara acak dari array responses.
- Menghasilkan indeks acak berdasarkan panjang array responses.
- Mengembalikan salah satu kalimat respons berdasarkan indeks yang dihasilkan secara acak.

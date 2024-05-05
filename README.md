## Tutorial 10 - Broadcast Chat
Nama: Syifa Kaffa Billah

NPM: 2206816430

Kelas: C


### Original Code of Broadcast Chat

**Server**
![server.png](img%2Fserver.png)
**Client 1**
![client1.png](img%2Fclient1.png)
**Client 2**
![client2.png](img%2Fclient2.png)
**Client 3**
![client3.png](img%2Fclient3.png)

Untuk menjalankan program dengan spesifikasi 1 server dan 3 client, saya menjalankan perintah `cargo run --bin server` 
pada satu terminal dan menjalankan perintah `cargo run --bin client` pada 3 terminal lainnya di intelij. Ketika saya
mengirim pesan (mengetik teks) pada client 1, server menerima pesan tersebut dan di broadcast ke semua client (client 2,
3, termasuk client 1 yang mengirim teks tesebut). Begitu juga ketika saya mengirim/mengetik teks dari client 2, yang 
akan di broadcast oleh server ke client lainnya.
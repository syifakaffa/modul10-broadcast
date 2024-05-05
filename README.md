## Tutorial 10 - Broadcast Chat
Nama: Syifa Kaffa Billah

NPM: 2206816430

Kelas: C


### 2.1. Original Code of Broadcast Chat

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

### 2.2. Modifying the websocket port
**Server**
![server-sebelum-diubah.png](img%2Fserver-sebelum-diubah.png)
**Client**
![client-port-8080-error.png](img%2Fclient-port-8080-error.png)

Pada saat  port 8080 hanya diubah di satu sisi saja (contohnya di sisi client), akan tejadi error pada client sebab
port client tersebut tidak terkoneksi dengan server. Server hanya menyediakan port 2000 saja.

**Server**
![server-port8080.png](img%2Fserver-port8080.png)
**Client 1**
![client1-port8080.png](img%2Fclient1-port8080.png)
**Client 2**
![client2-port8080.png](img%2Fclient2-port8080.png)
**Client 3**
![client3-port8080.png](img%2Fclient3-port8080.png)

Agar tidak terjadi error, perlu dilakukan modifikasi yang mengganti port menjadi 8080 pada kedua file, yaitu file client 
dan file server. Pada file client.rs, port dinti pada Uri di `ClientBuilder` yang akan membangun (build) koneksi
WebSocket pada client. Sedangkan pada file server, port 8080 diganti pada variabel `listener` nya yang bertujuan sebagai
sebagai TCP listener pada koneksi serta pada query print yang menunjukkan kalau server listening pada port 8080.
Saat port sudah sama di kedua file, maka program akan berjalan sebagaimana mestinya seperti pada saat masih menggunakan
port 2000.

### 2.3. Small changes. Add some information to client
**Server**
![server-add-ip-port.png](img%2Fserver-add-ip-port.png)
**Client 1**
![client1-add-ip-port.png](img%2Fclient1-add-ip-port.png)
**Client 2**
![client2-add-ip-port.png](img%2Fclient2-add-ip-port.png)
**Client 3**
![client3-add-ip-port.png](img%2Fclient3-add-ip-port.png)

Untuk memasukkan informasi tentang alamat IP dan port dari pengirim pada setiap klien, saya memodifikai format teks yang 
di-broadcast dalam file server.rs. Awalnya, teks yang di-broadcast menggunakan `bcast_tx.send(text.into())?;`, tetapi 
saya modifikasi agar mencakup alamat IP pengirim dengan menggunakan format baru `bcast_tx.send(format!("{addr} : {text}"))?;`
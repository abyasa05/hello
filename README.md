# Reflection Notes

### Commit 1
Method `handle_connection()` akan membaca _header_ dari _http request_ yang menyertai suatu koneksi TCP (`TcpStream`). Kemudian, method akan menuliskan dan menyimpan _string_ _http request_ tersebut dalam suatu `Vec<_>`. _String_ yang tersimpan kemudian akan dicetak ke konsol.
<br/>

### Commit 2
Seperti sebelumnya, method `handle_connection()` akan membaca dan menyimpan _string http request_ ketika terdapat suatu koneksi TCP. Kemudian, method akan mengkonstruksikan suatu _http response_ yang berisikan status _request_ yang sukses (_200 OK_) beserta dengan konten dari berkas `hello.html`. Ukuran berkas `hello.html` (panjang dari kontennya) juga dicatat untuk menentukan ukuran (Content-Length) dari _response body_. _Http response_ kemudian dikirimkan kembali ke klien sehingga ditampilkan konten dari berkas `hello.html`.

Screenshot untuk commit 2:
![Commit 2 Screenshot 1](/static/images/Commit2_1.png)
![Commit 2 Screenshot 2](/static/images/Commit2_2.png)
<br/>

### Commit 3
Method `handle_connection()` sekarang menerima _request_ yang dikategorikan dalam dua jenis, yaitu _request_ _default_ (dengan _endpoint_ `/`) dan _request_ lainnya. Jika method menerima _request_ untuk _endpoint_ `/`, program akan menyimpan _string_ berisi status sukses (200) beserta berkas `hello.html`. Selain _endpoint_ tersebut, program akan menyimpan status _request_ tidak ditemukan (404) beserta berkas `404.html`. Berkas dan status _request_ yang bersesuaian kemudian akan diproses (konten dan ukuran berkas dibaca dan disimpan) untuk membuat respons yang akan dikirimkan kembali ke klien. Refaktorisasi menggunakan `if` _clause_ berfungsi untuk merapikan kode program serta menyederhanakan logika program dalam membuat respons. Simplifikasi ini juga berdampak pada proses modifikasi program yang lebih efisien dan mudah (seandainya ingin dilakukan).

Screenshot untuk commit 3:
![Commit 3 Screenshot 1](/static/images/Commit3_1.png)
![Commit 3 Screenshot 2](/static/images/Commit3_2.png)
<br/>

### Commit 4
Method `handle_connection()` menerima tiga jenis _request_. _Request_ dengan _endpoint_ `/` akan mendapatkan respons berupa `hello.html`. Sementara itu, _endpoint_ `/sleep` akan men-_delay_ server selama 5 detik (dengan `thread::sleep`) sebelum mengirimkan respons berupa `hello.html`. Terakhir, untuk _endpoint_ lainnya akan mendapatkan respons berupa `404.html`. Karena program ini hanya berjalan pada satu _thread_, maka server hanya bisa memproses satu _request_ dalam satu waktu. Maka dari itu, jika _request_ `/` dikirimkan sesaat setelah `/sleep` dikirimkan, pengiriman respons untuk _request_ `/` harus menunggu hingga `/sleep` mendapatkan responsnya yang memerlukan waktu 5 detik.

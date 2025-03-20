## Reflection Notes

### Commit 1
Method `handle_connection()` akan membaca _header_ dari _http request_ yang menyertai suatu koneksi TCP (`TcpStream`). Kemudian, method akan menuliskan dan menyimpan _string_ _http request_ tersebut dalam suatu `Vec<_>`. _String_ yang tersimpan kemudian akan dicetak ke konsol.
<br/>

### Commit 2
Seperti sebelumnya, method `handle_connection()` akan membaca dan menyimpan _string http request_ ketika terdapat suatu koneksi TCP. Kemudian, method akan mengkonstruksikan suatu _http response_ yang berisikan status _request_ yang sukses (_200 OK_) beserta dengan konten dari berkas `hello.html`. Ukuran berkas `hello.html` (panjang dari kontennya) juga dicatat untuk menentukan ukuran (Content-Length) dari _response body_. _Http response_ kemudian dikirimkan kembali ke klien sehingga ditampilkan konten dari berkas `hello.html`.

Screenshot untuk commit 2:
![Commit 2 Screenshot 1](/static/images/Commit2_1.png)
![Commit 2 Screenshot 2](/static/images/Commit2_2.png)
<br/>
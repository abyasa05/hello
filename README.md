## Reflection Notes

### Commit 1
Method `handle_connection()` akan membaca _header_ dari _http request_ yang menyertai suatu koneksi TCP (`TcpStream`). Kemudian, method akan menuliskan dan menyimpan _string_ _http request_ tersebut dalam suatu `Vec<_>`. _String_ yang tersimpan kemudian akan dicetak ke konsol.
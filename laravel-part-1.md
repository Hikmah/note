#Laravel : Framework PHP -- 1
by arif setyawan

##Instalasi 

1. Download laravel pada <http://laravel.com/download>
2. Ekstrak instalasi pada `htdocs`
3. Rename direktori hasil ekstrakan misal dari `htdocs/laravel` ke nama project anda `htdocs/fashion` dan direktori project ini kita namai dengan [PROJECT]
4. Jika anda menggunakan linux, anda perlu membuka permission untuk direktori storage di `[PROJECT]/storage` menjadi 755, owner menjadi nobody dan group menjadi nogroup

		#sudo chmod -R 755 storage/
		#sudo chown -R nobody storage/
		#sudo chgrp -R nogroup storage/

5. Setting Virtual Host
	
	Virtual host digunakan untuk mensimulasikan host pada scoop local. Secara umum anda dapat mengakses aplikasi anda menggunakan <http://localhost/> *)baca Instalasi Apache + PHP Server. 

6. Setelah membuat virtual host misalkan fashion.dev anda dapat mengakses project web anda pada alamat tersebut seperti <http://fashion.dev/>.

##Konfigurasi

Berikut ini adalah konfigurasi utama yang perlu di edit.

1. application.php
		
		return array(
			'url' => 'http://fashion.dev/',
			'index' => '',
			'key' => 'your_key_here',
			'timezone' => 'Asia/Jakarta',
			'ssl' => TRUE
		);

2. database.php

		return array(
			'connections' => array(
				'mysql' => array(
				'driver'   => 'mysql',
				'host'     => 'localhost',
				'database' => 'fashion',
				'username' => 'user_database_anda',
				'password' => 'password_database_anda',
				'charset'  => 'utf8',
				'prefix'   => '',
			)
		);
		
##Success Landing Page

[1]: http://url.to.img.1/ "Gambar 1"
[2]: http://url.to.img.2/ "Gambar 2"
[3]: http://url.to.img.3/ "Gambar 3"



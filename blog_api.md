#Sample Blog Web API

mantain by : `Arif Setyawan and Sudaryatno`

## API List

###HTTP Get API
Semua api yang dapat diakses dengan menggunakan method HTTP GET Request

1. **Mengambil semua artikel**

		akses : api/blog/all.json
	return
		
		[
			- {
				title: "Hello World", 
				slug: "hello_world",
				content: "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
				categories: "general",
				created: "2013-01-05 04:28:16"
			},
			- {
				...
			}
			
		]

2. **Mengambil judul semua artikel**

		akses : api/blog/all?title_only=true
	return 
		
		[
			- {
				title: "Hello World",
				slug: "hello_world",
			},
			- {
				...
			}
				
		

3. **Melihat satu konten**

		akses : api/blog/single/(:slug)

4. **Mengambil nama kategori**

		akses : api/blog/categories
	return
		
		[
			{
				1: "Uncategorized",
				2: "General",
			}
		]


###HTTP Post API
Semua api yang dapat digunakan dengan menggunakan method HTTP POST Request

1. **Memasukkan artikel baru**

		akses : api/blog/single/create
	Metadata :
	`title`, `content`, `username`, `categories_name`

2. **Update artikel lama**
		
		akses : api/blog/update/(:slug),
		akses : api/blog/update/(:ids)
	Metadata :
	
	- `slug` / `posts_id` untuk klarifikasi post yang ingin diupdate
	- `title`, `content`, `username`, `categories_name` untuk field yang diupdate
		

3. **Menghapus artikel**

		akses : api/blog/single/delete/(:slug),
		akses : api/blog/single/delete/(:ids)
	Metadata :
	`slug` / `posts_id`
		
#Prediksi Soal UAS Pemrograman Web 

Teknik Informatika Universitas Muhammadiyah Malang

1. Konsep Web MVC (Model View Controller)
  - Pengertian tentang Model, View serta Controller di web
	- Hirarki Web MVC
	
2. Web Dinamis - Client Server
	- Menganalisa kebutuhan dalam membangun web dengan konten dinamis yang melibatkan peran client server dalam menyajikan data.
	- Mampu menjelaskan peranan teknologi dalam membuat konten dinamis tersebut seperti javascript, API, xml, json.  
	
3. PHP Data Object
	- pemahaman penggunaan php data object
	- berikut ini adalah contoh script PDO :
	
			<?php  
				$dbname = 'pelanggan'; $user = 'root'; $pass = 'pass'; $host = 'localhost';
				try{
					$DBH = new PDO("mssql:host=$host;dbname=$dbname", $user, $pass);
					$data = array('nim' => '06560267');
					// named placeholder
					$STH = $DBH->query("SELECT alamat, tanggal_daftar, nomer_telepon FROM pelanggan WHERE nim = :nim ");
					$STH->setFetchMode(PDO::FETCH_OBJ);
					$STH->execute($data);
					while($row = $STH->fetch()){ //loop
		    			echo $row->alamat . "\n";
		    			echo $row->tanggal_daftar . "\n";
		    			echo $row->nomer_telepon . "\n";
					}
				} catch (PDOException $e){
					echo $e‐>getMessage();
				}
			?>	

4. Fungsi Route di Framework
	- Dapat menjelaskan fungsi route pada framework PHP seperti Codeigniter
5. Framework + OOP 
	- Dapat membuat code dan atau memaparkan analisai dari studi kasus.
	- Contoh : studi kasus fitur pencarian pada data pegawai, sehingga dapat dimodel implementasinya sebagai berikut.
	
		**Controller**
			
			<?php
				class Searching extends CI_Controller{
					function __construct(){
						parent::__construct();
						$this->load->model('Search_Model', model_pencarian);
					}
					
					function index(){
						$this->load->view('search_form');
					}
					
					function do_search(){
						$input = $_INPUT['pencarian'];
						$arr_jabatan  = $this->model_pencarian->get_all_jabatan();

						if(in_array($arr_jabatan, $input)){
							//return yang dicari adalah jabatan 
							$data['arr_hasil'] = $this->model_pencarian->get_pegawai_by_jabatan($input);

							$this->load->view('table', $data);
						} else {
							//cari nama
							$data['arr_hasil'] = $this->model_pencarian->get_pegawai_by_name($input);

							$this->load->view('table', $data);
						}
					}
				}
			?>
			
		**Model**
		
			<?php
				class Search_Model extends CI_Model{
					function __construct(){
						parent::__construct();
					}
					
					function get_all_jabatan(){
						$query = $this->db->get('jabatan');
						return $query;
					}
		
					function get_pegawai_by_jabatan($input){
						$this->db->from('pegawai');
						$this->db->where('jabatan',$input)
						$query = $this->db->get();
						return $query->result_array();
					}
		
					function get_pegawai_by_name($input){
						$this->db->from('pegawai');
						$this->db->where('nama_pegawai',$input)
						$query = $this->db->get();
						return $query->result_array();
					}
				}
			?>
			
		**View search_form.php**
		
			<?php
				<form>
					<input type="text" name="pencarian"/>
					<input type="submit">
				</form>
			?>
			
		**View table.php**
		
			<table>
				<tr>
					<th>Nama</th>
					<th>Jabatan</th>
				</tr>
				
				<?php
					foreach ($arr_hasil as $row){
						echo '<tr>';
						echo '<td>'.$row['nama_pegawai'].'</td>';
						echo '<td>'.$row['jabatan'].'</td>';
						echo '</tr>';
					}
				?>
			</table>

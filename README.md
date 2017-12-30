## README To-Do-List-NodeJS

* Aplikasi To-Do-List-NodeJS yang dibuat ini bertujuan untuk menambahkan dan menampilkan To-Do-List dari input yang tersedia di dalam aplikasi tersebut.
Sebelum dapat menjalankan aplikasi To-Do-List-NodeJS ini, user perlu melakukan `Sign Up` terlebih dahulu.
Fungsi `Sign Up` dijalankan dengan menggunakan kode berikut:
```javascript
$(document).ready(function(){
	
	$('#submit').click(function(){
		var user = $('#username').val();
		var pass = $('#password').val();

		var userdata = ('user=' + user + "&pass=" + pass);
		var check = false;

		if(user && pass){
			insertData(userdata);
		} else {
			alert('Username or password is empty.');
		}

		if(check){
			redirect(userdata);
		}

		function insertData(userdata){
			$.ajax({
					type: 'POST',
					url: 'http://127.0.0.1:3000/adduser',
					data: userdata, 
					success: function(data){
						alert(data);
						console.log(userdata);
					},
					error: function(){
						alert('gagal');
					}
			});
			console.log(userdata);
			return check = true;
		}

		function redirect(userdata){
			$.ajax({
					type: 'POST',
					url: 'http://127.0.0.1:3001/profile',
					data: userdata, 
					success: function(newData){
						console.log(userdata);
					},
					error: function(){
						alert('gagal kedua');
					}
			});
			window.location.replace("http://127.0.0.1:3001/profile");
		}
		
	})
});
```

* Setelah 

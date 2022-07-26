###### Nama : Ferdy Aridho Irawan
###### Kelas : XII RPL1
###### No Absen : 27

#  Modul 1
1. Lakukan proses instalasi framework laravel kedalam folder dengan nama masing-masing.

```
composer create-project laravel/laravel penjualan
```

# Modul 2
1. Buatlah migration tabel kategori dengan menggunakan teknik yang telah dipelajari dalam modul ini.

Langkah 1

```
php artisan make:migration create_kategori_table
```

Langkah 2
isikan kode dibawah ini kedalam file yg dibuat tadi
```
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('kategori', function (Blueprint $table) {
            $table->id();
            $table->string('nama');
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('kategori');
    }
};
```

Langkah 3
migrate data diatas dengan cara 
```
php artisan migrate
```

Langkah 4
membuat model barang dengan cara 
```
php artisan make:model kategori
```
isi kode dibawah ini pada file yg dibuat tadi
```
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class Kategori extends Model
{
    use HasFactory; 
    protected $table = 'kategori';
}
```

Langkah 5
membuat file seeder dengan cara 
```
php artisan make:seeder kategoriTableseeder
```
isi kode dibawah ini kedalam file yang dibuat tadi
```
<?php

namespace Database\Seeders;

use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;
use DB;

class kategoriTableSeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
        DB::table('kategori')->insert(array(
    
          [
            'nama' => 'perlengkapan sekolah'
          ],
         
          [
            'nama' => 'komputer'
          ],
       
          [
            'nama' => 'sabun'
          ],
          
          [
            'nama' => 'accesories'
          ],

          [
            'nama' => 'atk'
          ]  
    
          ));
}
}
```
lalu buka file 
```
DatabaseSeeder.php
```
dan masukkan kode ini
```
?php

namespace Database\Seeders;

// use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;


class DatabaseSeeder extends Seeder
{
    /**
     * Seed the application's database.
     *
     * @return void
     */
    public function run()
    {
        $this->call(barangTableSeeder::class);
        $this->call(kategoriTableSeeder::class);
    }
}
```
langkah 6
untuk mengeksekusi seeder masukkan seperti dibawah ini
```
php artisan db:seed
```

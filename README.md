# Validation-Laravel
## How to Customize Validation Laravel 

### Langkah Langkah mengcustom validasi form error di laravel
- Ketikan di Terminal `php artisan make:request ErrorFormRequest // -> hanya nama`

- lalu masuk ke dalam file request yang sudah di buat tadi
    - di dalam file yang di buat tadi, ubahlah `function authorize()` menjadi `true` = 
        - awlnya :
            ```php
            public function authorize()
            {
                return false;
            }
            ```
        - menjadi : 
            ```php
            public function authorize()
            {
                return true;
            }
            ```
    - Tambahkan di rule nya seperti berikut : 
    
        ```php
        public function rules()
        {
            return [
                'judul' => 'required',
                'tahun' => 'required', 
                'pengarang' => 'required',
                'halaman' => 'required',
            ];       
        }
        ```
    - Sesuaikan dengan name dari form anda

    - Kemudian buat `function message()` di bawah `function rules()` seperti berikut : 
        ```php
         public function messages()
        {
            return [
                'judul.required' => 'Isi Judul Dulu!!',
                'tahun.required' => 'Isi tahun Dulu!!',
                'pengarang.required' => 'Isi pengarang Dulu!!',
                'halaman.required' => 'Isi halaman Dulu!!',
            ];
        }
        ```
- lalu pindah ke file controller anda 
    - di file controller anda, use terlebih dahulu request yang anda buat tadi, seperti berikut : 
    ```php
    use App\Http\Requests\ErrorFromRequest;
    ```

    - lalu di bagian functiion dari insert data nya tepatnya di `function store()` tambahkan seperti ini : 
    ```php
    public function store(ErrorFromRequest $request)
    {
    // tidak ada tambahan fungsi yang special di sini!!!
    }
    ```


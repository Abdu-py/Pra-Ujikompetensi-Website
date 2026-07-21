# MODUL PANDUAN PRAKTIK UJIKOM
## Junior Web Developer — Aplikasi Marketplace (Laravel 11 + MySQL)
### Edisi "Anti Gagal" — Step-by-Step untuk Pemula Total

> Dokumen ini disusun berdasarkan soal resmi **FR.IA.02 — Tugas Praktik Demonstrasi** (Kelompok Pekerjaan 1: Melakukan Perancangan, dan Kelompok Pekerjaan 2: Menulis Kode Sumber) dan mengacu pada Modul Pelatihan instruktur. Semua fitur wajib pada soal sudah dipetakan satu per satu ke dalam langkah-langkah di bawah, termasuk 3 hal yang **tidak lengkap** di modul pelatihan lama:
> 1. Dashboard admin harus menampilkan **angka dinamis** (bukan angka statis/kosong) — total produk, kategori, pesanan.
> 2. Pembeli harus bisa **mencari produk** dan **memfilter berdasarkan kategori**.
> 3. Daftar pesanan harus mencatat **nomor HP pembeli**, bukan email.

---

## Cara Memakai Dokumen Ini

- Total waktu ujian: **60 menit mockup + 180 menit coding = 240 menit**.
- Setiap sub-bab diberi label waktu, misalnya **"[Menit 0–8]"**. Anggap itu seperti alarm — kalau sudah lewat, jangan berhenti, lanjut ke sub-bab berikutnya dan kembali nanti kalau masih ada sisa waktu.
- Simbol yang dipakai:
  - 💡 **Kenapa?** — penjelasan alasan/logika sebelum Anda mengetik apa pun.
  - ⚠️ **Awas** — titik rawan error, baca dua kali sebelum lanjut.
  - ✅ **Cek** — cara memverifikasi langkah tadi berhasil, sebelum lanjut ke langkah berikutnya.
  - 🩹 **Error & Obatnya** — tabel troubleshooting di akhir tiap sesi.
- Semua kode di bawah ini sudah diberi komentar bahasa Indonesia di hampir setiap baris. **Jangan hanya copy-paste** — baca komentarnya, karena assessor BNSP bisa saja bertanya "baris ini fungsinya apa?".

---

# BAGIAN A — MOCKUP / RANCANGAN UI (60 MENIT)

💡 **Kenapa mockup dulu, bukan langsung coding?**
Mockup adalah "cetak biru" rumah sebelum tukang mulai membangun. Assessor menilai apakah Anda paham *alur pengguna* (user flow) sebelum menyentuh kode. Jangan bikin mockup yang cantik tapi tidak sesuai kebutuhan soal — utamakan **kelengkapan halaman**, bukan keindahan.

Soal mensyaratkan **minimal 7 halaman** berikut. Tempel tabel ini di dekat layar Anda sebagai checklist real-time:

| # | Halaman Wajib | Sudah Dibuat? |
|---|---|---|
| 1 | Landing Page / Beranda (katalog produk pembeli) | ☐ |
| 2 | Login Admin | ☐ |
| 3 | Dashboard Admin (ringkasan total produk, kategori, pesanan) | ☐ |
| 4 | Manajemen Produk (tabel + tombol Tambah/Edit/Hapus) | ☐ |
| 5 | Manajemen Kategori | ☐ |
| 6 | Detail Produk (foto, deskripsi, harga, stok, form pesan) | ☐ |
| 7 | Daftar Pesanan (Order) sisi admin | ☐ |

## [Menit 0–5] Persiapan Alat Mockup

1. Buka aplikasi desain yang Anda kuasai: **Figma** (disarankan, gratis, berbasis web di figma.com), atau Canva/Sketch/Adobe XD jika lebih familiar.
2. Buat 1 file baru, beri nama misalnya `Marketplace-UjiKom-Mockup`.
3. Siapkan 7 "frame"/"board" kosong berukuran desktop (misalnya 1440×1024 px), satu frame per halaman wajib di atas. Beri nama tiap frame persis seperti nama di tabel checklist — ini memudahkan Anda dan assessor menelusuri.

✅ **Cek**: Anda punya 7 frame kosong bernama jelas sebelum mulai menggambar apa pun.

## [Menit 5–15] Frame 1: Landing Page / Beranda

💡 **Kenapa halaman ini penting?** Ini "etalase toko" — hal pertama yang dilihat pembeli. Soal mewajibkan: foto produk, nama, kategori, harga, **stok**, **kolom pencarian**, dan **filter kategori**.

Elemen wajib yang harus digambar (boleh berupa kotak/placeholder, tidak perlu detail pixel-perfect):
- Navbar atas: logo/nama toko + tombol "Login".
- Kolom pencarian (search box) dengan placeholder "Cari produk...".
- Dropdown/tombol filter kategori di sebelah kolom pencarian.
- Grid kartu produk (minimal 4 kartu contoh), tiap kartu berisi: gambar, nama produk, nama kategori, harga, sisa stok, tombol "Detail".

## [Menit 15–25] Frame 2: Login Admin

Elemen wajib:
- Form dengan 2 input: **Email** dan **Password**.
- Tombol "Login".
- (Opsional) Link kembali ke Landing Page.

💡 **Kenapa cuma 2 input?** Soal hanya minta autentikasi email+password untuk admin — jangan menambah kompleksitas (misal: lupa password, captcha) karena itu di luar cakupan penilaian dan memakan waktu mockup Anda.

## [Menit 25–35] Frame 3: Dashboard Admin

Elemen wajib — 3 **kartu statistik** besar berjejer di bagian atas:
- Kartu 1: "Total Produk" + angka contoh (misal 24).
- Kartu 2: "Total Kategori" + angka contoh (misal 5).
- Kartu 3: "Total Pesanan" + angka contoh (misal 12).

Di bawahnya, gambar sidebar menu kiri berisi: Dashboard, Kategori, Produk, Pesanan, Stok (ini akan jadi acuan navigasi di semua halaman admin lainnya — boleh Anda copy-paste frame sidebar yang sama ke Frame 4, 5, dan 7 supaya konsisten dan hemat waktu).

## [Menit 35–45] Frame 4 & 5: Manajemen Produk dan Manajemen Kategori

**Frame 4 — Manajemen Produk:**
- Sidebar yang sama seperti Dashboard.
- Tombol "+ Tambah Produk" di kanan atas.
- Tabel dengan kolom: No, Nama Produk, Kategori, Harga, Stok, Gambar (thumbnail kecil), Aksi (ikon Edit + Hapus).

**Frame 5 — Manajemen Kategori:**
- Sidebar yang sama.
- Tombol "+ Tambah Kategori".
- Tabel dengan kolom: No, Nama Kategori, Aksi (Edit + Hapus).

💡 **Tips hemat waktu**: Duplikat (Ctrl+D / Copy-Paste) frame 4 untuk jadi frame 5, lalu tinggal ubah kolom tabelnya. Jangan menggambar dari nol.

## [Menit 45–55] Frame 6 & 7: Detail Produk dan Daftar Pesanan

**Frame 6 — Detail Produk (sisi pembeli):**
- Gambar produk besar di kiri.
- Di kanan: nama produk, kategori, harga, sisa stok, deskripsi singkat.
- Form pemesanan di bawahnya dengan input: **Nama Pembeli**, **Nomor HP**, **Jumlah Pesan**, tombol "Pesan Sekarang".

⚠️ **Awas**: Soal secara eksplisit minta form berisi **nama** dan **nomor HP** — bukan akun login pembeli. Artinya pembeli **tidak wajib login** untuk memesan. Gambarkan sesuai ini agar mockup dan aplikasi nanti konsisten.

**Frame 7 — Daftar Pesanan (Order) — sisi admin:**
- Sidebar yang sama seperti dashboard.
- Tabel dengan kolom: No, Nama Pembeli, **Nomor HP**, Produk, Jumlah, Total Harga, Tanggal Pesan.

## [Menit 55–60] Ekspor dan Simpan

1. Di Figma: klik **Share → Anyone with the link → Can view**, salin link tersebut. Link ini nanti dicantumkan di laporan Word Anda.
2. Export juga versi PDF/PNG sebagai cadangan offline (`File → Export`), simpan di folder tugas Anda.
3. Centang ulang tabel checklist 7 halaman di atas — pastikan semua ☑ sebelum lanjut ke Bagian B.

🩹 **Error & Obatnya — Sesi Mockup**

| Gejala | Kemungkinan Penyebab | Perbaikan |
|---|---|---|
| Waktu 60 menit habis tapi belum semua frame selesai | Terlalu detail menggambar styling/warna | Prioritaskan kelengkapan elemen wajib dulu (checklist), styling boleh seadanya kotak-kotak |
| Link share Figma tidak bisa dibuka orang lain | Setting akses masih "Only me" | Ubah ke "Anyone with the link – Viewer" sebelum menyalin link |
| Lupa menandai frame mana yang halaman apa | Nama frame masih default ("Frame 1", dst) | Rename tiap frame sesuai tabel checklist di atas, langsung dari awal |


---

# BAGIAN B — CODING APLIKASI (180 MENIT)

Peta waktu keseluruhan (tempel juga di dekat layar):

| Waktu | Kegiatan |
|---|---|
| Menit 0–8 | Buat project Laravel baru |
| Menit 8–15 | Setup database & file `.env` |
| Menit 15–35 | Salin template starter + daftarkan middleware Admin ⚠️ **KRITIS** |
| Menit 35–50 | Migration tabel + Seeder akun admin |
| Menit 50–70 | CRUD Kategori |
| Menit 70–100 | CRUD Produk + upload gambar ⚠️ **KRITIS** |
| Menit 100–110 | Dashboard admin dengan angka otomatis |
| Menit 110–145 | Landing Page (cari+filter+detail+form pesan) + Daftar Pesanan Admin |
| Menit 145–160 | Manajemen Stok |
| Menit 160–172 | Testing menyeluruh pakai Ceklis Final |
| Menit 172–180 | Push ke GitHub + screenshot + laporan |

---

## [Menit 0–8] Membuat Proyek Laravel

💡 **Kenapa pakai Composer, bukan download zip?** Laravel terdiri dari ratusan file library (disebut *dependency*). Composer adalah "kurir otomatis" yang mengunduh dan menyusun semua file itu dengan versi yang saling cocok. Kalau di-download manual, besar kemungkinan versinya tidak sinkron dan aplikasi error sejak awal.

**Langkah (Windows):**
1. Nyalakan **Apache** dan **MySQL** lewat XAMPP Control Panel (tombol Start di kedua baris tersebut harus berwarna hijau).
2. Buka Command Prompt (CMD).
3. Masuk ke folder `htdocs` — ini folder khusus tempat XAMPP mencari website:
```bash
cd c:\xampp\htdocs
```
4. Jalankan perintah pembuatan proyek (nama proyek `ujikom-app`):
```bash
composer create-project laravel/laravel ujikom-app
```
5. Tunggu proses selesai (biasanya 2–5 menit tergantung koneksi internet).

**Langkah (macOS):** sama seperti di atas, hanya ganti langkah 2–3 dengan membuka Terminal dan `cd` ke folder proyek pilihan Anda, misalnya `cd Documents/ujikom-app-folder`.

✅ **Cek**: setelah selesai, folder `ujikom-app` berisi banyak folder seperti `app`, `routes`, `resources`, dll — bukan folder kosong.

## [Menit 8–15] Setup Database dan File `.env`

💡 **Apa itu file `.env`?** Bayangkan `.env` seperti **kunci rumah** — di situ tersimpan alamat, nama pengguna, dan password untuk menyambungkan kode Laravel Anda ke database MySQL. Tanpa kunci yang benar, aplikasi tidak bisa "masuk" ke database sama sekali (akan muncul error koneksi).

1. Buka browser, ketik `localhost/phpmyadmin`.
2. Klik menu **New/Baru**, ketik nama database persis: `ujikom-app`, klik **Create/Buat**.
3. Buka folder proyek `ujikom-app` di **VS Code** (`File → Open Folder`).
4. Di root proyek, cari file bernama `.env`. Buka file itu, cari baris-baris berikut dan ubah:

**Sebelum diubah (bawaan Laravel):**
```env
DB_CONNECTION=sqlite
# DB_HOST=127.0.0.1
# DB_PORT=3306
# DB_DATABASE=laravel
# DB_USERNAME=root
# DB_PASSWORD=
```

**Sesudah diubah:**
```env
DB_CONNECTION=mysql
# ^ Memberitahu Laravel: "pakai MySQL", bukan SQLite bawaan
DB_HOST=127.0.0.1
# ^ Alamat server database — 127.0.0.1 artinya "komputer ini sendiri" (localhost)
DB_PORT=3306
# ^ Nomor pintu (port) tempat MySQL XAMPP biasanya "mendengarkan"
DB_DATABASE=ujikom-app
# ^ Nama database yang tadi dibuat di phpMyAdmin — HARUS sama persis
DB_USERNAME=root
# ^ Username default MySQL bawaan XAMPP
DB_PASSWORD=
# ^ Dikosongkan karena XAMPP secara default tidak memberi password ke user root
```

⚠️ **Awas**: kalau MySQL XAMPP Anda memang di-setting pakai password (biasanya tidak, kecuali pernah diubah manual), isi `DB_PASSWORD=` dengan password tersebut. Kalau salah isi sedikit saja (misalnya nama database beda huruf besar/kecil), Laravel tidak akan bisa konek ke database.

✅ **Cek**: buka terminal di folder proyek, jalankan `php artisan migrate`. Jika muncul pesan sukses (bukan pesan "SQLSTATE" atau "Connection refused"), berarti `.env` sudah benar. (Nanti tabelnya akan kita ganti lagi di sesi Migration — ini baru tes koneksi.)

🩹 **Error & Obatnya — Sesi Setup**

| Gejala | Kemungkinan Penyebab | Perbaikan |
|---|---|---|
| `SQLSTATE[HY000] [1049] Unknown database` | Nama database di `.env` tidak sama dengan yang dibuat di phpMyAdmin | Buka phpMyAdmin, cek ejaan persis nama database, samakan dengan `DB_DATABASE` |
| `SQLSTATE[HY000] [2002] Connection refused` | MySQL di XAMPP belum di-Start | Buka XAMPP Control Panel, klik Start pada baris MySQL |
| Halaman putih/blank saat buka `localhost/ujikom-app/public` | Belum jalankan `php artisan serve`, atau salah folder | Gunakan `php artisan serve` lalu buka `http://127.0.0.1:8000` |

---

## [Menit 15–35] Menyalin Template Starter + Middleware Admin ⚠️ SANGAT KRITIS

Ini adalah bagian paling sering bikin error di ujian sebelumnya — luangkan waktu ekstra untuk teliti di sini.

### A. Unduh Template Starter

💡 **Kenapa perlu template?** Supaya Anda tidak perlu membuat tema admin (AdminLTE), sistem login/register, dan struktur folder dari nol — itu bisa memakan waktu berjam-jam. Template ini sudah menyediakan "kerangka rumah", tugas Anda tinggal menambahkan "furniturnya" (fitur marketplace).

1. Buka repositori: `https://github.com/ariefutsman/template-junior-web`.
2. Download ZIP (`Code → Download ZIP`) atau clone dengan `git clone https://github.com/ariefutsman/template-junior-web`.
3. Ekstrak ke folder **terpisah** dari `ujikom-app`, misalnya taruh di Desktop dengan nama folder `template-junior-web`.

### B. Tabel Perbandingan: Apa yang Disalin ke Mana

💡 **Kenapa pakai tabel ini?** Supaya Anda tidak salah taruh file — ini penyebab #1 munculnya error "Class not found" atau halaman blank.

| Dari folder `template-junior-web` | Salin ke folder `ujikom-app` | Cara: Timpa atau Gabung? |
|---|---|---|
| `app/Http/Controllers/Auth/` (isi: `LoginController.php`, `RegisterController.php`) | `app/Http/Controllers/Auth/` | **Timpa** (folder `Auth` belum ada di ujikom-app, jadi otomatis dibuat) |
| `app/Http/Controllers/FrontController.php`, `HomeController.php`, `UserController.php` | `app/Http/Controllers/` (langsung, TANPA subfolder) | **Gabung** — taruh berdampingan dengan `Controller.php` bawaan Laravel, jangan bikin subfolder baru |
| `app/Http/Middleware/IsAdmin.php` | `app/Http/Middleware/` (buat folder ini dulu jika belum ada) | **Gabung** |
| `app/Http/Requests/RegisterRequest.php`, `LoginRequest.php` | `app/Http/Requests/` | **Gabung** |
| `resources/views/includes/` (isi: `footer.blade.php`, `navbar.blade.php`, `sidebar.blade.php`) | `resources/views/includes/` | **Timpa** (folder ini baru, otomatis dibuat) |
| `resources/views/layouts/` (isi: `app.blade.php`, `auth.blade.php`, `front.blade.php`) | `resources/views/layouts/` | **Timpa** |
| `resources/views/pages/auth/` + `resources/views/pages/home.blade.php` | `resources/views/pages/` | **Gabung** |
| `public/css`, `public/dist`, `public/plugins` (isi tema AdminLTE — ukurannya besar) | `public/css`, `public/dist`, `public/plugins` | **Timpa total** — folder ini sudah ada bawaan Laravel isi minim, ganti sepenuhnya |
| `routes/web.php` | `routes/` | **Timpa total** — file ini sudah memuat semua rute yang kita perlukan sampai akhir modul |

⚠️ **Awas**: Setelah menyalin `routes/web.php`, Anda akan melihat baris seperti `use App\Http\Controllers\ProductController;` padahal file `ProductController.php` **belum Anda buat**. Ini **normal dan tidak akan error** saat ini — PHP baru memeriksa apakah sebuah class benar-benar ada saat rute itu **diakses/dibuka di browser**, bukan saat file `routes/web.php` sekadar dibaca oleh sistem. Controller-controller itu akan kita buat di sesi-sesi berikutnya.

Cara praktis menyalin: buka dua jendela VS Code berdampingan (`File → New Window`), satu untuk `template-junior-web`, satu untuk `ujikom-app`. Drag-drop folder/file sesuai tabel di atas via File Explorer (Windows) / Finder (Mac), bukan lewat VS Code, supaya proses copy folder besar (seperti `public/dist`) tidak lambat/hang.

✅ **Cek**: buka struktur folder `ujikom-app/app/Http/Controllers/` — harus ada `Auth/` (subfolder), lalu `FrontController.php`, `HomeController.php`, `UserController.php`, `Controller.php` sejajar (tanpa subfolder tambahan).

### C. Mendaftarkan Middleware `IsAdmin` di Laravel 11 ⚠️ TITIK PALING RAWAN ERROR 403

💡 **Apa itu Middleware dan kenapa sering error?** Middleware adalah "satpam" yang memeriksa setiap orang yang mau masuk ke halaman admin. `IsAdmin.php` isinya logika "kalau role user bukan admin, tendang balik ke halaman utama". Tapi satpam ini **tidak otomatis aktif** hanya karena filenya ada di folder — di Laravel 11, kita wajib "mendaftarkan" dia dengan sebuah **alias** (nama panggilan) di file `bootstrap/app.php`. Kalau lupa langkah ini, saat route memanggil `'is_admin'`, Laravel akan bingung "middleware apa itu?" dan biasanya berujung error 500 atau 403 (Forbidden) yang membingungkan pemula.

**Langkah persis:**

1. Pastikan isi `app/Http/Middleware/IsAdmin.php` (hasil salinan tadi) seperti ini:

```php
<?php

namespace App\Http\Middleware;

use Closure;
use Illuminate\Http\Request;
use Illuminate\Support\Facades\Auth; // WAJIB ADA — untuk mengecek siapa yang sedang login
use Symfony\Component\HttpFoundation\Response;

class IsAdmin
{
    /**
     * Fungsi ini dijalankan setiap kali ada request masuk ke rute yang memakai middleware ini.
     */
    public function handle(Request $request, Closure $next): Response
    {
        // Auth::check() -> true jika ada user yang sedang login
        // Auth::user()->role === 'admin' -> true jika role user tsb adalah admin
        if (Auth::check() && Auth::user()->role === 'admin') {
            // Jika keduanya benar, izinkan lanjut ke halaman yang dituju
            return $next($request);
        }
        // Jika bukan admin (atau belum login), tendang balik ke halaman utama + pesan error
        return redirect('/')->with('error', 'Akses ditolak.');
    }
}
```

2. Buka file `bootstrap/app.php` di root proyek `ujikom-app`. File ini biasanya baru berisi seperti:

```php
<?php

use Illuminate\Foundation\Application;
use Illuminate\Foundation\Configuration\Exceptions;
use Illuminate\Foundation\Configuration\Middleware;

return Application::configure(basePath: dirname(__DIR__))
    ->withRouting(
        web: __DIR__.'/../routes/web.php',
        commands: __DIR__.'/../routes/console.php',
        health: '/up',
    )
    ->withMiddleware(function (Middleware $middleware) {
        // <- BARIS INI BIASANYA MASIH KOSONG, DI SINI KITA TAMBAHKAN
    })
    ->withExceptions(function (Exceptions $exceptions) {
        //
    })->create();
```

3. Isi bagian `withMiddleware` menjadi seperti ini (JANGAN hapus baris lain, cukup tambahkan isi di dalam kurung kurawal):

```php
    ->withMiddleware(function (Middleware $middleware): void {
        // $middleware->alias() mendaftarkan "nama panggilan pendek" untuk sebuah class middleware
        // supaya bisa dipakai di routes/web.php cukup dengan menulis 'is_admin'
        $middleware->alias([
            'is_admin' => \App\Http\Middleware\IsAdmin::class,
        ]);
    })
```

⚠️ **Awas — 3 kesalahan paling umum di langkah ini:**
- Menaruh `$middleware->alias([...])` di **luar** fungsi `withMiddleware` — tidak akan terbaca.
- Salah ketik nama alias, misalnya menulis `is-admin` (pakai strip) padahal di `routes/web.php` dipanggil `is_admin` (pakai underscore) — alias harus **sama persis, case-sensitive**.
- Lupa tanda backslash `\` sebelum `App\Http\Middleware\IsAdmin::class` — ini menunjuk ke "root namespace" PHP, sering lupa ditulis kalau kode diketik manual.

✅ **Cek**: jalankan `php artisan route:list --name=admin` di terminal. Jika muncul daftar rute (`admin.dashboard`, dll.) tanpa pesan error merah, artinya middleware sudah terdaftar dengan benar secara teknis (fungsinya baru bisa diuji penuh setelah ada data user, di sesi berikutnya).

🩹 **Error & Obatnya — Sesi Template & Middleware**

| Gejala | Kemungkinan Penyebab | Perbaikan |
|---|---|---|
| `Target class [is_admin] does not exist` | Alias belum didaftarkan di `bootstrap/app.php`, atau typo nama alias | Cek ulang isi `withMiddleware`, pastikan alias `is_admin` persis sama dengan yang dipanggil di `routes/web.php` |
| Halaman admin bisa diakses oleh siapa saja (padahal belum login) | Middleware `is_admin` tidak dipasang di grup route admin | Cek `routes/web.php`, pastikan ada `Route::middleware(['auth','is_admin'])->prefix('admin')->group(...)` |
| Error 500 blank tanpa pesan jelas setelah edit `bootstrap/app.php` | Ada tanda kurung `{ }` atau `( )` yang tidak seimbang | Bandingkan ulang persis dengan contoh kode di atas, hitung jumlah kurung buka-tutup |
| `Class "App\Http\Controllers\ProductController" not found` saat buka `/admin/product` | Controller memang belum dibuat (ini WAJAR di tahap ini) | Lanjutkan ke sesi CRUD Produk — error ini hilang otomatis begitu controller dibuat |


---

## [Menit 35–50] Migration Tabel + Seeder Akun Admin

💡 **Apa itu Migration?** Migration adalah "resep" yang ditulis dalam kode PHP untuk membuat tabel di database — supaya struktur database Anda bisa dibuat ulang kapan saja tanpa perlu klik manual di phpMyAdmin, dan bisa di-share lewat GitHub bersama kode.

⚠️ **Catatan penting perubahan dari modul lama**: Soal FR.IA.02 meminta daftar pesanan mencatat **nomor HP pembeli**, dan form pemesanan **tidak mengharuskan pembeli login**. Karena itu tabel `orders` di bawah ini sengaja **tidak memakai email/alamat**, melainkan kolom `phone` (nomor HP) — dan datanya diisi langsung dari form, bukan dari akun yang sedang login.

### A. Tabel `users` (kolom tambahan `role`)

Laravel sudah otomatis membuat migration `users` bawaan. Kita hanya perlu **menambah kolom `role`**. Buat migration baru:
```bash
php artisan make:migration add_role_to_users_table --table=users
```
Buka file migration yang baru dibuat di `database/migrations/`, isi seperti ini:
```php
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    public function up(): void
    {
        Schema::table('users', function (Blueprint $table) {
            // Kolom baru untuk membedakan admin vs pembeli (kalau pembeli login/daftar akun)
            // default 'customer' supaya user yang daftar sendiri otomatis bukan admin
            $table->string('role')->default('customer')->after('password');
        });
    }

    public function down(): void
    {
        Schema::table('users', function (Blueprint $table) {
            $table->dropColumn('role');
        });
    }
};
```

### B. Tabel `categories`
```bash
php artisan make:migration create_categories_table
```
```php
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    public function up(): void
    {
        Schema::create('categories', function (Blueprint $table) {
            $table->id(); // Primary key otomatis, auto increment
            $table->string('category_name'); // Nama kategori, contoh: "Elektronik"
            $table->timestamps(); // Otomatis membuat kolom created_at & updated_at
            $table->softDeletes(); // Kolom deleted_at -> hapus "halus", data tidak benar-benar hilang
        });
    }

    public function down(): void
    {
        Schema::dropIfExists('categories');
    }
};
```

### C. Tabel `products`
```bash
php artisan make:migration create_products_table
```
```php
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    public function up(): void
    {
        Schema::create('products', function (Blueprint $table) {
            $table->id();
            $table->foreignId('category_id')->constrained();
            // foreignId + constrained() -> otomatis membuat relasi ke tabel categories.id
            // Artinya: setiap produk WAJIB terhubung ke satu kategori yang benar-benar ada
            $table->string('product_name'); // Nama produk
            $table->integer('price'); // Harga dalam rupiah (bilangan bulat, tanpa desimal)
            $table->integer('stock'); // Sisa stok barang
            $table->text('product_image'); // Menyimpan PATH/lokasi file gambar, bukan gambarnya sendiri
            $table->text('product_description'); // Deskripsi produk, teks panjang
            $table->timestamps();
            $table->softDeletes();
        });
    }

    public function down(): void
    {
        Schema::dropIfExists('products');
    }
};
```

### D. Tabel `orders` (SUDAH DISESUAIKAN dengan spek nomor HP)
```bash
php artisan make:migration create_orders_table
```
```php
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    public function up(): void
    {
        Schema::create('orders', function (Blueprint $table) {
            $table->id();
            $table->foreignId('product_id')->constrained();
            // Setiap pesanan menunjuk ke satu produk yang dipesan
            $table->string('name'); // Nama pembeli (diisi manual di form, TANPA perlu login)
            $table->string('phone'); // Nomor HP pembeli -- WAJIB sesuai soal FR.IA.02
            $table->integer('total_item'); // Jumlah barang yang dipesan
            $table->integer('total_price'); // Total harga = harga produk x jumlah
            $table->timestamps();
            $table->softDeletes();
        });
    }

    public function down(): void
    {
        Schema::dropIfExists('orders');
    }
};
```

⚠️ **Awas urutan**: karena `products` bergantung pada `categories`, dan `orders` bergantung pada `products`, migration harus dijalankan dengan urutan: categories → products → orders. Laravel otomatis mengurutkan berdasarkan **timestamp nama file** — karena Anda membuatnya berurutan seperti di atas, urutannya sudah otomatis benar. Jangan mengubah-ubah nama file migration secara manual.

Setelah keempat migration di atas dibuat, jalankan:
```bash
php artisan migrate
```
✅ **Cek**: buka `localhost/phpmyadmin`, klik database `ujikom-app`, pastikan muncul tabel `users` (dengan kolom `role` baru), `categories`, `products`, `orders`.

### E. Seeder Akun Admin

💡 **Kenapa perlu Seeder?** Supaya kita punya akun untuk login pertama kali tanpa harus daftar manual lewat form. Seeder = "menabur benih data" otomatis ke database.

```bash
php artisan make:seeder UserSeeder
```
Buka `database/seeders/UserSeeder.php`:
```php
<?php

namespace Database\Seeders;

use Illuminate\Database\Seeder;
use App\Models\User;

class UserSeeder extends Seeder
{
    public function run(): void
    {
        // Membuat akun admin -- role WAJIB ditulis eksplisit 'admin'
        // (kalau tidak ditulis, akan jatuh ke default 'customer' sesuai migration tadi)
        User::create([
            'name' => 'Admin',
            'email' => 'admin@gmail.com',
            'password' => bcrypt('password'), // bcrypt() -> mengenkripsi password, JANGAN simpan teks polos
            'role' => 'admin',
        ]);
    }
}
```
Jalankan:
```bash
php artisan db:seed --class=UserSeeder
```
✅ **Cek**: di phpMyAdmin, buka tabel `users`, pastikan ada 1 baris dengan email `admin@gmail.com` dan kolom `role` berisi `admin` (bukan `customer`).

Jalankan server dan coba login:
```bash
php artisan storage:link
php artisan serve
```
Buka `http://127.0.0.1:8000/login`, login pakai `admin@gmail.com` / `password`.

✅ **Cek**: setelah login berhasil, Anda diarahkan ke dashboard tanpa pesan "Akses ditolak". Jika muncul "Akses ditolak", berarti middleware atau role belum benar — cek tabel troubleshooting di bawah.

🩹 **Error & Obatnya — Sesi Migration & Seeder**

| Gejala | Kemungkinan Penyebab | Perbaikan |
|---|---|---|
| `SQLSTATE... foreign key constraint fails` saat migrate | Migration `products`/`orders` dijalankan sebelum tabel induknya ada | Jalankan `php artisan migrate:fresh` untuk mengulang dari awal dengan urutan yang benar |
| Setelah login, muncul "Akses ditolak" padahal pakai akun admin | Kolom `role` di database masih `customer` | Buka phpMyAdmin, edit manual baris user tsb, ubah `role` jadi `admin` |
| `Class "Database\Seeders\UserSeeder" not found` | Lupa `use App\Models\User;` di atas file Seeder | Tambahkan baris `use App\Models\User;` tepat di bawah `namespace` |
| Ingin mengulang migration dari nol (misal salah ketik kolom) | — | `php artisan migrate:fresh` lalu `php artisan db:seed --class=UserSeeder` lagi |

---

## [Menit 50–70] CRUD Kategori

💡 **Kenapa Kategori dibuat lebih dulu daripada Produk?** Karena tabel `products` **butuh** `category_id` yang valid (foreign key). Kalau kategori belum ada, kita tidak bisa membuat produk sama sekali nanti — jadi urutan pengerjaan ini bukan kebetulan.

### A. Model
```bash
php artisan make:model Category
```
`app/Models/Category.php`:
```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;
use Illuminate\Database\Eloquent\SoftDeletes;

class Category extends Model
{
    use HasFactory, SoftDeletes;

    // $fillable -> daftar kolom yang BOLEH diisi lewat Category::create([...])
    // Ini pengaman supaya orang tidak bisa menyuntik kolom lain secara sembarangan (mass assignment protection)
    protected $fillable = [
        'category_name'
    ];

    // Relasi: satu kategori PUNYA BANYAK produk
    public function products()
    {
        return $this->hasMany(Product::class);
    }
}
```

### B. Controller
```bash
php artisan make:controller CategoryController --resource
```
`app/Http/Controllers/CategoryController.php`:
```php
<?php

namespace App\Http\Controllers;

use App\Models\Category;
use Illuminate\Http\Request;

class CategoryController extends Controller
{
    // Menampilkan semua data kategori ke halaman index
    public function index()
    {
        $categories = Category::all(); // Ambil semua baris dari tabel categories
        return view('pages.category.index', compact('categories'));
        // compact('categories') -> mengirim variabel $categories ke file Blade
    }

    // Menyimpan kategori baru dari form
    public function store(Request $request)
    {
        $request->validate([
            'category_name' => 'required|string|max:255',
            // required -> wajib diisi, string -> harus teks, max:255 -> maksimal 255 karakter
        ]);

        Category::create([
            'category_name' => $request->category_name,
        ]);

        return redirect()->back()->with('success', 'Kategori berhasil ditambahkan.');
    }

    // Menghapus kategori berdasarkan id
    public function destroy($id)
    {
        Category::findOrFail($id)->delete();
        // findOrFail -> cari data, kalau tidak ketemu otomatis munculkan halaman 404
        return redirect()->back()->with('success', 'Kategori berhasil dihapus.');
    }
}
```

### C. View: `resources/views/pages/category/index.blade.php`

Buat folder `category` di dalam `resources/views/pages/`, lalu buat file `index.blade.php`:
```blade
@extends('layouts.app')
{{-- Memakai kerangka tampilan admin (sidebar+navbar) yang sudah ada di template --}}

@section('content')
<div class="content-header">
  <div class="container-fluid">
    <h1 class="m-0">Kategori Produk</h1>
  </div>
</div>

<section class="content">
  <div class="container-fluid">

    {{-- Menampilkan pesan sukses jika ada, misal setelah tambah/hapus --}}
    @if(session('success'))
      <div class="alert alert-success">{{ session('success') }}</div>
    @endif

    <div class="card">
      <div class="card-header">
        {{-- Tombol ini membuka modal (popup) tambah kategori, tidak pindah halaman --}}
        <button class="btn btn-primary" data-toggle="modal" data-target="#modalTambah">
          + Tambah Kategori
        </button>
      </div>
      <div class="card-body">
        <table class="table table-bordered">
          <thead>
            <tr>
              <th>No</th>
              <th>Nama Kategori</th>
              <th>Aksi</th>
            </tr>
          </thead>
          <tbody>
            {{-- $key dimulai dari 0, makanya ditambah 1 supaya nomor tampil dari 1 --}}
            @foreach($categories as $key => $item)
              <tr>
                <td>{{ $key + 1 }}</td>
                <td>{{ $item->category_name }}</td>
                <td>
                  <form action="{{ route('category.destroy', $item->id) }}" method="POST"
                        onsubmit="return confirm('Yakin hapus kategori ini?')">
                    @csrf
                    {{-- @csrf -> token keamanan wajib ada di SETIAP form POST Laravel --}}
                    @method('DELETE')
                    {{-- @method('DELETE') -> HTML form asli cuma bisa GET/POST,
                         baris ini "menyamar" jadi request DELETE sesuai standar REST Laravel --}}
                    <button class="btn btn-sm btn-danger" type="submit">Hapus</button>
                  </form>
                </td>
              </tr>
            @endforeach
          </tbody>
        </table>
      </div>
    </div>
  </div>
</section>

{{-- Modal (popup) form tambah kategori --}}
<div class="modal fade" id="modalTambah">
  <div class="modal-dialog">
    <div class="modal-content">
      <form action="{{ route('category.store') }}" method="POST">
        @csrf
        <div class="modal-header">
          <h5 class="modal-title">Tambah Kategori</h5>
          <button type="button" class="close" data-dismiss="modal">&times;</button>
        </div>
        <div class="modal-body">
          <label>Nama Kategori</label>
          <input type="text" name="category_name" class="form-control" required
                 placeholder="Contoh: Elektronik">
        </div>
        <div class="modal-footer">
          <button type="submit" class="btn btn-primary">Simpan</button>
        </div>
      </form>
    </div>
  </div>
</div>
@endsection
```

### D. Tambahkan Menu di Sidebar

Buka `resources/views/includes/sidebar.blade.php`, sisipkan blok berikut tepat di bawah menu Dashboard:
```blade
<li class="nav-item">
  <a href="{{ route('category.index') }}"
     class="nav-link {{ request()->routeIs('category.*') ? 'active' : '' }}">
    {{-- routeIs('category.*') -> menu otomatis "menyala" saat kita ada di halaman kategori manapun --}}
    <i class="nav-icon fas fa-tags"></i>
    <p>Kategori</p>
  </a>
</li>
```

💡 **Soal rute**: Ingat, `routes/web.php` yang kita salin di sesi sebelumnya **sudah** memuat `Route::resource('category', CategoryController::class);` — jadi begitu file `CategoryController.php` dan view di atas selesai dibuat, seluruh rute `/admin/category` langsung otomatis berfungsi tanpa perlu menambah baris rute apa pun lagi.

✅ **Cek**: buka `localhost:8000/admin/category`, coba tambah 2–3 kategori contoh (misal "Elektronik", "Fashion"), pastikan muncul di tabel, coba hapus salah satu.

🩹 **Error & Obatnya — Sesi CRUD Kategori**

| Gejala | Kemungkinan Penyebab | Perbaikan |
|---|---|---|
| Halaman putih / Error 500 saat buka `/admin/category` | Nama file view salah lokasi/nama (harus persis `pages/category/index.blade.php`) | Cek ulang path folder, huruf besar-kecil harus sama persis |
| Tombol Tambah tidak membuka popup | Template AdminLTE butuh jQuery/Bootstrap JS — file `public/dist`/`public/plugins` belum tersalin lengkap | Ulangi penyalinan folder `public/css`, `public/dist`, `public/plugins` dari template |
| `Call to a member function on null` | Data `$categories` tidak terkirim ke view (lupa `compact`) | Cek lagi `return view(..., compact('categories'))` di controller |
| Tombol hapus tidak berfungsi, halaman reload tapi data masih ada | Lupa `@method('DELETE')` di form | Tambahkan baris `@method('DELETE')` tepat setelah `@csrf` |


---

## [Menit 70–100] CRUD Produk + Upload Gambar ⚠️ SANGAT KRITIS

### A. Model
```bash
php artisan make:model Product
```
`app/Models/Product.php`:
```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;
use Illuminate\Database\Eloquent\SoftDeletes;

class Product extends Model
{
    use HasFactory, SoftDeletes;

    protected $fillable = [
        'category_id',
        'product_name',
        'price',
        'stock',
        'product_image',
        'product_description',
    ];

    // Relasi: satu produk MILIK satu kategori
    public function category()
    {
        return $this->belongsTo(Category::class);
    }
}
```

### B. Controller
```bash
php artisan make:controller ProductController --resource
```
`app/Http/Controllers/ProductController.php`:
```php
<?php

namespace App\Http\Controllers;

use App\Models\Product;
use App\Models\Category;
use Illuminate\Support\Facades\Storage;
use Illuminate\Http\Request;

class ProductController extends Controller
{
    // Menampilkan semua produk beserta nama kategorinya
    public function index()
    {
        // with('category') -> eager loading, supaya di view bisa panggil $product->category->category_name
        // TANPA ini, akan muncul error "Attempt to read property on null" kalau kategori tidak dimuat
        $products = Product::with('category')->get();
        $categories = Category::all(); // untuk dropdown pilihan kategori di form tambah/edit
        return view('pages.product.index', compact('products', 'categories'));
    }

    // Menyimpan produk baru, termasuk upload gambar
    public function store(Request $request)
    {
        $request->validate([
            'product_name' => 'required',
            'category_id' => 'required',
            'price' => 'required|numeric',
            'stock' => 'required|numeric',
            'product_image' => 'required|image|mimes:jpeg,png,jpg|max:2048',
            // image -> file harus berupa gambar, mimes -> hanya format ini yang diterima
            // max:2048 -> maksimal 2048 KB (2MB), supaya server tidak kepenuhan file besar
            'product_description' => 'required',
        ]);

        // Ambil file yang diunggah dari form
        $image = $request->file('product_image');
        // Simpan file ke folder storage/app/public/products, lalu simpan PATH-nya ke variabel
        $imagePath = $image->store('products', 'public');

        Product::create([
            'category_id' => $request->category_id,
            'product_name' => $request->product_name,
            'price' => $request->price,
            'stock' => $request->stock,
            'product_image' => $imagePath, // yang disimpan ke DB cuma PATH, bukan file gambarnya
            'product_description' => $request->product_description,
        ]);

        return redirect()->route('product.index')->with('success', 'Produk berhasil ditambahkan.');
    }

    // Menampilkan halaman form edit, sudah terisi data lama
    public function edit($id)
    {
        $product = Product::findOrFail($id);
        $categories = Category::all();
        return view('pages.product.edit', compact('product', 'categories'));
    }

    // Memproses perubahan data produk
    public function update(Request $request, $id)
    {
        $product = Product::findOrFail($id);

        $request->validate([
            'product_name' => 'required',
            'category_id' => 'required',
            'price' => 'required|numeric',
            'stock' => 'required|numeric',
            // TIDAK ada 'required' di product_image -> boleh kosong, artinya gambar lama dipertahankan
            'product_image' => 'image|mimes:jpeg,png,jpg|max:2048',
            'product_description' => 'required',
        ]);

        $data = [
            'category_id' => $request->category_id,
            'product_name' => $request->product_name,
            'price' => $request->price,
            'stock' => $request->stock,
            'product_description' => $request->product_description,
        ];

        // Cek apakah admin mengunggah gambar baru saat edit
        if ($request->hasFile('product_image')) {
            // Hapus gambar lama dulu supaya tidak menumpuk file "sampah" di server
            if ($product->product_image) {
                Storage::disk('public')->delete($product->product_image);
            }
            $image = $request->file('product_image');
            $data['product_image'] = $image->store('products', 'public');
        }

        $product->update($data);

        return redirect()->route('product.index')->with('success', 'Produk berhasil diperbarui.');
    }

    // Menghapus produk beserta file gambarnya
    public function destroy($id)
    {
        $product = Product::findOrFail($id);
        Storage::disk('public')->delete($product->product_image); // bersihkan file gambar juga
        $product->delete();
        return redirect()->back()->with('success', 'Produk berhasil dihapus.');
    }
}
```

💡 **Kenapa `create()` dan `show()` tidak diisi?** Karena form tambah produk kita buat langsung dalam bentuk **modal popup** di halaman index (tidak perlu halaman terpisah), jadi fungsi `create()` bawaan resource controller tidak dipakai. `show()` juga tidak dipakai di sisi admin karena detail produk sudah cukup terlihat di tabel.

### C. Storage Link — JANGAN SAMPAI LUPA

💡 **Kenapa harus jalankan `php artisan storage:link`?** Laravel menyimpan file upload di folder `storage/app/public/` yang **tersembunyi** dan tidak bisa diakses langsung lewat browser (demi keamanan). Perintah ini membuat sebuah **"jalan pintas" (symbolic link)** dari folder publik (`public/storage`) menuju folder tersembunyi tadi.

⚠️ **Kalau lupa langkah ini**: semua gambar produk akan tampil sebagai **ikon gambar rusak/broken image** di browser, padahal file-nya sebenarnya sudah tersimpan dengan benar di server — dan pemula sering bingung mengira upload-nya yang gagal.

Jalankan **satu kali saja** (biasanya cukup di awal proyek):
```bash
php artisan storage:link
```

✅ **Cek**: setelah dijalankan, harus muncul folder baru bernama `storage` di dalam folder `public/` proyek Anda (isinya bukan folder biasa, tapi "shortcut"/symlink).

### D. View: `resources/views/pages/product/index.blade.php`

Buat folder `product` di `resources/views/pages/`:
```blade
@extends('layouts.app')

@section('content')
<div class="content-header">
  <div class="container-fluid">
    <h1 class="m-0">Produk</h1>
  </div>
</div>

<section class="content">
  <div class="container-fluid">
    @if(session('success'))
      <div class="alert alert-success">{{ session('success') }}</div>
    @endif

    <div class="card">
      <div class="card-header">
        <button class="btn btn-primary" data-toggle="modal" data-target="#modalTambah">
          + Tambah Produk
        </button>
      </div>
      <div class="card-body">
        <table class="table table-bordered">
          <thead>
            <tr>
              <th>No</th><th>Nama</th><th>Kategori</th><th>Harga</th>
              <th>Stok</th><th>Gambar</th><th>Aksi</th>
            </tr>
          </thead>
          <tbody>
            @foreach($products as $key => $product)
              <tr>
                <td>{{ $key + 1 }}</td>
                <td>{{ $product->product_name }}</td>
                <td>{{ $product->category->category_name }}</td>
                <td>Rp {{ number_format($product->price, 0, ',', '.') }}</td>
                {{-- number_format(angka, 0 desimal, koma desimal, titik ribuan) -> format Rupiah --}}
                <td>{{ $product->stock }}</td>
                <td>
                  {{-- asset('storage/...') -> membaca file lewat symlink hasil storage:link tadi --}}
                  <img src="{{ asset('storage/' . $product->product_image) }}" width="80">
                </td>
                <td>
                  <a href="{{ route('product.edit', $product->id) }}" class="btn btn-sm btn-primary">Edit</a>
                  <form action="{{ route('product.destroy', $product->id) }}" method="POST"
                        class="d-inline" onsubmit="return confirm('Yakin hapus produk ini?')">
                    @csrf
                    @method('DELETE')
                    <button class="btn btn-sm btn-danger" type="submit">Hapus</button>
                  </form>
                </td>
              </tr>
            @endforeach
          </tbody>
        </table>
      </div>
    </div>
  </div>
</section>

<div class="modal fade" id="modalTambah">
  <div class="modal-dialog">
    {{-- enctype="multipart/form-data" WAJIB ada setiap kali form punya input type="file" --}}
    <form action="{{ route('product.store') }}" method="POST" enctype="multipart/form-data">
      @csrf
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title">Tambah Produk</h5>
          <button type="button" class="close" data-dismiss="modal">&times;</button>
        </div>
        <div class="modal-body">
          <label>Nama Produk</label>
          <input type="text" name="product_name" class="form-control mb-2" required>

          <label>Kategori</label>
          <select name="category_id" class="form-control mb-2" required>
            <option value="">-- Pilih Kategori --</option>
            @foreach($categories as $cat)
              <option value="{{ $cat->id }}">{{ $cat->category_name }}</option>
            @endforeach
          </select>

          <label>Harga</label>
          <input type="number" name="price" class="form-control mb-2" required>

          <label>Stok</label>
          <input type="number" name="stock" class="form-control mb-2" required>

          <label>Gambar Produk</label>
          <input type="file" name="product_image" class="form-control mb-2" required>

          <label>Deskripsi</label>
          <textarea name="product_description" class="form-control mb-2" required></textarea>
        </div>
        <div class="modal-footer">
          <button type="submit" class="btn btn-primary">Simpan</button>
        </div>
      </div>
    </form>
  </div>
</div>
@endsection
```

### E. View: `resources/views/pages/product/edit.blade.php`
```blade
@extends('layouts.app')

@section('content')
<div class="content-header">
  <div class="container-fluid"><h1 class="m-0">Edit Produk</h1></div>
</div>

<section class="content">
  <div class="container-fluid">
    <div class="card">
      <div class="card-body">
        <form action="{{ route('product.update', $product->id) }}" method="POST" enctype="multipart/form-data">
          @csrf
          @method('PUT')
          {{-- @method('PUT') -> menyamar sebagai request PUT, sesuai standar route resource Laravel untuk update --}}

          <label>Nama Produk</label>
          <input type="text" name="product_name" class="form-control mb-2"
                 value="{{ old('product_name', $product->product_name) }}">
          {{-- old('field', default) -> kalau validasi gagal sebelumnya, isi lama tetap muncul;
               kalau belum pernah gagal, pakai data produk yang sedang diedit --}}

          <label>Kategori</label>
          <select name="category_id" class="form-control mb-2">
            @foreach($categories as $cat)
              <option value="{{ $cat->id }}" {{ $product->category_id == $cat->id ? 'selected' : '' }}>
                {{ $cat->category_name }}
              </option>
            @endforeach
          </select>

          <label>Harga</label>
          <input type="number" name="price" class="form-control mb-2" value="{{ $product->price }}">

          <label>Stok</label>
          <input type="number" name="stock" class="form-control mb-2" value="{{ $product->stock }}">

          <label>Gambar Saat Ini</label><br>
          <img src="{{ asset('storage/' . $product->product_image) }}" width="120" class="mb-2"><br>
          <label>Ganti Gambar (kosongkan jika tidak ingin ganti)</label>
          <input type="file" name="product_image" class="form-control mb-2">

          <label>Deskripsi</label>
          <textarea name="product_description" class="form-control mb-2">{{ $product->product_description }}</textarea>

          <a href="{{ route('product.index') }}" class="btn btn-secondary">Batal</a>
          <button type="submit" class="btn btn-primary">Update</button>
        </form>
      </div>
    </div>
  </div>
</section>
@endsection
```

### F. Tambahkan Menu Sidebar
```blade
<li class="nav-item">
  <a href="{{ route('product.index') }}"
     class="nav-link {{ request()->routeIs('product.*') ? 'active' : '' }}">
    <i class="nav-icon fas fa-box"></i>
    <p>Produk</p>
  </a>
</li>
```

✅ **Cek menyeluruh sesi ini**:
1. Tambah 1 produk baru dengan foto — pastikan foto **tampil** (bukan broken image) di tabel.
2. Edit produk tanpa mengganti foto — pastikan foto lama tetap ada.
3. Edit produk dengan mengganti foto — buka folder `storage/app/public/products` di file explorer, pastikan file foto lama sudah terhapus (tidak menumpuk).
4. Hapus produk — pastikan hilang dari tabel dan dari database (cek phpMyAdmin, `deleted_at` akan terisi karena soft delete, itu normal).

🩹 **Error & Obatnya — Sesi CRUD Produk**

| Gejala | Kemungkinan Penyebab | Perbaikan |
|---|---|---|
| Gambar tampil sebagai ikon rusak (broken image) di semua produk | Lupa menjalankan `php artisan storage:link` | Jalankan perintah tersebut, lalu refresh browser |
| `The product_image field is required` padahal sudah pilih file | Form lupa `enctype="multipart/form-data"` | Tambahkan atribut tersebut di tag `<form>` |
| Error 500 "Attempt to read property 'category_name' on null" | Produk punya `category_id` yang kategorinya sudah terhapus, atau lupa `with('category')` | Pastikan `Product::with('category')->get()` dipakai di controller |
| Ukuran gambar besar ditolak sistem | Melebihi batas `max:2048` (2MB) di validasi | Kompres gambar dulu, atau naikkan angka `max:` di validasi (misal `max:5120` untuk 5MB) |
| Tombol Edit/Hapus tidak muncul rute-nya (`Route [product.edit] not defined`) | `Route::resource('product', ...)` di `routes/web.php` belum ada/terhapus | Cek ulang `routes/web.php`, pastikan baris resource tersebut ada |


---

## [Menit 100–110] Dashboard Admin dengan Angka Dinamis

⚠️ **Ini menutup celah dari modul lama.** Di modul pelatihan sebelumnya, rute dashboard hanya `return view('pages.home')` **tanpa mengirim data apa pun** — sehingga kalau soal minta "ringkasan total produk, kategori, pesanan", tampilan itu akan kosong/statis. Assessor pasti mengecek apakah angka ini **benar-benar berubah** saat data di database berubah (dinamis), bukan angka yang di-hardcode di HTML.

💡 **Caranya**: kita hitung jumlah baris di masing-masing tabel memakai `Model::count()`, lalu kirim ke view.

### A. Ubah Rute Dashboard di `routes/web.php`

Cari baris berikut (hasil salinan template):
```php
Route::get('/', function () {
    return view('pages.home');
})->name('admin.dashboard');
```
Ganti isinya menjadi:
```php
Route::get('/', function () {
    // Menghitung jumlah baris di masing-masing tabel secara real-time dari database
    $totalProduk = \App\Models\Product::count();
    $totalKategori = \App\Models\Category::count();
    $totalPesanan = \App\Models\Order::count();

    // Mengirim ketiga angka tadi ke view pages.home
    return view('pages.home', compact('totalProduk', 'totalKategori', 'totalPesanan'));
})->name('admin.dashboard');
```

💡 **Kenapa pakai closure (fungsi langsung), bukan Controller terpisah?** Karena logikanya sangat sederhana (cuma 3 baris hitung), tidak perlu dibuatkan file Controller baru — ini tetap dianggap "rapi" untuk kasus sesederhana ini. Kalau Anda ingin lebih rapi/sesuai best practice penuh, boleh juga dipindah ke `DashboardController@index`, caranya sama saja tinggal pindah 3 baris kode di atas ke dalam method controller.

### B. Tampilkan di View `resources/views/pages/home.blade.php`

Buka file tersebut, cari bagian `@section('content')`, tambahkan (atau ganti) dengan:
```blade
@extends('layouts.app')

@section('content')
<div class="content-header">
  <div class="container-fluid">
    <h1 class="m-0">Dashboard Admin</h1>
  </div>
</div>

<section class="content">
  <div class="container-fluid">
    <div class="row">
      {{-- Kartu statistik 1: Total Produk --}}
      <div class="col-lg-4 col-6">
        <div class="small-box bg-info">
          <div class="inner">
            <h3>{{ $totalProduk }}</h3>
            <p>Total Produk</p>
          </div>
          <div class="icon"><i class="fas fa-box"></i></div>
        </div>
      </div>

      {{-- Kartu statistik 2: Total Kategori --}}
      <div class="col-lg-4 col-6">
        <div class="small-box bg-success">
          <div class="inner">
            <h3>{{ $totalKategori }}</h3>
            <p>Total Kategori</p>
          </div>
          <div class="icon"><i class="fas fa-tags"></i></div>
        </div>
      </div>

      {{-- Kartu statistik 3: Total Pesanan --}}
      <div class="col-lg-4 col-6">
        <div class="small-box bg-warning">
          <div class="inner">
            <h3>{{ $totalPesanan }}</h3>
            <p>Total Pesanan</p>
          </div>
          <div class="icon"><i class="fas fa-shopping-cart"></i></div>
        </div>
      </div>
    </div>
  </div>
</section>
@endsection
```

✅ **Cek**: buka dashboard, angka harus sesuai jumlah data asli. Coba tambah 1 kategori baru lewat menu Kategori, lalu balik ke Dashboard — angka "Total Kategori" harus **bertambah otomatis**. Kalau angka tidak berubah, berarti masih ada sisa kode lama yang menampilkan angka statis (hardcode).

🩹 **Error & Obatnya — Sesi Dashboard**

| Gejala | Kemungkinan Penyebab | Perbaikan |
|---|---|---|
| `Undefined variable $totalProduk` | Lupa `compact('totalProduk', ...)` di rute, atau salah nama variabel antara rute dan view | Samakan persis nama variabel di kedua tempat |
| Angka selalu 0 padahal data sudah ada | Salah nama Model di-`count()`, atau namespace `\App\Models\...` kurang tepat | Cek ulang nama class model, pastikan sesuai dengan nama file di `app/Models/` |
| Dashboard blank/Error 500 | Order model (dibuat di sesi berikutnya) belum ada saat baris ini dipanggil | Pastikan Anda sudah menyelesaikan sesi Model Order sebelum menguji baris `Order::count()` ini |


---

## [Menit 110–145] Landing Page (Cari + Filter) + Detail Produk + Form Pesan + Daftar Pesanan Admin

Ini sesi terpanjang karena mencakup 5 fitur wajib sekaligus: katalog, pencarian, filter kategori, detail produk, form pemesanan, dan daftar pesanan admin. Kerjakan berurutan, jangan loncat-loncat.

### A. Model `Order`
```bash
php artisan make:model Order
```
`app/Models/Order.php`:
```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;
use Illuminate\Database\Eloquent\SoftDeletes;

class Order extends Model
{
    use HasFactory, SoftDeletes;

    protected $fillable = [
        'product_id',
        'name',       // nama pembeli
        'phone',      // nomor HP pembeli
        'total_item', // jumlah barang dipesan
        'total_price',
    ];

    // Relasi: satu pesanan menunjuk ke satu produk
    public function product()
    {
        return $this->belongsTo(Product::class);
    }
}
```

### B. Controller `OrderController` (khusus sisi admin — menampilkan daftar pesanan)
```bash
php artisan make:controller OrderController --resource
```
`app/Http/Controllers/OrderController.php` — cukup isi `index()`, sisanya boleh dibiarkan kosong bawaan:
```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
use App\Models\Order;

class OrderController extends Controller
{
    public function index()
    {
        // with('product') -> supaya bisa panggil $order->product->product_name di view
        // latest() -> urutkan dari pesanan paling baru di atas
        $orders = Order::with('product')->latest()->get();
        return view('pages.order.index', compact('orders'));
    }
}
```

### C. Update `FrontController` — Katalog + Search + Filter + Simpan Pesanan

💡 **Penjelasan fitur pencarian & filter**: kita memakai `$request->search` (isi kotak pencarian) dan `$request->category_id` (kategori yang dipilih). Query dasar `Product::query()` kita "tambahi syarat" secara bertahap **hanya kalau** parameter tersebut memang diisi pengguna — kalau kosong, syarat itu dilewati sehingga semua produk tetap tampil.

`app/Http/Controllers/FrontController.php`:
```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
use App\Models\Order;
use App\Models\Product;
use App\Models\Category;

class FrontController extends Controller
{
    // Menampilkan landing page/katalog, dengan dukungan pencarian & filter kategori
    public function index(Request $request)
    {
        $query = Product::with('category'); // mulai dari query dasar: semua produk + kategorinya

        // Jika pengguna mengisi kotak pencarian, tambahkan syarat WHERE nama produk mengandung kata itu
        if ($request->filled('search')) {
            // filled() -> true jika parameter ada DAN tidak kosong
            $query->where('product_name', 'like', '%' . $request->search . '%');
            // 'like' + tanda % -> mencari produk yang MENGANDUNG kata kunci, bukan harus sama persis
        }

        // Jika pengguna memilih kategori tertentu, tambahkan syarat WHERE category_id sama
        if ($request->filled('category_id')) {
            $query->where('category_id', $request->category_id);
        }

        $products = $query->get(); // eksekusi query, ambil hasil akhirnya
        $categories = Category::all(); // untuk menampilkan pilihan filter kategori di halaman

        return view('pages.front.index', compact('products', 'categories'));
    }

    // Menyimpan pesanan baru dari form di halaman detail produk
    // CATATAN: pembeli TIDAK perlu login, data nama & HP diambil langsung dari input form
    public function store(Request $request)
    {
        $product = Product::findOrFail($request->product_id);

        $request->validate([
            'product_id' => 'required|exists:products,id',
            // exists:products,id -> memastikan product_id yang dikirim benar-benar ada di tabel products
            'name' => 'required|string|max:255',
            'phone' => 'required|string|max:20',
            'total_item' => 'required|numeric|min:1|max:' . $product->stock,
            // max: diisi dinamis dari stok produk saat ini -> mencegah pesan melebihi stok
        ], [
            'total_item.max' => 'Maaf, jumlah pesanan melebihi stok yang tersedia (sisa: ' . $product->stock . ').',
        ]);

        Order::create([
            'product_id' => $product->id,
            'name' => $request->name,
            'phone' => $request->phone,
            'total_item' => $request->total_item,
            'total_price' => $product->price * $request->total_item, // hitung otomatis total harga
        ]);

        // Kurangi stok produk sebanyak jumlah yang dipesan -- INI SYARAT WAJIB DI SOAL
        $product->decrement('stock', $request->total_item);

        return redirect()->route('home-page')->with('success', 'Pesanan berhasil dikirim! Admin akan segera memproses.');
    }
}
```

⚠️ **Awas**: pastikan `use App\Models\Order;` dan `use App\Models\Category;` sudah ditambahkan di atas — ini penyebab umum error "Class not found" kalau lupa.

### D. View Landing Page: `resources/views/pages/front/index.blade.php`

```blade
@extends('layouts.front')

@section('content')
<div class="container mt-4">
  <h3>Katalog Produk</h3>

  {{-- Menampilkan pesan sukses setelah pesan berhasil dikirim --}}
  @if(session('success'))
    <div class="alert alert-success">{{ session('success') }}</div>
  @endif

  {{-- FORM PENCARIAN + FILTER KATEGORI --}}
  {{-- method GET (bukan POST) supaya kata kunci pencarian muncul di URL, bisa di-refresh/dibagikan --}}
  <form method="GET" action="{{ route('home-page') }}" class="row g-2 mb-4">
    <div class="col-md-6">
      <input type="text" name="search" class="form-control" placeholder="Cari nama produk..."
             value="{{ request('search') }}">
      {{-- request('search') -> menampilkan kembali kata kunci terakhir yang diketik, supaya tidak hilang saat refresh --}}
    </div>
    <div class="col-md-4">
      <select name="category_id" class="form-control">
        <option value="">-- Semua Kategori --</option>
        @foreach($categories as $cat)
          <option value="{{ $cat->id }}" {{ request('category_id') == $cat->id ? 'selected' : '' }}>
            {{ $cat->category_name }}
          </option>
        @endforeach
      </select>
    </div>
    <div class="col-md-2">
      <button type="submit" class="btn btn-primary w-100">Cari</button>
    </div>
  </form>

  <div class="row">
    @forelse($products as $product)
      <div class="col-md-3 mb-4">
        <div class="card h-100">
          <img src="{{ asset('storage/'.$product->product_image) }}" class="card-img-top" alt="{{ $product->product_name }}">
          <div class="card-body">
            <h5 class="card-title">{{ $product->product_name }}</h5>
            <p class="text-muted">{{ $product->category->category_name }}</p>
            <p>Rp {{ number_format($product->price, 0, ',', '.') }}</p>
            <p>Stok: {{ $product->stock }}</p>
            <button class="btn btn-sm btn-success w-100" data-bs-toggle="modal"
                    data-bs-target="#modalDetail{{ $product->id }}">
              Detail & Pesan
            </button>
          </div>
        </div>
      </div>

      {{-- MODAL DETAIL PRODUK + FORM PEMESANAN (berfungsi sebagai "Halaman Detail Produk") --}}
      <div class="modal fade" id="modalDetail{{ $product->id }}" tabindex="-1">
        <div class="modal-dialog modal-lg">
          <div class="modal-content">
            <div class="modal-header">
              <h5 class="modal-title">{{ $product->product_name }}</h5>
              <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
            </div>
            <div class="modal-body">
              <div class="row">
                <div class="col-md-6">
                  <img src="{{ asset('storage/'.$product->product_image) }}" class="img-fluid rounded">
                </div>
                <div class="col-md-6">
                  <p><strong>Kategori:</strong> {{ $product->category->category_name }}</p>
                  <p><strong>Harga:</strong> Rp {{ number_format($product->price, 0, ',', '.') }}</p>
                  <p><strong>Sisa Stok:</strong> {{ $product->stock }}</p>
                  <p>{{ $product->product_description }}</p>
                  <hr>
                  {{-- FORM PEMESANAN -- tanpa login, isi nama & nomor HP manual sesuai soal --}}
                  <form action="{{ route('marketplace.order.process') }}" method="POST">
                    @csrf
                    <input type="hidden" name="product_id" value="{{ $product->id }}">

                    <label>Nama Pembeli</label>
                    <input type="text" name="name" class="form-control mb-2" required>

                    <label>Nomor HP</label>
                    <input type="text" name="phone" class="form-control mb-2" required
                           placeholder="Contoh: 081234567890">

                    <label>Jumlah Pesan</label>
                    <input type="number" name="total_item" class="form-control mb-2"
                           value="1" min="1" max="{{ $product->stock }}" required>

                    <button type="submit" class="btn btn-primary w-100"
                            {{ $product->stock < 1 ? 'disabled' : '' }}>
                      {{ $product->stock < 1 ? 'Stok Habis' : 'Pesan Sekarang' }}
                    </button>
                  </form>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    @empty
      <p class="text-muted">Produk tidak ditemukan.</p>
    @endforelse
  </div>
</div>
@endsection
```

💡 **Kenapa pakai modal, bukan halaman `/produk/{id}` terpisah?** Secara fungsi, modal ini **sudah memenuhi** semua isi yang diminta soal untuk "Halaman Detail Produk" (foto, deskripsi, harga, stok, form pemesanan) — hanya beda cara render (popup vs. berpindah halaman). Ini pilihan hemat waktu yang aman untuk ujian 180 menit. Jika waktu Anda longgar, silakan kembangkan jadi halaman/rute terpisah `Route::get('/produk/{id}', ...)` dengan struktur HTML yang sama persis dipindah ke view baru.

### E. View Daftar Pesanan Admin: `resources/views/pages/order/index.blade.php`
```blade
@extends('layouts.app')

@section('content')
<div class="content-header">
  <div class="container-fluid"><h1 class="m-0">Daftar Pesanan</h1></div>
</div>

<section class="content">
  <div class="container-fluid">
    <div class="card">
      <div class="card-body">
        <table class="table table-bordered">
          <thead>
            <tr>
              <th>No</th><th>Nama Pembeli</th><th>Nomor HP</th>
              <th>Produk</th><th>Jumlah</th><th>Total Harga</th><th>Tanggal</th>
            </tr>
          </thead>
          <tbody>
            @forelse($orders as $key => $order)
              <tr>
                <td>{{ $key + 1 }}</td>
                <td>{{ $order->name }}</td>
                <td>{{ $order->phone }}</td>
                <td>{{ $order->product->product_name }}</td>
                <td>{{ $order->total_item }}</td>
                <td>Rp {{ number_format($order->total_price, 0, ',', '.') }}</td>
                <td>{{ $order->created_at->format('d-m-Y H:i') }}</td>
              </tr>
            @empty
              <tr><td colspan="7" class="text-center text-muted">Belum ada pesanan masuk.</td></tr>
            @endforelse
          </tbody>
        </table>
      </div>
    </div>
  </div>
</section>
@endsection
```

Tambahkan menu di sidebar admin:
```blade
<li class="nav-item">
  <a href="{{ route('admin.orders') }}"
     class="nav-link {{ request()->routeIs('admin.orders') ? 'active' : '' }}">
    <i class="nav-icon fas fa-shopping-cart"></i>
    <p>Pesanan</p>
  </a>
</li>
```

💡 **Rute sudah tersedia**: `Route::get('/orders', [OrderController::class, 'index'])->name('admin.orders');` dan `Route::post('/order/process', [FrontController::class, 'store'])->name('marketplace.order.process');` sudah ada sejak sesi penyalinan template — tidak perlu menambah rute baru.

✅ **Cek menyeluruh sesi ini**:
1. Buka landing page, ketik nama produk di kotak pencarian — pastikan hasil ter-filter benar.
2. Pilih kategori di dropdown filter — pastikan hanya produk kategori itu yang tampil.
3. Klik "Detail & Pesan" pada satu produk, isi nama + nomor HP + jumlah, submit.
4. Cek di phpMyAdmin tabel `products` — kolom `stock` produk tersebut harus **berkurang** sesuai jumlah yang dipesan.
5. Buka menu Pesanan di admin — pastikan data pesanan tadi (nama, nomor HP, produk, jumlah, total harga, tanggal) muncul benar.

🩹 **Error & Obatnya — Sesi Pemesanan & Pencarian**

| Gejala | Kemungkinan Penyebab | Perbaikan |
|---|---|---|
| Pencarian/filter tidak mengubah hasil apa pun | Form pencarian pakai `method="POST"` bukan `GET`, atau nama input tidak `search`/`category_id` | Pastikan `method="GET"` dan nama `name="search"` & `name="category_id"` persis |
| Stok tidak berkurang setelah pesan | Baris `$product->decrement('stock', ...)` terlewat/terhapus di `store()` | Cek ulang method `store()` di `FrontController`, pastikan baris itu ada sebelum `return redirect` |
| `SQLSTATE... Column not found: phone` | Migration `orders` lama (versi email) masih terpakai, migration baru belum di-*fresh* | Jalankan `php artisan migrate:fresh` lalu ulangi seeding admin |
| Modal tidak muncul saat klik "Detail & Pesan" | Bootstrap 5 JS belum termuat di `layouts/front.blade.php` | Cek file tersebut, pastikan script Bootstrap dari CDN tetap ada |
| Bisa pesan melebihi stok yang tersisa | Validasi `max:` di `store()` tidak jalan / value awal input `max` di HTML lain dengan validasi backend | Backend (`FrontController::store`) adalah validasi utama yang wajib benar; atribut `max` di HTML cuma bantuan tampilan |


---

## [Menit 145–160] Manajemen Stok

💡 **Kenapa tidak buat Controller/Model baru?** Karena fitur ini hanya "menambah angka" pada kolom `stock` yang sudah ada di tabel `products` — cukup tambahkan 2 fungsi baru ke `ProductController` yang sudah dibuat.

Buka `app/Http/Controllers/ProductController.php`, tambahkan 2 fungsi berikut di dalam class (sebelum kurung kurawal penutup `}` terakhir):
```php
    // Menampilkan halaman daftar stok semua produk
    public function stockIndex()
    {
        $products = Product::all();
        return view('pages.stock.index', compact('products'));
    }

    // Memproses penambahan stok manual oleh admin
    public function updateStock(Request $request, $id)
    {
        $request->validate([
            'penambahan' => 'required|numeric|min:1',
            // min:1 -> admin tidak bisa menambah stok dengan angka 0 atau negatif
        ]);

        $product = Product::findOrFail($id);
        // increment() -> menambahkan angka ke kolom stock yang SUDAH ADA, bukan menimpanya
        $product->increment('stock', $request->penambahan);

        return redirect()->back()->with('success', 'Stok berhasil diperbarui.');
    }
```

Buat view `resources/views/pages/stock/index.blade.php`:
```blade
@extends('layouts.app')

@section('content')
<div class="content-header">
  <div class="container-fluid"><h1 class="m-0">Manajemen Stok</h1></div>
</div>

<section class="content">
  <div class="container-fluid">
    @if(session('success'))
      <div class="alert alert-success">{{ session('success') }}</div>
    @endif
    <div class="card">
      <div class="card-body">
        <table class="table table-bordered">
          <thead>
            <tr><th>No</th><th>Nama Produk</th><th>Stok Saat Ini</th><th>Tambah Stok</th><th>Aksi</th></tr>
          </thead>
          <tbody>
            @foreach($products as $key => $product)
              <tr>
                <td>{{ $key + 1 }}</td>
                <td>{{ $product->product_name }}</td>
                <td>{{ $product->stock }}</td>
                <form action="{{ route('admin.stock.update', $product->id) }}" method="POST">
                  @csrf
                  <td>
                    <input type="number" name="penambahan" class="form-control" placeholder="0" required min="1">
                  </td>
                  <td>
                    <button type="submit" class="btn btn-sm btn-primary">Simpan</button>
                  </td>
                </form>
              </tr>
            @endforeach
          </tbody>
        </table>
      </div>
    </div>
  </div>
</section>
@endsection
```

Tambahkan menu sidebar:
```blade
<li class="nav-item">
  <a href="{{ route('admin.stock') }}"
     class="nav-link {{ request()->routeIs('admin.stock') ? 'active' : '' }}">
    <i class="nav-icon fas fa-warehouse"></i>
    <p>Stok</p>
  </a>
</li>
```

💡 **Rute sudah tersedia**: `Route::get('/stock', [ProductController::class, 'stockIndex'])->name('admin.stock');` dan `Route::post('/stock/update/{id}', [ProductController::class, 'updateStock'])->name('admin.stock.update');` sudah ada sejak sesi penyalinan template.

✅ **Cek**: buka menu Stok, tambahkan angka 5 pada suatu produk, submit, pastikan kolom "Stok Saat Ini" bertambah 5 dari nilai sebelumnya (bukan berubah jadi 5).

🩹 **Error & Obatnya — Sesi Manajemen Stok**

| Gejala | Kemungkinan Penyebab | Perbaikan |
|---|---|---|
| Stok malah jadi angka yang diketik (bukan ditambah) | Salah pakai `update()` alih-alih `increment()` | Pastikan memakai `$product->increment('stock', $request->penambahan);` |
| Error "Route [admin.stock.update] not defined" | Nama route di form (`route('admin.stock.update', ...)`) tidak sama dengan yang di `routes/web.php` | Cek ejaan nama route persis sama di kedua tempat |

---

## [Menit 160–172] Testing Menyeluruh

Lakukan alur pengujian ini secara berurutan seperti pengguna sungguhan — jangan hanya cek satu-satu terpisah, karena assessor BNSP sering menguji **alur end-to-end**:

1. Logout dari akun admin (jika sedang login).
2. Buka landing page sebagai "pembeli" — cari produk, filter kategori, buka detail, lakukan 1 pemesanan.
3. Login sebagai admin — cek dashboard, apakah "Total Pesanan" bertambah 1.
4. Buka menu Pesanan — pastikan data pesanan tadi (nama, HP, produk, jumlah, total, tanggal) muncul benar.
5. Buka menu Produk — pastikan stok produk yang dipesan tadi sudah berkurang.
6. Tambah kategori baru, lalu tambah produk baru dengan kategori tersebut, pastikan muncul di landing page.
7. Edit salah satu produk (ubah harga & ganti gambar), pastikan perubahan tersimpan.
8. Hapus salah satu kategori yang **tidak dipakai** produk manapun, pastikan berhasil.
9. Tambah stok manual di menu Stok, cek angka bertambah benar.
10. Logout, coba akses langsung URL `/admin/product` tanpa login — pastikan **ditolak/redirect**, bukan malah bisa masuk (ini menguji middleware `is_admin` benar-benar bekerja).

## [Menit 172–180] Push ke GitHub, Screenshot, dan Laporan

1. Di terminal folder proyek:
```bash
git init
git add .
git commit -m "Aplikasi Marketplace UjiKom - Junior Web Developer"
```
2. Buat repository baru di GitHub (jangan centang "Add README"), lalu hubungkan dan push:
```bash
git remote add origin https://github.com/USERNAME_ANDA/ujikom-app.git
git branch -M main
git push -u origin main
```
⚠️ **Awas**: pastikan file `.env` **tidak ikut ter-upload** ke GitHub (berisi info sensitif). Laravel sudah otomatis menaruh `.env` di `.gitignore`, jadi seharusnya aman secara default — cukup pastikan Anda tidak menghapus/mengubah isi `.gitignore` bawaan.
3. Ambil screenshot tiap halaman utama (landing page, login, dashboard, kategori, produk, detail+form pesan, daftar pesanan, stok).
4. Buat laporan di Ms. Word berisi: link GitHub, link mockup Figma, dan seluruh screenshot tadi, lalu upload sesuai instruksi soal ke `https://lspmi.co.id`.

🩹 **Error & Obatnya — Sesi Push GitHub**

| Gejala | Kemungkinan Penyebab | Perbaikan |
|---|---|---|
| `.env` ikut ter-push ke GitHub | `.gitignore` sempat terhapus/diedit | Hapus file dari histori: `git rm --cached .env`, commit ulang, pastikan `.env` ada di `.gitignore` |
| `failed to push some refs` | Repository GitHub sudah ada isi (README) yang bentrok dengan commit lokal | `git pull origin main --allow-unrelated-histories` lalu push ulang |
| Folder `vendor/` atau `node_modules/` ikut ter-push (berat & lama) | `.gitignore` bawaan Laravel terhapus | Pastikan pakai `.gitignore` bawaan Laravel yang sudah otomatis mengecualikan folder tersebut |

---

# ✅ CEKLIS FINAL KELULUSAN

Sebelum submit, centang satu per satu. Untuk setiap poin, sudah disertakan **cara mengecek** persisnya.

| # | Fitur Wajib (sesuai FR.IA.02) | Cara Mengecek | ☑ |
|---|---|---|---|
| 1 | Admin bisa login (email + password) | Buka `/login`, masuk dengan `admin@gmail.com`/`password`, harus masuk ke dashboard tanpa error | ☐ |
| 2 | Dashboard menampilkan total produk, kategori, pesanan (dinamis) | Tambah 1 kategori baru, kembali ke dashboard, angka "Total Kategori" harus ikut bertambah | ☐ |
| 3 | Admin bisa Tambah/Edit/Hapus Kategori | Di phpMyAdmin, buka tabel `categories`, cocokkan jumlah baris dengan yang tampil di menu Kategori | ☐ |
| 4 | Admin bisa Tambah/Edit/Hapus Produk (dengan upload gambar) | Tambah produk baru dengan foto, pastikan foto tampil (bukan broken image) di tabel produk | ☐ |
| 5 | Admin bisa menambah stok produk (Manajemen Stok) | Tambah stok 5 pada satu produk, pastikan angka bertambah (bukan menimpa) di phpMyAdmin | ☐ |
| 6 | Admin bisa melihat daftar pesanan (nama, nomor HP, produk, jumlah, total harga, tanggal) | Buka menu Pesanan, pastikan semua 6 kolom tersebut terisi data benar | ☐ |
| 7 | Pembeli bisa melihat katalog di Landing Page (foto, nama, kategori, harga, stok) | Buka landing page tanpa login, pastikan semua elemen tsb tampil di tiap kartu produk | ☐ |
| 8 | Pembeli bisa mencari produk berdasarkan nama | Ketik sebagian nama produk di kotak pencarian, pastikan hasil ter-filter sesuai | ☐ |
| 9 | Pembeli bisa memfilter produk berdasarkan kategori | Pilih satu kategori di dropdown filter, pastikan hanya produk kategori itu yang tampil | ☐ |
| 10 | Pembeli bisa melihat Detail Produk (foto, deskripsi, harga, stok) | Klik "Detail & Pesan" pada produk, pastikan semua info tersebut lengkap di modal/halaman | ☐ |
| 11 | Pembeli bisa memesan (isi nama, nomor HP, jumlah) TANPA harus login | Logout dulu, coba lakukan pemesanan sebagai pengunjung anonim, pastikan berhasil | ☐ |
| 12 | Stok produk otomatis berkurang setelah pemesanan berhasil | Cek kolom `stock` di phpMyAdmin sebelum & sesudah memesan, harus berkurang sesuai jumlah | ☐ |
| 13 | Middleware admin benar-benar melindungi halaman admin | Logout, coba akses langsung `/admin/product` lewat URL, harus ditolak/redirect | ☐ |
| 14 | Setiap fungsi/kode diberi komentar penjelasan | Buka ulang tiap file Controller & Model, pastikan ada komentar bahasa Indonesia di baris-baris penting | ☐ |
| 15 | Kode sudah di-push ke GitHub, `.env` tidak ikut ter-upload | Buka repo GitHub Anda di browser, pastikan file `.env` **tidak terlihat** dalam daftar file | ☐ |
| 16 | Mockup UI (7 halaman wajib) sudah selesai dan link-nya siap | Buka kembali link Figma, pastikan bisa diakses orang lain (viewer) | ☐ |
| 17 | Laporan Word (link GitHub + link mockup + screenshot) sudah disusun dan diupload ke lspmi.co.id | Buka file laporan, pastikan semua link bisa diklik dan screenshot jelas terbaca | ☐ |

Jika **semua baris di atas sudah ☑**, aplikasi Anda sudah memenuhi seluruh kriteria unjuk kerja pada soal FR.IA.02. Selamat mengerjakan UjiKom! 🎉

# Langkah-Langkah Pembuatan Aplikasi Marketplace Online
### Laravel 11 + MySQL — TPD J.620100.010–019 (Menulis Kode Sumber)

Panduan ini mengacu pada soal **Tugas Praktik Demonstrasi Kelompok Pekerjaan 2** dan mockup UI (`ujikom-app.drawio`) yang berisi 7 halaman: Login, Dashboard Admin, Kategori, Produk, Pesanan, Stok, dan Lihat Marketplace.

---

## 0. Ringkasan Kebutuhan

**Aktor:**
- **Admin** — login, dashboard ringkasan, CRUD Kategori, CRUD Produk, Manajemen Stok, List Pesanan.
- **Pembeli** — landing page/katalog, cari produk, filter kategori, detail produk, form pemesanan (stok otomatis berkurang).

**Stack:** Laravel 11, MySQL, Blade (boleh + Tailwind/Bootstrap), Laravel Breeze/Fortify untuk auth admin.

---

## 1. Persiapan Proyek

```bash
composer create-project laravel/laravel marketplace-app
cd marketplace-app
composer require laravel/breeze --dev
php artisan breeze:install blade
npm install && npm run build
```

1. Buat database MySQL, misal `marketplace_db`.
2. Isi `.env`:
   ```
   DB_DATABASE=marketplace_db
   DB_USERNAME=root
   DB_PASSWORD=
   ```
3. Jalankan repo git & buat repository GitHub (nanti untuk laporan):
   ```bash
   git init
   git add .
   git commit -m "init laravel project"
   git remote add origin <url-repo-github-anda>
   git push -u origin main
   ```

---

## 2. Desain Database (Migration)

Buat migration untuk masing-masing tabel:

```bash
php artisan make:model Category -m
php artisan make:model Product -m
php artisan make:model Order -m
```

**`categories`**
| Kolom | Tipe |
|---|---|
| id | bigIncrements |
| name | string |
| timestamps | |

**`products`**
| Kolom | Tipe |
|---|---|
| id | bigIncrements |
| category_id | foreignId → categories |
| name | string |
| description | text |
| price | decimal(12,2) |
| stock | integer default 0 |
| photo | string (path gambar) |
| timestamps | |

**`orders`**
| Kolom | Tipe |
|---|---|
| id | bigIncrements |
| product_id | foreignId → products |
| buyer_name | string |
| buyer_phone | string |
| quantity | integer |
| total_price | decimal(12,2) |
| order_date | timestamp |
| timestamps | |

> Komentari setiap kolom migration dengan `// deskripsi field` sesuai guideline penulisan kode di soal.

Jalankan:
```bash
php artisan migrate
```

Tabel `users` bawaan Breeze dipakai untuk akun **Admin** (tidak perlu tabel role terpisah kalau hanya 1 admin; bila perlu bedakan role, tambahkan kolom `role` string default `admin`).

---

## 3. Model & Relasi

- `Product belongsTo Category`
- `Category hasMany Product`
- `Order belongsTo Product`

Definisikan `$fillable`, relasi, dan tambahkan komentar docblock di setiap method sesuai best practice.

---

## 4. Autentikasi Admin (Login)
*Mockup: `D-Login`*

1. Breeze sudah menyediakan `LoginController`/`AuthenticatedSessionController`, form Login (email + password), dan middleware `auth`.
2. Batasi akses: hanya user dengan role admin yang boleh masuk ke route `/admin/*` — buat middleware `IsAdmin`:
   ```bash
   php artisan make:middleware IsAdmin
   ```
   Daftarkan di `bootstrap/app.php` (Laravel 11 style) sebagai alias `admin`.
3. Setelah login sukses, redirect ke `/admin/dashboard`.
4. Buat seeder akun admin default:
   ```bash
   php artisan make:seeder AdminSeeder
   php artisan db:seed --class=AdminSeeder
   ```

---

## 5. Dashboard Admin
*Mockup: `D-Dashboard-Admin`*

Route: `GET /admin/dashboard` → `DashboardController@index`

Tampilkan ringkasan:
- Total produk: `Product::count()`
- Total kategori: `Category::count()`
- Total pesanan masuk: `Order::count()`
- (opsional) pesanan terbaru: `Order::latest()->take(5)->get()`

---

## 6. Manajemen Kategori (Admin)
*Mockup: `D-Kategori`*

Resource controller CRUD:
```bash
php artisan make:controller Admin/CategoryController --resource
```
Route resource: `Route::resource('admin/categories', CategoryController::class)`

- Index — tabel daftar kategori + tombol Tambah/Edit/Hapus.
- Store/Update — validasi `name` required, unique.
- Destroy — cegah hapus kategori yang masih dipakai produk (validasi/relasi restrict), tampilkan pesan error yang jelas.

---

## 7. Manajemen Produk (Admin)
*Mockup: `D-Produk`*

```bash
php artisan make:controller Admin/ProductController --resource
```

- Form Tambah/Edit: nama, kategori (dropdown dari `Category::all()`), deskripsi, harga, stok, upload foto produk (`Storage::disk('public')`).
- Index: tabel produk + kolom stok + tombol Tambah/Edit/Hapus.
- Validasi: `price` numeric, `stock` integer min:0, `photo` image max 2MB.
- Jangan lupa `php artisan storage:link` agar foto bisa diakses publik.

---

## 8. Manajemen Stok Produk (Admin)
*Mockup: `D-Stok`*

Fitur tambahan stok manual, terpisah dari form edit produk agar sesuai soal ("penambahan stok manual oleh admin"):

Route: `POST /admin/products/{product}/add-stock`

```php
// Menambah stok produk secara manual oleh admin
public function addStock(Request $request, Product $product)
{
    $request->validate(['amount' => 'required|integer|min:1']);
    $product->increment('stock', $request->amount);
    return back()->with('success', 'Stok berhasil ditambahkan');
}
```

---

## 9. List Pesanan / Order (Admin)
*Mockup: `D-Pesanan`*

Route: `GET /admin/orders` → `OrderController@index`

Tabel menampilkan: nama pembeli, no. HP, produk, jumlah, total harga, tanggal — urutkan terbaru dulu, boleh tambahkan filter tanggal/produk.

---

## 10. Landing Page / Katalog (Pembeli)
*Mockup: `D-Lihat-Market-Place`*

Route: `GET /` → `MarketplaceController@index`

- Tampilkan grid produk: foto, nama, kategori, harga, stok.
- **Pencarian**: `Product::where('name', 'like', "%$q%")`
- **Filter kategori**: `Product::when($categoryId, fn($q) => $q->where('category_id', $categoryId))`
- Gunakan pagination (`->paginate(12)`).

---

## 11. Detail Produk & Form Pemesanan (Pembeli)

Route: `GET /produk/{product}` → `MarketplaceController@show`
Route: `POST /produk/{product}/order` → `MarketplaceController@order`

- Halaman detail: foto besar, deskripsi, harga, stok, form pemesanan (nama pembeli, no. HP, jumlah).
- Saat submit, dalam **DB transaction**:
  ```php
  DB::transaction(function () use ($product, $request) {
      if ($product->stock < $request->quantity) {
          throw ValidationException::withMessages(['quantity' => 'Stok tidak mencukupi']);
      }
      Order::create([...]);
      $product->decrement('stock', $request->quantity);
  });
  ```
- Tampilkan halaman/notifikasi sukses setelah pesanan berhasil dibuat.

---

## 12. Gambar Produk

Gunakan gambar bebas hak cipta (mis. Unsplash, Pexels, Pixabay) sesuai instruksi soal, atau unggah gambar hasil desain sendiri. Simpan referensi sumber gambar bila diperlukan untuk laporan.

---

## 13. Rapikan Kode (sesuai penilaian J.620100.015/016/017)

- Ikuti struktur folder default Laravel (Controllers per aktor: `Admin/`, `Marketplace/`).
- Terapkan **PSR-12**: `./vendor/bin/pint`
- Gunakan **Form Request** (`php artisan make:request StoreProductRequest`) untuk validasi kompleks, bukan validasi manual di controller.
- Beri komentar/docblock pada setiap fungsi (tujuan, parameter, return).
- Gunakan named routes (`route('admin.products.index')`), hindari hardcode URL di Blade.

---

## 14. Testing Manual (checklist sebelum submit)

- [ ] Login admin berhasil & gagal (email/password salah)
- [ ] Dashboard menampilkan angka yang benar
- [ ] CRUD kategori lengkap (create/read/update/delete)
- [ ] CRUD produk lengkap termasuk upload foto
- [ ] Tambah stok manual berfungsi
- [ ] List pesanan tampil & terurut
- [ ] Landing page menampilkan katalog produk
- [ ] Pencarian & filter kategori berfungsi
- [ ] Detail produk menampilkan data lengkap
- [ ] Form pemesanan berhasil & stok otomatis berkurang
- [ ] Validasi stok tidak mencukupi ditangani dengan baik

---

## 15. Deploy / Push ke GitHub & Laporan

1. Pastikan `.env` **tidak** ikut ter-commit (cek `.gitignore`).
2. Push kode final ke GitHub:
   ```bash
   git add .
   git commit -m "final: marketplace app admin & buyer flow"
   git push
   ```
3. Buat laporan **Ms. Word** yang berisi:
   - Link repository GitHub aplikasi
   - Link file rancangan/mockup (drawio/Figma/Canva)
   - Screenshot tampilan aplikasi (semua halaman utama)
4. Upload laporan ke **https://lspmi.co.id** sesuai instruksi soal.

---

### Referensi Halaman Mockup ↔ Fitur

| File Mockup (drawio) | Fitur Terkait |
|---|---|
| D-Login | Autentikasi Admin |
| D-Dashboard-Admin | Ringkasan total produk/kategori/pesanan |
| D-Kategori | CRUD Kategori |
| D-Produk | CRUD Produk |
| D-Stok | Manajemen stok manual |
| D-Pesanan | List pesanan masuk |
| D-Lihat-Market-Place | Landing page, pencarian, filter, detail produk, form pemesanan |

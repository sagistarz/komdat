<h1 align="center"><img src="https://1.bp.blogspot.com/-3za0XKJuLSc/WNfUgBtwwFI/AAAAAAAAGiQ/ADAfpkEiUn0w6FHDjMpt-i3PzYyMBtNQQCLcB/s1600/1.png"></h1>

[Sekilas Tentang](#sekilas-tentang) | [Instalasi](#instalasi) | [Cara Pemakaian](#cara-pemakaian) | [Pembahasan](#pembahasan) | [Referensi](#referensi)
:---:|:---:|:---:|:---:|:---:



# Sekilas Tentang
[`^ kembali ke atas ^`](#)

[FocusStopWatch](https://github.com/hilmyveradin/focusstopwatch-vue) merupakan sebuah aplikasi web yang telah dirancang dengan tujuan utama untuk melakukan pemantauan dan pencatatan secara cermat mengenai sejauh mana kemampuan seseorang dalam menjaga tingkat fokusnya sebelum akhirnya mengalami distraksi atau kehilangan konsentrasi.

# Instalasi
[`^ kembali ke atas ^`](#)

#### Kebutuhan Sistem :
- Unix, Linux atau Windows.
- Apache Web server 1.3+.
- PHP 5.2+.
- MySQL 5.0+.
- RAM minimal 64 Mb+

#### Proses Instalasi :
1. Setup Docker via DockerFile.
   ```
    # Step 1: Build the Vue.js application
    FROM node:17 as build-stage
    WORKDIR /app
    COPY package*.json ./
    RUN npm install
    COPY . .
    RUN npm run build
    
    # Step 2: Serve the app with Nginx
    FROM nginx:stable-alpine as production-stage
    COPY --from=build-stage /app/dist /usr/share/nginx/html
    EXPOSE 80
    CMD ["nginx", "-g", "daemon off;"]
   ```

2. Setup Docker Compose dengan cara bikin via docker-compose.yml.
   ```
    version: '3'
    
    services:
      vue-app:
        container_name: vue_app_container
        build:
          context: .
          dockerfile: Dockerfile
        volumes:
          - ./nginx.conf:/etc/nginx/conf.d/default.conf
        ports:
          - "80:80"
   ```

3. Setup server pake Nginx melalui nginx.conf.
   ```
    server {
        listen 80;
    
        location / {
            root /usr/share/nginx/html;
            index index.html;
            try_files $uri $uri/ /index.html;
        }
    }
    ```
   
4. Establish komunikasi dengan server menggunakan protokol ssh. Jalankan di terminal.
   Contoh command :
   ```
     ssh -p 10422 ubuntu@103.6.53.254
   ```

6. Pindahkan file yang kita punya ke server menggunakan protokol scp.
   contoh command :
   ```
     scp -P 10422 -r /Users/muhammadhilmytsaqifveradin/Documents/FRONTEND/focus-stopwatch-vue/focus-stopwatch ubuntu@103.6.53.254:/home/ubuntu/focus-stopwatch
   ```

8. Install aplikasi-aplikasi yang berhubungan dengan aplikasi kita di server, yaitu :
   - docker
   - docker-compose
   - node version 17
   - nginx

9. Jalankan docker compose-nya menggunakan command :
   ```
     docker-compose up -d --build
   ```

10. Cek aplikasi udah jalan pake ip:port, dalam kasus ini berarti :
   ```
     http://103.6.53.254:10480. ip kita: 103.6.53.254, port-nya: 10480
   ```

# Cara Pemakaian
[`^ kembali ke atas ^`](#)

Cara pemakaian **CMS Prestashop** ini sangat mudah, karena aplikasi ini telah menyediakan *interface* yang mudah dimengerti. Berikut untuk lebih jelasnya :
1. Sebelum menggunakan prestashop, kita perlu login pada halaman admin toko kita.

    ![login](https://4.bp.blogspot.com/-rmIdzrb4t4E/WOGbktO4p8I/AAAAAAAAGlc/z1NraShhrpUt-4Z0MVfXofZ5IV9hR_XbwCLcB/s1600/presta1.png)

2. Setelah login, kita akan masuk ke halaman *Dashboard*. Disini kita dapat melihat laporan penjualan website kita baik harian, mingguan, bulanan, bahkan tahunan.

    ![mainpage](https://3.bp.blogspot.com/-AjB_6mJZCxc/WOGbk3XPniI/AAAAAAAAGlg/NGZ_vOSF1s4jvw9Yx9jh7odGt8B4qHSuwCLcB/s1600/presta2.png)

3. Pada bagian samping kiri, terdapat berbagai menu yang dapat kita gunakan. Menu **Order** berguna untuk mengetahui informasi lebih detail tentang penjualan pada website kita. Disini kita dapat mencetak *invoices, credit slips, delivery slips*, dan lain-lain.

    ![order](https://1.bp.blogspot.com/-0-MhQjYMGvQ/WOGbkmpYSXI/AAAAAAAAGlY/JSwla_Py4ckrxc839Im9JKtyJjsmye_hQCLcB/s1600/presta3.png)

4. Menu **Catalog** berguna untuk mengetahui informasi lebih detail tentang barang apa saja yang dijual pada website kita, kategori apa saja yang ada, mengawasi stok barang yang tersisa, merek apa saja yang ada, melihat daftar diskon, dan lain-lain.

    ![catalog](https://4.bp.blogspot.com/-PQTBdZzcMBY/WOGblDw9tYI/AAAAAAAAGlk/GDC7cEzfWmo9LZ8bqcqwnv7iilAYlXNhwCLcB/s1600/presta4.png)

5. Menu **Customers** berguna untuk melihat informasi lebih detail tentang daftar pelanggan kita dan alamatnya.

    ![customer](https://2.bp.blogspot.com/-Mtss0c3rblo/WOGblcDU_bI/AAAAAAAAGlo/u1Hv6LWzwtAEuk9_NPQHnedI6PnotkEMwCLcB/s1600/presta5.png)

6. Menu **Customer Service** berguna untuk mengatur hubungan dengan pelanggan, seperti menerima keluhan, mengirim pesan kepada pelanggan, pengembalian barang, dan lain-lain.

    ![cs](https://3.bp.blogspot.com/-ZlT_WQ0bpyk/WOGblYW-yPI/AAAAAAAAGls/gcZb8k36rEUn8dDFnGXl35R_Uhy_lNMeACLcB/s1600/presta6.png)

7. Menu **Stat** berguna untuk melihat informasi lebih detail dari website kita, seperti jumlah pengunjung setiap harinya, lokasi pelanggan terbanyak, barang apa yang populer, dan lain-lain.

    ![stat](https://3.bp.blogspot.com/-kvZ9MMH6Fxc/WOGblsk5jpI/AAAAAAAAGlw/p8LhO5LIvMU4WnDEF5NKg7--tKy8mWa-wCLcB/s1600/presta7.png)

8. Selain menu-menu yang berhubungan dengan penjualan, **Prestashop** juga menyediakan menu untuk meningkatkan performa website kita seperti menu untuk menginstal modul atau plugin, menu untuk memperindah tampilan website, menu untuk mengatur pengiriman dan pembayaran barang, bahkan menu lokalisasi untuk meningkatkan layanan pada region tertentu.

    ![improve](https://3.bp.blogspot.com/-d_DufFiAblk/WOGbls1KYxI/AAAAAAAAGl0/AsyvLt1zp1IP1BG1PbDaG91PJKV-xDkhACLcB/s1600/presta8.png)

9. Selain itu, terdapat juga menu untuk mempermudah konfigurasi website kita baik itu konfigurasi umum maupun konfigurasi lanjut.

    ![configure](https://4.bp.blogspot.com/-58ke7QyDUwQ/WOGbmCZvHFI/AAAAAAAAGl4/LuQRv6uYmywWjbzmJy82UwNu5qCg8fp1gCLcB/s1600/presta9.png)



# Pembahasan
[`^ kembali ke atas ^`](#)

**Prestashop** ditulis dalam bahasa pemrograman `PHP` yang support untuk penggunaan MySQL. Sebagai salah satu CMS yang paling banyak digunakan di dunia, aplikasi ini menawarkan berbagai kelebihan, diantaranya :
- Aplikasi memiliki panel administrasinya mudah digunakan dan fleksibel, sehingga dapat disesuaikan dengan kebutuhan.
- Mendukung berbagai layanan pembayaran utama, seperti `PayPal`, `VISA`, `MasterCard`, dan `Maestro`.
- Diterjemahkan dalam banyak bahasa, termasuk Bahasa Indonesia.
- Memiliki desain yang *responsive*, sehingga dapat dibuka menggunakan *device* apapun.
- Memiliki lebih dari tiga ratus fitur untuk memudahkan pengguna.
- Banyak pengguna yang berkontribusi pada *discussion boards* dan sejenisnya, sehingga masalah yang dihadapi pengguna dapat cepat terselesaikan.

Tentu saja, sebuah aplikasi pasti memiliki kekurangan. Kekurangan yang dimiliki **Prestashop** antara lain :
- Penggunaan fitur atau modul yang lengkap menyebakan proses loading dari aplikasi ini menjadi sangat lambat
- Penggunaan *resource* memory aplikasi ini cukup besar, terutama ketika menggunakan fitur atau modul yang lengkap.
- Sebagian besar modul dan tema yang tersedia tidak gratis.

Jika dibandingkan dengan CMS sejenisnya seperti **Microweber**, CMS ini memiliki beberapa keunggulan dan kelemahan. Berikut adalah beberapa perbandingan antara kedua CMS ini :
- **Microweber** menyediakan proses design yang fleksibel dengan fitur *Drag and Drop* tanpa batasan, sehingga pengguna bebas mengkreasikan tampilan websitenya. Sedangkan **Prestashop** hanya menyediakan fitur design berupa penggantian template dan logo, adapun template yang tersedia tidak gratis.
- Modul atau plugin yang tersedia pada **Prestashop** jauh lebih banyak dibandingkan pada **Microweber**.
- **Prestashop** memiliki pengguna yang jauh lebih banyak daripada **Microweber** yang aktif pada forum-forum diskusi untuk membantu pengguna pemula.
- **Microweber** lebih ringan daripada **Prestashop** karena modulnya yang sedikit.
- Proses instalasi **Prestashop** lebih mudah karena berbasis PHP saja, sedangkan **Microweber** menggunakan framework laravel sehingga proses instalasi lebih sulit, terutama dalam hal *dependency*.



# Referensi
[`^ kembali ke atas ^`](#)

1. [About PrestaShop](https://www.prestashop.com/) - PrestaShop
2. [How to Log Into a VPS with PuTTY on Windows](https://www.digitalocean.com/community/tutorials/how-to-log-into-a-vps-with-putty-windows-users) - DigitalOcean
3. [How to Install PrestaShop on Ubuntu 16.04](http://idroot.net/linux/install-prestashop-ubuntu-16-04/) - idroot
4. [One Click Install PrestaShop](https://www.prestashop.com/blog/en/how-to-install-prestashop/) - PrestaShop
5. [PrestaShop Review](http://whichshoppingcart.com/prestashop.html) - whishshoppingcart

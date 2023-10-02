<h1 align="center"><img src="https://github.com/sagistarz/komdat/blob/main/image/logo.png"></h1>

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
Cara pemakaian aplikasi web FocusStopwatch termasuk mudah, karena. Berikut adalah lengkap nya : 
   1. Pada tampilan utama, terlihat interface yang mudah dimengerti. Kita perlu login ke dalam aplikasi.
      ![alt text](https://github.com/sagistarz/komdat/blob/main/image/1homepage.png)
   2.  Kita perlu memasukkan email agar report hasil data bisa tersimpan
      ![alt text](https://github.com/sagistarz/komdat/blob/main/image/2sendemail.png)
   3. Perlu dilakukannya confirm your mail untuk verifikasi email
      ![alt text](https://github.com/sagistarz/komdat/blob/main/image/3email.png)
   4. Tampilan setelah login
      ![alt text](https://github.com/sagistarz/komdat/blob/main/image/4signin.png)
   5. Tekan tombol Start, maka stopwatch akan mulai bekerja
      ![alt text](https://github.com/sagistarz/komdat/blob/main/image/5start.png)
   6. Jika, sudah merasa terdistraksi, maka tekan tombol Reset and Lap. FocusStopwach akan mencatat seberapa lama waktu fokus.
       ![alt text](https://github.com/sagistarz/komdat/blob/main/image/6reset.png)
   7. Jika ingin memulai kembali, tekan tombol Start. Maka, lap 2 akan dimulai.
       ![alt text](https://github.com/sagistarz/komdat/blob/main/image/7startagain.png)
   8. Jika ingin mencatat hasil fokus pada lap 2, tekan tombol Reset and Lap kembali. Maka waktu fokus pada lap 2 akan tercatat.
       ![alt text](https://github.com/sagistarz/komdat/blob/main/image/8resetagain.png)
   9. Jika sudah selesai menggunakan FocusStopwatch, tekan tombol Finish Stopwatch untuk balik ke tampilan awal.
       ![alt text](https://github.com/sagistarz/komdat/blob/main/image/9stop.png)
   10. Tekan tombol Report untuk melihat rekaman waktu fokus yang telah dijalankan
       ![alt text](https://github.com/sagistarz/komdat/blob/main/image/10reportIn.png)

Dalam penggunaan aplikasi web FocusStopwatch, penting untuk melakukan proses Sign in. Tanpa melakukan Sign in, report (laporan) mengenai penggunaan aplikasi kita tidak akan terekam. Berikut adalah perbandingan tangkapan layar dari report (laporan) penggunaan tanpa Sign in.
   ![alt text](https://github.com/sagistarz/komdat/blob/main/image/11reportOut.png)


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

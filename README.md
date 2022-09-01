# Load-Balance-Server

### Web Server

1. Apa itu Web Server?​

   Web Server adalah sebuah software yang memberikan layanan berupa data. Berfungsi untuk menerima permintaan HTTP atau HTTPS dari client atau di kenal dengan web browser (chrome atau firefox). Kemudian web server akan mengirimkan respon atas permintaan tersebut dalam bentuk halaman web.

2. Mengapa Memplejari Web Server?​

   Karena Web server memiliki peran penting dalam mengendalikan proses kerja dari sebuah website. Tanpa adanya web server, kamu tidak bisa melakukan permintaan data apapun pada suatu halaman atau page di web browser.

3. Bagaimana Cara Kerja Web Server?​

   ![image](https://user-images.githubusercontent.com/40049149/187933088-46bbc394-25b3-43e7-8e85-4b92e5f6dc1c.png)

   Pada ilustrasi di atas, dapat dilihat bahwa komputer client sedang melakukan request data yang berada pada server database melalui sebuah web server kemudian web server akan mengembalikan data tersebut dalam bentuk halaman website pada komputer client.

4. Fungsi Web Server​

  - Menyediakan data berdasarkan request atau permintaan yang masuk agar dapat menjamin keamanan sistem yang berjalan dengan lancar.
  - Melakukan pemeriksaan terhadap sistem security yang berasal dari permintaan HTTP berdasarkan request client atau web browser.

5. Jenis-Jenis Web Server​

  - Nginx
  - Apache
  - Lightpd
  - Lightspeed

6. Instalasi Nginx dan Service Management​

   Sekarang kita akan mencoba untuk melakukan instalasi salah satu web server yang terkenal yaitu adalah Nginx.

   Berikut adalah cara untuk melakukan Instalasi Nginx:

        sudo apt update; sudo apt upgrade

   ![Screenshot from 2022-09-01 21-11-59](https://user-images.githubusercontent.com/40049149/187936138-419dabf7-7798-449e-9a1d-08bfd79700e6.png)

        sudo apt install nginx

   Lalu nanti akan muncul notifikasi Do you want to continue? [Y/n] kalian ketik saja Y. Jika sudah maka instalasi akan berjalan.

   ![Screenshot from 2022-09-01 21-07-21](https://user-images.githubusercontent.com/40049149/187936063-f8bfd74a-16f7-4d2f-9f98-47b0463f630b.png)
   
   Jika kalian sudah menjalankan beberapa perintah diatas kalian sudah berhasil untuk melakukan installasi Nginx. Kalian bisa check menggunakan perintah di bawah ini.

        nginx -v

   ![image](https://user-images.githubusercontent.com/40049149/187937272-091f41e4-1977-40f1-8293-a38c101abe4e.png)
   
   Untuk melihat status nginx jalankan perintah berikut
   
        sudo systemctl status nginx

   ![image](https://user-images.githubusercontent.com/40049149/187937416-0c5c0744-702b-45fe-aebe-205072a615f8.png)

   Perintah untuk menghidupkan sistem dari Nginx
   
        sudo systemctl enable nginx

   ![image](https://user-images.githubusercontent.com/40049149/187938202-ae19f88c-e662-46c7-bcb3-1d92146cafb2.png)

   Perintah untuk menjalankan sistem dari Nginx
   
        sudo systemctl start nginx

   ![Screenshot from 2022-09-01 21-26-46](https://user-images.githubusercontent.com/40049149/187941136-8601d8e4-6d97-483c-8b83-561841b8f0c1.png)

   Perintah untuk me-reload sistem dari Nginx

        sudo systemctl reload nginx

   Perintah untuk mematikan sistem dari Nginx

        sudo systemctl disable nginx

   Perintah untuk menghentikan sistem dari Nginx

        sudo systemctl stop nginx

### Check Nginx​

Kemudian untuk melihat nginx telah terinstall. Kalian dapat mengakses IP dari server kalian, maka akan terlihat seperti berikut

![image](https://user-images.githubusercontent.com/40049149/187941524-9010cc4d-00bf-4ca0-8eec-fe4949a2c071.png)


### Reverse Proxy

1. Reverse proxy adalah konfigurasi standar yang digunakan untuk mengubah jalur traffic, misalkan aplikasi menggunakan port 3000 tetapi agar dapat di akses melalui port 80 maka harus menggunakan reverse proxy.

   Berikut adalah konfigurasi dari revese proxy.

         server { 
            server_name domain.com; 
    
            location / { 
                     proxy_pass http://127.0.0.1:3000;
            }
         }

2. Kenapa Harus Reverse Proxy?​

   Untuk mengamankan aplikasi yang berjalan pada server maka kita perlu untuk melakukan reverse proxy, supaya pengguna tidak dapat mengakses aplikasi kita secara langsung.


### Membuat Konfigurasi Revese Proxy​

Untuk membuat reverse proxy dapat mengikuti langkah-langkah berikut :

1. Pertama-tama masuk ke folder nginx setelah itu buat suatu directory baru telebih dahulu.

         cd /etc/nginx

   ![image](https://user-images.githubusercontent.com/40049149/187946466-2895b7f0-31e1-4fb6-bd6d-14550156cc24.png)

         sudo mkdir config
         ls

   ![image](https://user-images.githubusercontent.com/40049149/187946737-97f148b2-4bf3-4b28-9543-0fbda7bd8690.png)

2. Setelah itu masuk ke directory yang sudah kalian buat, setelah itu buat suatu file dengan nama my.reverse-proxy.conf

         cd config

         sudo nano reverse-proxy.conf

   ![image](https://user-images.githubusercontent.com/40049149/187947641-897ad6fb-2ac2-45c5-8c59-d4c84093ce64.png)

3. Setelah itu masukkan konfigurasi berikut:

         server { 
            server_name menther.xyz; 
    
            location / { 
                     proxy_pass http://192.168.1.107:3000;
            }
         }

   .

         INFO
         pastikan port 3000 di ganti sesuai aplikasi yang digunakan dan sesuaikan server_name dan IP addres kalian.

   ![image](https://user-images.githubusercontent.com/40049149/187973065-57db5443-523b-4bc0-aa4d-4622514af67a.png)

4. Jika sudah simpan konfigurasi yang sudah kalian buat tadi.

5. Selanjutnya keluar dari directory dumbways, setelah itu masuk ke dalam file nginx.conf.

         cd ..

   ![image](https://user-images.githubusercontent.com/40049149/187948209-d13db6a4-a572-4c90-bc36-2b70f868e428.png)

         sudo nano nginx.conf

   ![image](https://user-images.githubusercontent.com/40049149/187948473-dbd5eaec-5557-4f13-9c6f-9962eae3daf8.png)

6. Selanjutnya pergi ke-bagian include, setelah itu masukan lokasi dari directory yang bersi konfigutasi yang sudah kalian buat tadi.

   ![image](https://user-images.githubusercontent.com/40049149/187948752-9a15747d-e6b8-47b7-8877-bf5e19896f12.png)

         INFO
         /*; menandakan file nginx.conf akan membaca seluruh file yang berada di dalam directory config

7. Beberapa proses tadi adalah cara untuk membuat reverse proxy untuk aplikasi kita, kemudian pastikan untuk melakukan pengecekan konfigurasi dengan menjalankan perintah :

         sudo nginx -t

   ![image](https://user-images.githubusercontent.com/40049149/187949868-a68d0ba1-982b-4e32-aad1-8c6ace71b7c2.png)

8. Jika sudah sekarang kita tinggal melakukan restart/reload Nginx kita.

         sudo systemctl restart nginx

   ![image](https://user-images.githubusercontent.com/40049149/187949939-bed70f16-d376-4fac-8239-ea5e6b111d0a.png)

9. Sekarang kita akan membuat sebuah virtual host. Untuk membuat virtual host kita harus masuk ke local server kita setelah itu masuk ke dalam file /etc/hosts.

         sudo nano /etc/hosts

   ![image](https://user-images.githubusercontent.com/40049149/187955117-67c95a96-2263-422b-9923-3673a998d1ce.png)

10. Setelah itu masukkan IP server kita selanjutnya masukkan nama domain yang kalian inginkan.

    ![image](https://user-images.githubusercontent.com/40049149/187955188-aea603da-3184-4d08-8de3-ee743e729f9e.png)

11. Jika sudah sekarang coba buka web browser kalian setelah itu coba akses nama domain kalian.

    ![image](https://user-images.githubusercontent.com/40049149/187955307-322d3fd1-b0fb-4868-aafd-b9c757c9d294.png)

12. Jika kita lihat disini adalah kita mendapatkan 502 Bad Gateway kenapa? karena kita belum menjalankan aplikasi kita. Sekarang kita coba untuk menjalankan aplikasi dumbflix yang sudah pernah kita pakai sebelumnya. Untuk menjalankan aplikasi dumbflix kalian dapat mengikuti langkah-langkah berikut ini.

          git clone https://github.com/dumbwaysdev/dumbflix-frontend.git

    ![image](https://user-images.githubusercontent.com/40049149/187955509-c3d4714e-a9cf-42f6-8d63-a330a6cb858a.png)

          cd dumbflix-frontend
          npm install

    ![Screenshot from 2022-09-01 23-24-26](https://user-images.githubusercontent.com/40049149/187968906-062ee359-905d-440a-af01-41e69f728ef6.png)


    keterangan : perintah di atas ini bertujuan untuk meng-install module dari aplikasi node.js

         npm start

    ![image](https://user-images.githubusercontent.com/40049149/187974015-51c37aa9-56a9-4cf0-9ea9-55ca64394148.png)

    keterangan : perintah di atas ini untuk menjalankan aplikasi

13. Selanjutnya kita coba untuk me-refresh web browser kita.

14. Sekarang bisa kita lihat bahwa aplikasi kita sudah berjalan, dan dapat di akses oleh domain virtual yang kita buat.

    ![image](https://user-images.githubusercontent.com/40049149/187973862-7603382d-4319-4c61-a490-e3cf126a0777.png)

### Load Balancing
1. Apa itu Load Balancing?​

   Load Balancing adalah suatu jaringan komputer yang menggunakan metode untuk mendistribusikan beban kerjaan pada dua atau bahkan lebih suatu koneksi jaringan secara seimbang agar pekerjaan dapat berjalan optimal dan tidak overload (kelebihan) beban pada salah satu jalur koneksi.

2. Kenapa Harus Load Balancing?​

   Jika kita memiliki website atau aplikasi yang telah digunakan hingga ribuan, ratusan atau bahkan jutaan pengguna maka kita harus melakukan load balancing pada aplikasi tersebut agar tidak down, karena beban akses pengguna dibagi ke beberapa server sekaligus.

3. Membuat Konfigurasi Load Balancing​

   Untuk membuat Load Balancing kalian harus membuat server baru lagi. Untuk cara membuat server kalian ikuti saja step by step seperti saat pertemuan Fundamental DevOps : Install Ubuntu Server

- Jika server kalian sudah terbuat maka buatlah aplikasi sederhana sama seperti pertemuan sebelumnya (node.js). setelah itu jalankan aplikasi tersebut.

image1
image1
image1
image1

- Sekarang kita sudah mempunyai 2 buah server untuk aplikasi kita.

- Sekarang kita akan coba untuk membuat konfigurasi load balancing.

- Pertama-tama kita masuk ke dalam konfigurasi reverse proxy yang sudah kita buat sebelumnya.

      sudo nano sudo nano /etc/nginx/config/reverse-proxy.conf

  ![image](https://user-images.githubusercontent.com/40049149/187977973-d7801259-42ef-4ad2-b586-6d1824156238.png)

- Selanjutnya kita akan tambahkan konfigurasi ke dalam file my.reverse-proxy.conf. Sekarang kita akan coba tambahkan beberapa konfigurasi, kalian dapat menggunakan konfigurasi di bawah ini.

      upstream loadbalance { 
          server 192.168.1.107:3000;
          server 192.168.1.105:3000;
      }
      server { 
          server_name menther.xyz; 
  
          location / { 
                   proxy_pass http://loadbalance;
          }
      }

  ![image](https://user-images.githubusercontent.com/40049149/187979176-49673190-7dc3-4c62-9248-2cd62559bf7c.png)


  keterangan :

  Pada bagian upstream kalian dapat mengganti nama domain dengan nama yang kalian inginkan.

  Pada bagian server masukan IP dari server kalian, setelah itu diikuti dengan port aplikasi.

- Selanjutnya pada bagian proxy_pass ubah dari yang sebelumnya adalah alamat IP dari aplikasi kalian, sekarang kalian samakan dengan nama upstream yang ada di konfigurasi kalian.

- Jika sudah sekarang kita coba cek apakah konfigurasi yang sudah kita buat tadi itu error atau tidak.

      sudo nginx -t

  ![image](https://user-images.githubusercontent.com/40049149/187978044-9a592fd3-5c79-472b-9ecc-4e9687a6cc1c.png)

- Jika tidak ada error jalankan perintah restart nginx untuk merestart nginx kita, karena kita sudah menambahkan suatu konfigurasi baru di dalam file reverse proxy kita.

      sudo systemctl restart nginx

  ![image](https://user-images.githubusercontent.com/40049149/187978199-2d715cf2-d324-4735-bdb4-4b71aec05859.png)

- Selanjutnya jalankan aplikasi kita yang ada di server kita.

image1
image1

- Jika sudah sekarang coba buka web browser kalian setelah itu coba akses nama domain kalian.

image1

- Untuk make sure apakah load balancing yang sudah kita buat tadi berjalan dengan baik atau tidak, kita coba untuk mematikan satu aplikasi kita.

- Kita masuk ke dalam salah satu server aplikasi kita, setelah itu kalian hentikan aplikasi kalian CTRL + C.

image1

- Sekarang kita coba akses web browser kita lagi setelah itu akses nama domain kalian.

image1

      INFO
      Jika aplikasi kalian masih bisa di akses berarti konfigurasi Load Balance kalian berhasil dan tidak ada error

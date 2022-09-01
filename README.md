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













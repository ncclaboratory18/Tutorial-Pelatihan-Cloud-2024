# Tutorial Pelatihan Cloud 2024

## Daftar Isi
- [Resource Group](#resource-group)
    - [Membuat Resource Group](#membuat-resource-group)
    - [Role Assignment](#role-assignment)
- [Virtual Machine](#virtual-machine)
    - [Menyewa dan Mengakses Azure VM Windows](#menyewa-dan-mengakses-azure-vm-windows)
    - [Menyewa dan Mengakses Azure VM Linux](#menyewa-dan-mengakses-azure-vm-linux)
    - [Mendeploy Aplikasi di Azure VM](#mendeploy-aplikasi-di-azure-vm)
- [Database](#database)
    - [Membuat Database PostgreSQL di Azure](#membuat-database-postgresql-di-azure)
    - [Mengakses Database melalui psql](#mengakses-database-melalui-psql-pada-vm)
    - [Mengakses Database melalui pgAdmin](#mengakses-database-melalui-pgadmin-local)

## Resource Group
Setiap resource yang akan kita buat harus terikat kepada suatu resource group. Resource group berguna untuk mengelompokkan resource sejenis sehingga dapat diberi konfigurasi, subscription, dan hak akses serupa. Cara pengelompokan resource bebas mengikuti kebutuhan pengguna.
### Membuat Resource Group
Untuk membuat resource group di microsoft azure, kalian bisa mengikuti langkah-langkah berikut:
1. Pada sidebar tampilan Microsoft Azure, pilih Resource Group dan tekan tombol create.<br><img src="image/resource-group-1.png" style="width:500px"/>
2. Pada project details, pilih subscription yang ingin digunakan dan masukkan nama resource group.<br><img src="image/resource-group-2.png" style="width:500px"/>
3. Selanjutnya, masukkan region tempat metadata dari resource group disimpan pada bagian `Resource Details`. Region di sini hanya menunjukkan lokasi metadata resource group dan tidak berhubungan dengan region dari resource yang akan dimasukkan ke dalam resource group. Lokasi resource tetap dapat dipilih secara bebas dan independen dari resource group.<br><img src="image/resource-group-3.png" style="width:500px"/>
4. Lanjutkan proses `review + create`. Setelah proses selesai, kembali ke menu `Resource Group`. Resource group yang berhasil dibuat akan terlihat.<br><img src="image/resource-group-4.png" style="width:500px"/>
5. Informasi detail terkait resource group dapat dilihat dengan menekan pilihan resource group yang sesuai.<br><img src="image/resource-group-5.png" style="width:500px"/>
### Role Assignment
Sebelumnya, telah disinggung bahwa alokasi hak akses dapat dilakukan pada resource group. Sederhananya, alokasi ini dapat membantu suatu tim untuk mengatur apa saja yang bisa dilakukan seseorang sesuai dengan perannya masing-masing. Pada Microsoft Azure, sistem autorisasi ini disebut Azure RBAC (role-based access control) dan berlaku tidak hanya untuk resource group saja, tetapi juga subscription, resource, dll. Langkah-langkah pemberian hak akses pada resource group dapat dilakukan dengan langkah-langkah berikut:
1. Buka menu `Resource Group` dan pilih resource group yang akan dilakukan role assignment. Selanjutnya, pilih menu `Access Control (IAM)`.<br><img src="image/role-assignment-1.png" style="width:500px"/>
2. Klik `Add` dan pilih `Add role assignment` yang berada di bagian kiri atas.<br><img src="image/role-assignment-2.png" style="width:500px"/>
3. Pada bagian `Role`, pilih role yang ingin diberikan. Detail privileges dapat dilihat dengan menekan tombol `view` di kolom `Details`.<br><img src="image/role-assignment-3.png" style="width:500px"/><br><img src="image/role-assignment-4.png" style="width:500px"/>
4. Selanjutnya, pindah ke bagian `Members` untuk menentukan akun yang akan diberi hak akses dengan menekan tombol `select members`.<br><img src="image/role-assignment-5.png" style="width:500px"/>
5. Masukkan akun yang akan diberi hak akses, lalu tekan `select`. Jika sudah, klik `Review + assign`.<br><img src="image/role-assignment-6.png" style="width:500px"/>
6. Untuk melihat role yang telah diberikan, kembali ke tampilan resource group, pilih menu `Access Control (IAM)`, dan pindah ke tab `Role Assignments`.<br><img src="image/role-assignment-7.png" style="width:500px"/>

## Virtual Machine
Microsoft azure menyediakan layanan virtual machine dengan berbagai macam sistem operasi, baik windows maupun linux.
### Menyewa dan Mengakses Azure VM Windows
Menyewa Virtual Machine dengan sistem operasi windows dan mengaksesnya melalui RDP dapat dilakukan dengan mengikuti langkah-langkah berikut:
1. Pada sidebar tampilan Microsoft Azure, pilih Virtual Machines<br><img src="image/vm-windows-1.png" style="width:500px"/>
2. Setelah muncul tampilan menu Virtual Machines, tekan tombol `Create` dan pilih Azure Virtual Machines
3. Masukkan resource group, nama VM, dan region yang sesuai<br><img src="image/vm-windows-2.png" style="width:500px"/>
4. Pilih image Windows `Windows Server 2022 Datacenter: Azure Edition - x64 Gen2` dengan size vm `Standard_DS1_v2`<br><img src="image/vm-windows-3.png" style="width:500px"/>
5. Selanjutnya, masukkan username dan password akun administrator untuk menunjang keamanan<br><img src="image/vm-windows-4.png" style="width:500px"/>
6. Pastikan port 3389 (RDP) telah dipilih pada `Indbound Port Rule` agar VM dapat diakses menggunakan RDP<br><img src="image/vm-windows-port.png" style="width:500px"/>
7. Lanjutkan proses `review + create` untuk membuat virtual machine.
8. Setelah VM berhasil dideploy, VM tersebut akan terlihat pada menu `Virtual Machines`.<br><img src="image/vm-windows-5.png" style="width:500px"/>
9. Untuk mengakses, pilih VM windows yang telah dibuat lalu masuk ke bagian `Connect`. Pada menu tersebut, terdapat informasi terkait IP publik, admin username, dan port yang terbuka. Di bagian bawahnya, terdapat pula pilihan Native RDP, pilih `Download RDP file` dan jalankan RDPnya.<br><img src="image/vm-windows-6.png" style="width:500px"/>
10. Tekan connect dan masukkan password akun administrator sesuai yang telah dimasukkan sebelumnya<br><img src="image/vm-windows-7.png" style="width:500px"/>
11. Jika berhasil tersambung, maka kita dapat mengakses VM windows beserta GUI-nya seperti berikut<br><img src="image/vm-windows-8.png" style="width:500px"/>
### Menyewa dan Mengakses Azure VM Linux
Menyewa Virtual Machine dengan sistem operasi windows dan mengaksesnya melalui RDP dapat dilakukan dengan mengikuti langkah-langkah berikut:
1. Pada sidebar tampilan Microsoft Azure, pilih Virtual Machines<br><img src="image/vm-windows-1.png" style="width:500px"/>
2. Setelah muncul tampilan menu Virtual Machines, tekan tombol `Create` dan pilih Azure Virtual Machines
3. Masukkan resource group, nama VM, dan region yang sesuai<br><img src="image/vm-ubuntu-1.png" style="width:500px"/>
4. Pilih image Ubuntu `Ubuntu Server 20.04 LTS - x64 Gen2` dengan size vm `Standard_DS1_v2`.<br><img src="image/vm-ubuntu-2.png" style="width:500px"/>
5. Pada bagian `Administrator Account`, terdapat 2 pilihan tipe autentikasi dengan menggunakan SSH Public Key atau Password. Di sini, kita akan mencoba menggunakan Public Key. Selanjutnya, masukkan username, pilih `Generate new key pair`, dan masukkan nama key-nya.<br><img src="image/vm-ubuntu-3.png" style="width:500px"/>
6. Agar dapat diakses melalui SSH, jangan lupa untuk memilih port 22 (SSH) pada menu `Select inbound ports`.<br><img src="image/vm-ubuntu-4.png" style="width:500px"/>
7. Lanjutkan proses `create` dan jangan lupa untuk mendownload file private key-nya.<br><img src="image/vm-ubuntu-5.png" style="width:500px"/>
8. Setelah VM berhasil dideploy, VM tersebut akan terlihat pada menu `Virtual Machines`.<br><img src="image/vm-ubuntu-6.png" style="width:500px"/>
9. Untuk mengakses, pilih VM windows yang telah dibuat lalu masuk ke bagian `Connect`. Pada menu tersebut, terdapat informasi terkait IP publik, admin username, dan port yang terbuka.
10. Selanjutnya, buka terminal (powershell, cmd, atupun linux terminal) dan `Run as Administrator`.<br><img src="image/vm-ubuntu-7.png" style="width:500px"/>
11. Pada terminal, jalankan `ssh -i <path ke file private key> <admin username>@<IP publik>` seperti berikut:<br><img src="image/vm-ubuntu-8.png" style="width:500px"/>
12. Jika berhasil terkoneksi dengan VM, tampilan akan seperti berikut. Melalui CLI tersebut, kita dapat mengakses file dan mengeksekusi program yang ada di VM.<br><img src="image/vm-ubuntu-9.png" style="width:500px"/>
### Mendeploy Aplikasi di Azure VM
Salah satu fungsi Virtual Machine yang telah kita buat adalah untuk menjalankan aplikasi. Selanjutnya, kita akan mencoba men-deploy aplikasi nodejs dengan langkah-langkah berikut:
1. Agar dapat menerima request `Http`, kita perlu membuka port 80 dengan melakukan pengaturan jaringan.
2. Buka VM Ubuntu yang telah kita buat di Azure Portal, lalu pilih menu `Network settings` pada bagian `Networking`. Scroll hingga masuk ke bagian `Rules`, kemudian pilih `Create port rule` > `Inbound port rule`.
3. Isi `Destination port ranges` dengan 80 dan pilih `TCP` pada bagian `Protocol`. Selanjutnya, klik tombol `Add`.
4. Selanjutnya, akses kembali VM Ubuntu seperti cara sebelumnya.
5. Pada VM, download Web Server Nginx, nodejs, dan npm dengan menjalankan command berikut:<br>
    ```R
    sudo apt-get update
    sudo apt-get install nginx -y
    sudo apt-get install nodejs -y
    sudo apt-get install npm -y
    ```
6. Selanjutnya download source code aplikasi yang ingin dideploy dan letakkan di folder `/var/www/`. Kalian bisa menggunakan aplikasi dari repo `https://github.com/ramamimu/socket.io-NCC.git`. Pindah ke folder `/var/www/` lalu `git clone` menggunakan command berikut:<br>
   ```R
   cd /var/www/
   sudo git clone https://github.com/ramamimu/socket.io-NCC.git
   ```
7. Pindah ke folder `socket.io` lalu install dependecies yang dibutuhkan.<br>
    ```R
    cd /var/www/socket.io/
    sudo npm i
    ```
8. Program dapat dijalankan di latar belakang menggunakan `pm2`
   ```R
   sudo npm install pm2 -g
   pm2 start index.js
   ```
9. Karena program berjalan di port 3000, ubah konfigurasi nginx di file `/etc/nginx/sites-available/default` menjadi sebagai berikut:
    ```R
    server {
        listen 80;
    
        location / {
            proxy_set_header   X-Forwarded-For $remote_addr;
            proxy_set_header   Host $http_host;
            proxy_pass         "http://127.0.0.1:3000";
        }
    }
    ```
10. Restart nginx agar mengikuti konfigurasi yang baru.
    ```R
    systemctl restart nginx
    ```
11. Akses `http:<IP Publik>` pada web browser.

## Database
### Membuat Database PostgreSQL di Azure
### Mengakses Database melalui psql pada VM
### Mengakses Database melalui pgAdmin Local


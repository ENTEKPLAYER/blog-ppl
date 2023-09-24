# Individual Review 1

## 1. Scrum Understanding

### 1.1 Apa itu Scrum?
Scrum adalah framework yang bisa dipakai suatu organisasi untuk menyelesaikan problem yang kompleks, seperti pada software development.

Di framework Scrum, masalah yang kompleks diharapkan bisa diselesaikan dengan pemikiran *Empirism* yaitu solusi dapat ditemukan dengan pengalaman dan observasi. Maka di Scrum diterapkan pengembangan software dengan *iterative* dan *incremental*.

### 1.2 Scrum Team
Agar proses pengembangan software dapat dilakukan dengan efektif dan dapat memberikan banyak value di tiap iterasi, dibuat organisasi tim yang isinya:

#### Developer
Tugas developer adalah untuk membuat sprint backlog (pemilihan task dari product backlog yang mau dikerjakan), menentukan definition of done, dan menyelesaikan tasknya.

#### Product Owner
Product Owner bertugas untuk berkomunikasi dengan client dan menentukan product backlog (apa saja yang diinginkan client).

#### Scrum Master
Scrum Master adalah yang memastikan semua event Scrum jalan dan membantu Product Owner menentukan product backlog.

### 1.3 Events
Sprint Planning, Sprint, Daily Scrum, Review, Retrospective.

Di PPL Sprint Planning 2:30 jam, Sprint 5 jam per task, Daily Scrum minimal 2 kali per minggu.

### 1.4 Konfigurasi Scrum Tim Kami
Tim kami menggunakan azure devops yang disediakan oleh client untuk memudahkan kami menjalankan Scrum framework.

![devops](/img/img1.png)

Di azure devops kita dapat menambah backlog, task, dll dengan mudah.

![devopstasks](/img/img11.png)


## 2. CI/CD
Link CI/CD yang saya setup: https://gitlab.com/alin.fathul.ilmi/tugas-deployment-ppl

Saya membuat template kode ini memakai framework Spring Boot, alasannya karena saya memakai Spring Boot di pelajaran Advprog semester kemarin.

Sesuai dengan ketentuan PPL wiki, Repository saya mempunyai 3 branch utama yaitu:

- Production (berada di branch master)
- Staging (berada di branch staging)
- Development (berada di branch PBI-n-description)

Production isinya aplikasi yang sudah bisa dipakai untuk umum, Staging berisi aplikasi yang dipakai untuk testing dan Development adalah untuk penambahan suatu fitur.

Di branch development, saya setup CI/CD dengan pipelines build dan test, build adalah untuk mengcompile aplikasi menjadi runnable standalone dan test adalah untuk menghitung code coverage (code coverage dihitung menggunakan plugin JaCoCo pada SpringBoot).

![hasil test branch development](/img/img2.png)

Pada branch Staging, pipelines ditambahkan stage Publish dan Deploy. Publish digunakan untuk membuat docker image dan menaruhnya di dockerhub. Stage Deploy digunakan untuk mengambil image yang sudah ditaruh di dockerhub tadi lalu jalankan di server GCP. Akan dijelaskan cara pembuatannya dibawah.

![hasil pipeline branch staging](/img/img3.png)

Untuk membuat pipelines di Gitlab, perlu dibuat file .gitlab-ci.yml di root directory. Syntax .gitlab-ci mengikuti YAML language.

Defining variable dan stages yang ingin dijalankan pipeline:

![defining variable and stages](/img/img5.png)

Untuk tiap stages kita bisa setup image apa yang dipakai untuk menjalankan script (gitlab ci/cd run script dengan docker), before script, script, artifacts (file yang dihasilkan script yang nantinya bisa dipakai untuk stages lain) dan di branch mana stages dijalankan.

Untuk stage build, saya memangil command bootJar pada gradle untuk membuat runnable standalone file. 

![bootJar](/img/img6.png)

Untuk stage test, saya memangil plugin JaCoCo pada SpringBoot untuk menghitung Code Coverage, dan menulisnya di variable coverage pada gitlab.

![test jacoco](/img/img7.png)

Pada stage publish, saya memakai image docker in docker untuk menjalankan command docker build dengan argument link server database saya. Argument dari docker build akan di passing ke file DockerFile yang nantinya akan digunakan oleh server untuk running image. 

![dockerfile](/img/img9.png)

![publish](/img/img8.png)

Upload ke dockerhub menggunakan command docker push.

Di stage deploy, saya connect ke server GCP dengan ssh. SSH key saya taruh di CICD. Kemudian jalankan command docker run disana.

![deploy](/img/img10.png)

## 3. Framework
Setelah melewati pipeline CI/CD template kode yang saya buat tadi harusnya sudah running di server dan dapat diakses dari mana saja. Templatenya ini juga sudah saya connect ke database provider supabase.com akses ke database dibantu menggunakan JDBC API.

![hasil deploy branch staging](/img/img4.png)

Untuk template framework tim, saya menggunakan Nuxt.js sesuai yang sudah didiskusikan. Untuk setup Nuxt.js pertama saya harus install Node js v16.10.0 keatas.

![hasil instalasi node](/img/img15.png)

Setelah install run command: npx nuxi@latest init <project-name>

![setup projek](/img/img12.png)

Setelah install tinggal change directory ke project-name yang dipilih dan jalankan: npm run dev.

![running](/img/img13.png)
![running](/img/img14.png)




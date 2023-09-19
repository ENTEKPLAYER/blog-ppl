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
todo: Jelasin di PPL nya kapan dan berapa lama.

### 1.4 Konfigurasi Scrum Tim Kami
Tim kami menggunakan azure devops yang disediakan oleh client untuk memudahkan kami menjalankan Scrum framework.

![devops](/img/img1.png)

Di azure devops kita dapat menambah backlog, task, dll dengan mudah.

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

Pada branch Staging, pipelines ditambahkan stage Publish dan Deploy. Publish digunakan untuk membuat docker image dan menaruhnya di dockerhub. Stage Deploy digunakan untuk mengambil image yang sudah ditaruh di dockerhub tadi lalu jalankan di server GCP.


## 3. Framework

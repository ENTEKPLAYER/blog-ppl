## Melanjutkan task

Di week 3 ini saya lanjutkan task yang kemarin yaitu buat form registrasi pasien baru task yang dari minggu kemarin ada dua di gabung menjadi satu task. Jadi task ini acceptance criterianya ditaruh di azure devOps agar dapat di tracking.

![tracking](/img_3/tracking.png)

Dengan menggunakan fitur task board di azure devOps, saya dapat melihat progress kelompok dan saya juga dapat menyampaikan progress saya dengan mudah. Ini menurut saya dapat meningkatkan effisiensi penggerjaan team.

Tetapi menurut saya fitur yang paling meningkatkan effisiensi adalah git repository. Git memiliki banyak fitur yang dapat memanage proyek yang berkelompok, seperti adanya fitur branching, branching memungkinkan kelompok bekerja di berbagai environment berbeda seperti adanya branch development yang digunakan untuk pembuatan fitur yang belum di release, staging digunakan untuk menyatukan branch development untuk pengetesan, dan branch production yang digunakan untuk merelease proyek. 

Selain branching ada juga fitur pull request dan merging, pull request memudahkan kelompok untuk melakukan review code sebelum code di merge atau digabungkan, sedangkan merging digunakan untuk mengabungkan kode secara automatis dan dapat mendeteksi error saat pengabungan kode.

## Nuxt component

Untuk menerapkan reusability dan abstraksi dalam OOP, kelompok saya menggunakan Nuxt component untuk membuat pages. Nuxt component memungkinkan suatu kode HTML, css atau js digunakan berulang ulang dan dapat di abstraksi dari halaman utama. Contohnya pada pembuatan popup gagal dan popup berhasil, saya menggunakan component Dialog yang didapat dari plugin headlessui, saya tinggal memakai saja komponent ini tanpa mengetahui cara kerjanya dan saya bisa memakainya sebanyak 3 kali untuk menampilkan popup yang berbeda-beda.

![dialog](/img_3/dialog.png)

![popup](/img_3/popup.png)

## Sonarqube

Untuk menerapkan best practices dalam coding saya menggunakan sonarqube untuk menjalankan automated code checking berikut hasil sonarqube saya:

![sonarqube](/img_3/sonarqube.png)

sonarqube link: [Link](https://sonarqube.cs.ui.ac.id/dashboard?id=pendaftaran-pasien-baru)
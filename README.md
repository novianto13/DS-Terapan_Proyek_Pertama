# DS-Terapan_Proyek_Pertama
Proyek Pertama DS Terapan untuk menjelaskan faktor apa yang menyebabkan Attrition HR mencapai 10%. 
nama : Novianto

Link dashboard

https://public.tableau.com/views/ProjectpertamaDSTerapan/Dashboard1?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link

# Business Understanting
Jaya Jaya Maju merupakan salah satu perusahaan multinasional yang telah berdiri sejak tahun 2000. Ia memiliki lebih dari 1000 karyawan yang tersebar di seluruh penjuru negeri. Walaupun telah menjadi menjadi perusahaan yang cukup besar, Jaya Jaya Maju masih cukup kesulitan dalam mengelola karyawan. Hal ini berimbas tingginya attrition rate (rasio jumlah karyawan yang keluar dengan total karyawan keseluruhan) hingga lebih dari 10%.

Business problem

Dari latar belakang tersebut pertanyaan yang diajukan dalam project ini adalah
1. Faktor apa yang mempengaruhi attririon

Project Scope
Untuk menjawab permasalah bisnis tersebut maka aktivitas dalam project ini meliput:

1. Pemahaman data untuk menjelaskan secara deskripsi data
2. Menemukan faktor yang mempengaruhi attrition

Persiapan
untuk menjelakan project ini, data yang diperlukan diambil dari case dicoding yang diberikan dengan akses berikut: https://github.com/dicodingacademy/dicoding_dataset/tree/main/employee

Untuk olah data, project ini menggunakan Google Colab dengan pemrograman pyton.
Hasil olah data ditampilkan dalam dashboard

# 1. Pemahaman Data
pada bagian ini akan dilakukan untuk menjelaskan data makna dalam dataset.
![image](https://github.com/user-attachments/assets/d6bdb57a-b644-4f3d-8e5f-2fe5bbd5c7a8)

Hasilnya adalah berikut
![image](https://github.com/user-attachments/assets/19b1081b-55a1-40d2-bea7-57d1dc7d06f1)

Berikut adalah arti dari masing-masing elemen dalam hasil data:

Total 35 kolom – Data memiliki 35 variabel yang menggambarkan berbagai aspek dari karyawan.
Non-Null Count – Menunjukkan jumlah entri yang tidak kosong dalam setiap kolom. Misalnya, kolom Attrition hanya memiliki 1058 entri, yang berarti ada beberapa nilai yang hilang (missing values) sebanyak 412.
Dtype – Menunjukkan tipe data dari setiap kolom:
int64 → Bilangan bulat (integer)
float64 → Bilangan desimal (floating point)
object → Data kategori atau teks
Berikut beberapa variabel utama dan artinya:

EmployeeId → ID unik untuk setiap karyawan.
Age → Usia karyawan.
Attrition → Indikator apakah karyawan telah keluar dari perusahaan (1 untuk keluar, 0 untuk tetap).
BusinessTravel → Kategori perjalanan bisnis yang dilakukan karyawan.
DailyRate & MonthlyRate → Gaji harian dan bulanan karyawan.
Department → Departemen tempat karyawan bekerja (misalnya HR, R&D, Sales).
DistanceFromHome → Jarak rumah ke kantor.
Education & EducationField → Tingkat pendidikan dan bidang studi karyawan.
EnvironmentSatisfaction → Kepuasan karyawan terhadap lingkungan kerja.
JobInvolvement & JobSatisfaction → Seberapa terlibat dan puas karyawan dalam pekerjaannya.
MonthlyIncome → Pendapatan bulanan karyawan.
OverTime → Apakah karyawan bekerja lembur atau tidak.
PerformanceRating → Rating kinerja karyawan.
WorkLifeBalance → Indikator keseimbangan kehidupan kerja karyawan.
YearsAtCompany & YearsInCurrentRole → Lama bekerja di perusahaan dan dalam peran saat ini.
YearsSinceLastPromotion → Waktu sejak promosi terakhir.

## 1.2. Eksplorasi data
Pada bagian ini visualisasi data dilakukan untuk memberikan gambaran tentang data.

Untuk mempermudah pemahaman data maka data project diarahkan pada hanya pada beberapa variabel yang dinilai dapat menjelaskan attrition.

![image](https://github.com/user-attachments/assets/eaf45923-cd2f-4ece-a440-044ce631dfa9)

Hasil dataset baru adalah sebagai berikut:

![image](https://github.com/user-attachments/assets/835f2eb1-fa3c-496f-a8be-f01e3805b628)

Untuk melihat data lebih detail maka code berikut digunakan:
new_df.describe(include='all')

Hasil keterangan dari code berikut adalah :
1️⃣ Karakteristik Karyawan

Usia rata-rata adalah sekitar 36,9 tahun, dengan rentang usia dari 18 hingga 60 tahun.
Jumlah tahun bekerja di perusahaan memiliki rata-rata 7 tahun, tetapi ada karyawan yang sudah bekerja hingga 40 tahun.
Rata-rata tahun dalam peran saat ini adalah sekitar 4,2 tahun, menunjukkan adanya stabilitas dalam posisi pekerjaan.

2️⃣ Kesejahteraan & Kepuasan

Keseimbangan kehidupan kerja memiliki nilai rata-rata 2,72, menunjukkan bahwa beberapa karyawan mungkin mengalami tantangan dalam menyeimbangkan pekerjaan dan kehidupan pribadi.
Kepuasan pekerjaan memiliki distribusi yang cukup luas, dari 1 (sangat tidak puas) hingga 4 (sangat puas), dengan median sekitar 3.
Kepuasan lingkungan kerja juga bervariasi, dengan angka tertinggi mencapai 4.

3️⃣ Gaji dan Insentif

Pendapatan bulanan rata-rata adalah sekitar 14.313, dengan nilai minimum 2094 dan maksimum 26.999. Ini menunjukkan adanya kesenjangan yang cukup besar dalam distribusi gaji.
Karyawan dengan opsi saham tampaknya memiliki beberapa tingkatan berbeda, meskipun ini tidak dijelaskan dalam data.
Peningkatan gaji tahunan memiliki nilai rata-rata 2,91%, yang mungkin mempengaruhi kepuasan dan motivasi kerja.

4️⃣ Perjalanan Bisnis & Departemen

Mayoritas karyawan jarang melakukan perjalanan bisnis (Travel_Rarely muncul sebanyak 1043 kali).
Departemen terbesar adalah Research & Development, yang memiliki 961 karyawan dibandingkan departemen lain seperti Sales atau HR.

5️⃣ Promosi & Rotasi

Rata-rata waktu sejak promosi terakhir adalah sekitar 7 tahun, dengan beberapa karyawan yang belum mendapatkan promosi selama 40 tahun.
Beberapa karyawan tidak mengalami perpindahan perusahaan, tetapi ada yang memiliki pengalaman bekerja di beberapa perusahaan sebelum ini.

*Kesimpulan*
Data ini menunjukkan pola yang menarik terkait kepuasan kerja, keseimbangan kehidupan kerja, serta struktur gaji dan perjalanan bisnis. Jika dianalisis lebih lanjut, mungkin bisa ditemukan hubungan antara kepuasan kerja dan faktor-faktor seperti gaji, perjalanan bisnis, atau kesempatan promosi.

Untuk dapat memahami lebih lanjut maka dapat dibuat visualisasi berikut ini

![image](https://github.com/user-attachments/assets/76390cd9-0e06-4fb1-b129-6c22d1197d96)




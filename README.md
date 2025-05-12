# Proyek Pertama: Identifikasi Masalah Attrition HR
Proyek Pertama DS Terapan untuk menjelaskan faktor apa yang menyebabkan Attrition HR mencapai 10%. 
nama : Novianto
ID: novianto_14b


# Business Understanting
Jaya Jaya Maju merupakan salah satu perusahaan multinasional yang telah berdiri sejak tahun 2000. Ia memiliki lebih dari 1000 karyawan yang tersebar di seluruh penjuru negeri. Walaupun telah menjadi menjadi perusahaan yang cukup besar, Jaya Jaya Maju masih cukup kesulitan dalam mengelola karyawan. Hal ini berimbas tingginya attrition rate (rasio jumlah karyawan yang keluar dengan total karyawan keseluruhan) hingga lebih dari 10%.

## Business problem

Dari latar belakang tersebut pertanyaan yang diajukan dalam project ini adalah
1. Faktor apa yang mempengaruhi attririon

## Project Scope
Untuk menjawab permasalah bisnis tersebut maka aktivitas dalam project ini meliput:

1. Pemahaman data untuk menjelaskan secara deskripsi data
2. Menemukan faktor yang mempengaruhi attrition

## Persiapan
untuk menjelakan project ini, data yang diperlukan diambil dari case dicoding yang diberikan dengan akses berikut: https://github.com/dicodingacademy/dicoding_dataset/tree/main/employee

Atau data set asli diambil dari link berikut:
https://www.ibm.com/communities/analytics/watson-analytics-blog/watson-analytics-use-case-for-hr-retaining-valuable-employees/

Data tersebut berisi tentang demografi karyawan yang meliputi:

1. EmployeeId - Employee Identifier
2. Attrition - Did the employee attrition? (0=no, 1=yes)
3. Age - Age of the employee
4. BusinessTravel - Travel commitments for the job
5. DailyRate - Daily salary
6. Department - Employee Department
7. DistanceFromHome - Distance from work to home (in km)
8. Education - 1-Below College, 2-College, 3-Bachelor, 4-Master,5-Doctor
9. EducationField - Field of Education
10. EnvironmentSatisfaction - 1-Low, 2-Medium, 3-High, 4-Very High
11. Gender - Employee's gender
12. HourlyRate - Hourly salary
13. JobInvolvement - 1-Low, 2-Medium, 3-High, 4-Very High
14. JobLevel - Level of job (1 to 5)
15. JobRole - Job Roles
16. JobSatisfaction - 1-Low, 2-Medium, 3-High, 4-Very High
17. MaritalStatus - Marital Status
18. MonthlyIncome - Monthly salary
19. MonthlyRate - Mounthly rate
20. NumCompaniesWorked - Number of companies worked at
21. Over18 - Over 18 years of age?
22. OverTime - Overtime?
23. PercentSalaryHike - The percentage increase in salary last year
24. PerformanceRating - 1-Low, 2-Good, 3-Excellent, 4-Outstanding
25. RelationshipSatisfaction - 1-Low, 2-Medium, 3-High, 4-Very High
26. StandardHours - Standard Hours
27. StockOptionLevel - Stock Option Level
28. TotalWorkingYears - Total years worked
29. TrainingTimesLastYear - Number of training attended last year
30. WorkLifeBalance - 1-Low, 2-Good, 3-Excellent, 4-Outstanding
31. YearsAtCompany - Years at Company
32. YearsInCurrentRole - Years in the current role
33. YearsSinceLastPromotion - Years since the last promotion
34. YearsWithCurrManager - Years with the current manager

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

Hasil visualisasi histogram tesebut menunjukkan jumlah karyawan yang keluar lebih banyak dari yang masih bekerja.

Dominasi Karyawan Muda: Distribusi usia menunjukkan perusahaan memiliki banyak karyawan muda, yang mungkin berkaitan dengan tingginya attrition pada masa kerja awal.

Tingkat Attrition Tinggi di Awal Karir: Karyawan baru cenderung lebih sering mengundurkan diri, yang ditunjukkan oleh data years at company yang didominasi oleh pekerja dengan lama kerja 0-10 tahun

Kepuasan Sedang: Nilai kepuasan kerja dan lingkungan tidak terlalu tinggi (rata-rata 3.0–3.5), mengindikasikan perlunya perbaikan di area tertentu.

Keseimbangan Hidup-Kerja Cukup Baik: Meski tidak ideal, karyawan merasa cukup nyaman dengan keseimbangan ini.

![image](https://github.com/user-attachments/assets/f6cbe5e9-fada-4380-b2ad-e4c294edd8bb)

Hasil visualisasi pairplot menunjukkan secara umum tidak ada gambar khusus yang meunjukkan pola pengaruh linear. Indikasi hanya pada variabel lama bekerja di perusahaan year at the company.

![image](https://github.com/user-attachments/assets/7f8b9698-8ede-4555-b80c-f560f849a225)

Matriks korelasi menunjukkan hubungan linier antar variabel numerik dalam dataset karyawan. Nilai berkisar dari -1 (korelasi negatif sempurna) hingga 1 (korelasi positif sempurna). Nilai mendekati 0 menunjukkan tidak ada hubungan. Beberapa pola penting yang teridentifikasi:

Korelasi Signifikan

Age (Usia) vs. MonthlyIncome (Pendapatan Bulanan) = Korelasi: 0.50. Interpretasi: Karyawan dengan usia lebih tinggi cenderung memiliki pendapatan lebih besar. Ini mungkin terkait pengalaman atau jenjang karir.

YearsAtCompany (Lama Bekerja) vs. YearsInCurrentRole (Lama di Posisi Saat Ini) = Korelasi: 0.76. Interpretasi: Hubungan sangat kuat. Karyawan yang lama di perusahaan cenderung menempati posisi yang sama dalam waktu panjang.

YearsAtCompany vs. MonthlyIncome = Korelasi: 0.51. Interpretasi: Karyawan dengan masa kerja panjang umumnya memiliki pendapatan lebih tinggi (efek kenaikan gaji tahunan/promosi).

Attrition (Pengunduran Diri) vs. Age = Korelasi: -0.17. Interpretasi: Karyawan muda lebih mungkin mengundurkan diri.

Attrition vs. MonthlyIncome = Korelasi: -0.16. Interpretasi: Karyawan dengan pendapatan rendah lebih rentan resign.

Attrition vs. MonthlyIncome = Korelasi: -0.16. Interpretasi: Karyawan dengan pendapatan rendah lebih rentan resign.

Attrition vs. Joblevel = Korelasi: -0.17. Interpretasi: Karyawan dengan posisi rendah lebih rentan resign.

![image](https://github.com/user-attachments/assets/34a92c44-d05e-4daa-b458-0f7d28941a0a)

Data tersebut menjelaskan bahwa karyawan terbanyak adalah dari bagian RnD. Karyawan ini jarang melakukan perjalanan bisnis dan jarang untuk melakukan lebur.


# 2. Data Preperation
Pada tahap ini, olah data dilakukan untuk mempersiapkan data untuk modeling. Tahapan ini dilakukan dengan cara:

1. Melakukan perbaikan data,
2. Pembersihan data

Karena tipe data tidak memiliki masalah, maka data preparataion akan dilakukan dengan pembersihan data.

![image](https://github.com/user-attachments/assets/b386554d-0512-473b-ad63-a0287d990cd2)

Pembersiah data dilakukan terhadap data data kosong atau missing value pada variabel attrition. Hasilnya adalah terdapat 1058 data yang siap untuk diolah lebih lanjut.

![image](https://github.com/user-attachments/assets/dd5abcb3-3b3b-4e64-a5e4-61c71dd9f833)

Setelah data dibersihakn, maka dapat dihitung berapa persen karyawan yang tetap dan yang keluar. Nilai 1 untuk menunjukkan status karyawan yang sudah keluar dan nilai 0 menunjukkan karyawan yang masih bekerja. Hasil menunjukkan bahwa karyawan yang keluar adalah 16.9% dari keseluruhan karyawan.

# 3. Modeling
Pada bagian modeling, data akan disusun dalam model untuk dapat melihat faktor apa yang mempengaruhi attretion karyawan.

Untuk membuat model ini ditentukan variabel y adalah attrition, variabel x adalah semua variabel yang memiliki tipe data numeric. Model yang dengan bangun menggunakan regresi logistik.

Tujuan dari regresi ini adalah untuk melihat dampak bagaimana pengaruh faktor-faktor tersebut terhadap kemungkinan karyawan untuk keluar.

![image](https://github.com/user-attachments/assets/391e1642-61f4-4c3f-b3fd-b4d09b32a12a)

Hasilnya:

![image](https://github.com/user-attachments/assets/b0fd533b-7681-446c-addd-fb455506c2d7)

Berikut adalah interpertasi dari hasil regresi logistik

Variabel	Koefisien	Arah Pengaruh	Keterangan
Age	-0.0332	Negatif	Semakin tua, semakin kecil kemungkinan keluar.
DistanceFromHome	0.0263	Positif	Semakin jauh jarak dari rumah, semakin besar kemungkinan keluar.
EnvironmentSatisfaction	-0.3395	Negatif	Kepuasan lingkungan kerja menurunkan attrition.
JobInvolvement	-0.5781	Negatif	Keterlibatan kerja yang tinggi mengurangi attrition.
JobSatisfaction	-0.2940	Negatif	Kepuasan kerja menurunkan attrition.
WorkLifeBalance	-0.2747	Negatif	Keseimbangan hidup-kerja lebih baik mengurangi attrition.
YearsInCurrentRole	-0.1403	Negatif	Lama di posisi sekarang → lebih kecil kemungkinan keluar.
YearsSinceLastPromotion	0.1354	Positif	Semakin lama sejak promosi terakhir → lebih besar kemungkinan keluar.
Makna temuan hasil

Faktor uang (gaji, pendapatan harian/bulanan) tidak terbukti signifikan mempengaruhi attrition dalam model ini.

Faktor psikologis dan lingkungan kerja seperti JobSatisfaction, EnvironmentSatisfaction, dan JobInvolvement justru lebih kuat berpengaruh.

Hal ini menunjukkan bahwa untuk mengurangi attrition, perusahaan sebaiknya fokus pada peningkatan kepuasan kerja dan lingkungan kerja, bukan hanya menaikkan gaji.

Model

image.png

logit(p) = 4.6009 - 0.0332(Age) + 0.0263(DistanceFromHome) - 0.3395(EnvironmentSatisfaction) - 0.5781(JobInvolvement) - 0.2940(JobSatisfaction) - 0.2747(WorkLifeBalance) - 0.0156(YearsAtCompany) - 0.1403(YearsInCurrentRole) + 0.1354(YearsSinceLastPromotion)

![image](https://github.com/user-attachments/assets/545171ae-89aa-4ef7-a867-11fbd8c31da4)

**Interpretasi Hasil**

Variabel signifikan negatif (mencegah attrition): JobInvolvement: Koefisien negatif besar (sekitar -0.58), artinya semakin tinggi keterlibatan kerja, semakin kecil kemungkinan karyawan keluar.

Environment Satisfaction, Job Satisfaction, Work Life Balance, Years In CurrentRole, Age: Semua ini memiliki efek negatif terhadap attrition — artinya, kepuasan, keseimbangan hidup-kerja, dan senioritas mengurangi risiko keluar.

Variabel signifikan positif (meningkatkan attrition): Distance FromHome: Semakin jauh jarak ke kantor, semakin besar kemungkinan karyawan keluar.

Years Since Last Promotion: Semakin lama tidak dipromosikan, semakin tinggi kemungkinan keluar.

Variabel tidak signifikan (abu-abu): MonthlyIncome, MonthlyRate, DailyRate, EmployeeId, Education, PerformanceRating, JobLevel, YearsAtCompany → Semua ini tidak terbukti punya pengaruh yang berarti terhadap attrition, meskipun secara umum sering dianggap relevan.

Makna Visualisasi

Visualisasi ini memperkuat kesimpulan sebelumnya bahwa faktor-faktor psikologis dan keterlibatan kerja lebih penting daripada faktor finansial seperti gaji.

Variabel yang secara signifikan memengaruhi attrition dapat menjadi target intervensi HR, seperti:

Meningkatkan kepuasan kerja dan keterlibatan.

Memperhatikan promosi tepat waktu.

Mengelola keseimbangan kerja–hidup karyawan.

# 4. Evaluasi model
Pada tahap ini model dan hasil yang sudah dibuat sebelumnya akan dievaluasi tingkat akurasi dari hasil tersebut.

Model telah dibangun dengan Regresi Logistik, nilai koefisien akan memprediksi kemungkinan terjadinya attrition. Namun model dan nilai koefisien perlu dievaluasi.

![image](https://github.com/user-attachments/assets/a7b5a84f-2f9d-4361-b760-9b18372a329d)

Hasilnya:
![image](https://github.com/user-attachments/assets/ff40b063-794d-466d-a76b-ee4e530e340b)

**Penjelasan** 

Walaupun model memiliki akurasi tinggi 81%. Namun Model ini gagal dalam mendeteksi karyawan yang akan keluar, meskipun akurasinya tampak tinggi. Anda perlu menangani ketidakseimbangan data agar model menjadi benar-benar berguna untuk prediksi attrition.

Hal ini mungkin dikarenakan regresi logistik menilai kemungkinan dari suatu faktor y.

Untuk melakukan evaluasi model maka digunakan model KNN, RF, Boosting. Evaluasi model dilakukan dengan mse.

![image](https://github.com/user-attachments/assets/5cd74b0d-94fb-4bab-a4fa-f62db59264eb)

Hasil

![image](https://github.com/user-attachments/assets/c4d19725-55c7-443f-ac2a-b3e997003b92)

Visualisasinya adalah sebagai berikut:

![image](https://github.com/user-attachments/assets/518dec89-0f73-44ce-a610-926fabf01b7f)

Penjelasan:


KNN: Sangat lambat saat prediksi (test), karena menghitung jarak ke semua data latih.

Boosting: Berat di dua sisi — butuh waktu lama saat pelatihan dan prediksi.

Random Forest: Cepat saat train, tapi agak lambat saat prediksi dalam visualisasi ini.

Trade-off yang ditampilkan: kecepatan vs kompleksitas dari masing-masing algoritma.

# Business Dashboard

Link dashboard

https://public.tableau.com/views/ProjectpertamaDSTerapan/Dashboard1?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link

![novianto_j41b-dashboard](https://github.com/user-attachments/assets/5a54598e-797a-4b48-ac13-b7f6cd8adfee)

Dashboar tersebut menunjukkan bahwa 

1. Jumlah karyawan yang keluar (179) lebih sedikit dibandingkan dengan yang masih bekerja (879)
2. Secara rata-rata jumlah karyawan yang keluar berdasarkan gender tidak memiliki perbedaan yang besar. Hal ini menunjukkan bahwa karyawan pria atau wanita memiliki kemungkinan yang sama untuk keluar.
3. Secara rata-rata, karyawan yang keluar lebih didominasi oleh karyawan berstatus singel.
4. Perbandingan secara rata-rata terkait dengan faktor psikologi kerja (lingkungan kerja, keterlibatan kerja, tingkat jabatan, tingkat keluasan) tidak memiliki selisih yang tinggi antara karyawan yang keluar dan yang tetap bekerja. Namun rata-rata karyawan yang tetap bekerja memiliki nilai lebih tinggi dari pada karyawan yang keluar.
5. Selisih rata-rata yang besar ada pada jarak rumah dengan tempat kerja. Pada karyawan yang keluar memiliki rata-rata jarak rumah yang lebih jauh dari pada kelompok karyawan yang mtetap bekerja. 

# 5. Kesimpulan

Proyek ini menjelaskan faktor apa yang menyebabkan attrition karyawan. Hasil model ini mengindikasikan bahwa faktor yang menyebabkan karyawan keluar / attrition adalah:

JobInvolvement: Koefisien negatif besar semakin kecil kemungkinan karyawan keluar.

Environment Satisfaction, Job Satisfaction, Work Life Balance, Years In CurrentRole, Age: Semua ini memiliki efek negatif terhadap attrition — artinya, kepuasan, keseimbangan hidup-kerja, dan senioritas mengurangi risiko keluar.

Variabel signifikan positif (meningkatkan attrition): Distance From Home: Semakin jauh jarak ke kantor, semakin besar kemungkinan karyawan keluar.

Years Since Last Promotion: Semakin lama tidak dipromosikan, semakin tinggi kemungkinan keluar.

## 5.1. Rekomendasi Action Items

Dari hasil deskriptif dan analisa yang dilakukan maka rekomendasi untuk mengurangi tingkat attrition:

Peningkatan faktor psikologi kerja seperti kepuasan dan keterlibatan karyawan perlu ditingkatkan untuk dapat mengurangi tingkat attrition.
Perusahaan dapat membantu untuk karyawan memiliki tempat tinggal atau bertempat tinggal yang dekat dengan kantor untuk mengurangi tingkat attrition
Perusanaan perlu memperbaiki sistem promosi dengan memberikan kejelasan tahapan dan waktu pencapaian promosi untuk mengurangi attrition, karena semakin lama promosi maka kecenderungan karyawan untuk keluar semakin tinggi.

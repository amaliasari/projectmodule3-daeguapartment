 **1. Business Problem Understanding**

**Context**

Menurut website [The City of Hirosima](https://www.city.hiroshima.lg.jp/site/english/10621.html), Daegu merupakan sebuah kota metropolitan yang terletak di bagian Tenggara Korea Selatan. Daegu memiliki luas 883.68 sq km dengan penduduk berjumlah 2.5 juta orang. Hasil sensus penduduk tahun 2020 yang terdapat pada website [City Population](https://www.citypopulation.de/en/southkorea/cities/), Daegu merupakan sebuah kota 102 km Barat Laut Busan dengan jumlah penduduk keempat terbanyak setelah Seoul, Busan, dan Incheon. Nama Daegu berarti "Big Hills", diambil dari kondisi geografisnya yang dikelillingi perbukitan. Kota metropolitan yang berada 237 km arah Tenggara dari Seoul ini memiliki pemandangan yang indah dan kawasan wisata yang menjadi target wisatawan lokal maupun mancanegara. Dilansir dari [The Washington Post](https://www.washingtonpost.com/world/after-decades-of-economic-growth-south-korea-is-the-land-of-apartments/2013/09/15/9bd841f8-1c55-11e3-8685-5021e0c41964_story.html), apartment di Korea Selatan "*strictly residential, with one or two guarded entrances. Only residents or approved visitors may enter*" sehingga menjadikannya lebih aman dibanding rumah yang tidak selalu memiliki gerbang yang dijaga. Selain itu apartment umumnya memiliki tempat bermain untuk anak-anak (*playground*) dan fasilitas lain yang tidak dimiliki oleh rumah seperti *fitness center*. Terbatasnya luas area Daegu, banyaknya penduduk dan wisatawan, serta keamanan dan fasilitas yang disediakan oleh apartment menjadikan apartment sebagai pilihan favorit untuk tinggal.

Banyak aspek yang dapat menjadi pertimbangan untuk memilih apartment terbaik. Dalam menentukan nilai/harga, developer atau pemilik unit apartment akan mempertimbangkan lokasi, fasilitas, dan fitur-fitur lain yang diberikan. Pembeli pun juga akan mempertimbangkan hal yang sama dalam proses pemilihan apartment yang ingin dibeli. Namun, tidak mudah untuk menetapkan harga yang tepat untuk sebuah unit apartment karena setiap fitur/fasilitas yang diberikan akan mempengaruhi harga jual/sewa sebuah unit apartment.

--------

**Problem Statement**


Penentuan harga jual apartment apartment yang tepat menjadi salah satu tantangan terbesar dari proses jual-beli sebuah *apartment unit* di Daegu. Oleh karena itu, diperlukan sebuah jalan keluar untuk mengatasi hal ini. Solusi ini diharapkan dapat membantu para penjual menemukan harga yang sesuai dengan fasilitas yang ditawarkan. Penjual tidak ingin menjual dengan harga yang terlalu murah atau menetapkan harga yang terlalu tinggi sehingga tidak ada yang berminat, dan pembeli tidak ingin membeli apartment yang tidak sesuai antara harga dan fasilitas yang diberikan. Adanya analisis terhadap *history* penjualan apartment dapat menjadi acuan yang akan membantu ketika penjual memberikan *offering* harga sehingga pembeli tidak perlu khawatir dengan harga yang *overpriced* atau *underpriced*. Dengan adanya prediksi ini, **Kesesuaian harga dengan fasilitas yang tersedia di dalam dan di sekitar apartment yang dijual sangat penting agar dapat terjadi sebuah kesepakatan antara penjual dan pembeli**.

--------

**Goals**

Penjual perlu memiliki pola dari penjualan-penjualan apartment sebelumnya untuk **mendapatkankan prediksi harga jual unit apartment sesuai dengan fasilitas yang ditawarkan di apartment tersebut** agar ketika menetapkan harga sebuah unit apartment tidak terjadi *underprice* atau *overprice* dan pembeli tidak *law-balling* apartment tersebut sehingga dapat terjadi kesepakatan jual-beli dan tidak ada pihak yang merasa dirugikan atau terpaksa setelah terjadinya transaksi jual-beli apartment. Perbedaan fasilitas dari setiap apartment, seperti tipe *hallway*, jarak tempuh ke stasiun *subway*, jumlah parkir *basement* yang tersedia, dan tahun berdirinya bangunan tersebut dapat memengaruhi harga atau nilai jual sebuah unit apartment sehingga penjual dan pembeli dapat melakukan transaksi dengan harga terbaik. 

Pola yang didapat dari penjualan apartment-apartment sebelumnya dapat memberikan prediksi harga yang terbaik sehingga proses transaksi dapat lebih cepat dilakukan dan tidak ada pihak yang merasa rugi dikemudian hari karena ketidaksesuaian harga dengan *features* yang ditawarkan oleh apartment tersebut.

--------

**Analytic Approach**

Untuk menemukan harga jual yang terbaik, perlu dilakukan analisis data dengan cara menemukan pola dari fitur-fitur yang ada dari penjualan apartment yang pernah terjadi di Daegu serta menemukan algoritma untuk membangun model regresi yang akan membantu menemukan *the fair and reasonable price* dari sebuah apartment sesuai dengan fitur yang ditawarkan. Selain itu, akan dilakukan analisis untuk menemukan fitur yang paling berpengaruh terhadap target atau harga jual unit apartment.

--------

**Metric Evaluation**

Evaluasi metrik yang akan digunakan adalah MAE, MAPE, RMSE, dan R-Squared. RMSE mengukur perbedaan nilai dari prediksi sebuah model. Semakin kecil nilai RMSE, semakin akurat prediksi harga jual. MAE digunakan untuk merepresentasikan nilai kesalahan rata-rata mutlak *(absolut error)*, sedangkan MAPE merepresentasikan persentase kesalahan rata-rata mutlak *(absolut)*. Sama halnya dengan RMSE, semakin kecil nilai MAE dan MAPE,semakin akurat prediksi harga jualnya.

R-squared merupakan nilai yang memperlihatkan besar pengaruh variabel independen terhadap dependen. Nilai R-squared berkisar antara 0 sampai 1 yang merupakan indikasi besarnya kombinasi variable independen secara bersama-sama memengaruhi variable dependen. Semakin mendekati 1, semakin fit model terhadap data observasi. Namun, dikutip dari [National Library of Medicine](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2892436/), *"R2 is inappropriate when used for demonstrating the performance or validity of a certain nonlinear model"*, artinya R-squared tidak valid untuk model nonlinear.

--------

**2. Data Understanding**

- Dataset merupakan data transaksi jual-beli apartment di Daegu dari Agustus 2007 hingga 2017. 
- Setiap baris data merepresentasikan informasi terkait properti, fasilitas yang ditawarkan, dan harga jualnya.

**Attributes Information**

| **Attribute** | **Data Type** | **Description** |
| --- | --- | --- |
| HallwayType | Object | Tipe hallway pada apartment |
| TimeToSubway | Object | Waktu yang diperlukan ke *subway* terdekat |
| SubwayStation | Object | Stasiun *subway* terdekat |
| N_FacilitiesNearBy(ETC) | Float | Jumlah fasilitas ETC di sekitar |
| N_FacilitiesNearBy(PublicOffice) | Float | Jumlah kantor pemerintahan (*public office*) di sekitar |
| N_SchoolNearBy(University) | Float | Jumlah universitas di sekitar |
| N_Parkinglot(Basement) | Float | Jumlah area parkir *basement* |
| YearBuilt | Integer | Tahun pembangunan apartment |
| N_FacilitiesInApt | Integer | Jumlah Fasilitas di dalam Apartment |
| Size(sqf) | Integer | Luas apartment |
| SalePrice | Integer | Harga jual apartment |

<br>

--------

**3. Data Preprocessing**

Pada tahap ini dilakukan cleaning pada data. Data yang sudah bersih akan digunakan untuk proses analisis berikutnya. Beberapa hal yang dilakukan pada tahap ini adalah sebagai berikut.

1. Mengecek missing value dan data duplikat
2. Drop fitur yang kolinear dengan fitur lain
3. Menangani outlier

--------
**Clean Dataset**


![image](https://user-images.githubusercontent.com/107789740/188471913-bee8785a-b61b-45bf-91f0-c81e9186daca.png)

<br>
**Modeling**

![image](https://user-images.githubusercontent.com/107789740/188472054-7d395e32-4655-43c0-851e-945fa51f44a4.png)

<br>
**Feature Importance**

<img width="727" alt="image" src="https://user-images.githubusercontent.com/107789740/188481580-8815ff69-d59c-462b-8578-129d3416c204.png">


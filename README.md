# Tugas ke-4 OAK

## 1. Struktur Antar Hubungan dan Contohnya

Struktur antar hubungan dalam sistem komputer mengacu pada cara berbagai komponen perangkat keras (CPU, memori, perangkat I/O) saling terhubung untuk berkomunikasi dan bertukar data. Struktur ini dapat berupa:
	
 • Bus: Jalur komunikasi bersama yang digunakan oleh semua perangkat. Contoh: PCIe pada motherboard.
	
 • Point-to-Point: Koneksi langsung antar perangkat tanpa melalui jalur bersama. Contoh: Direct Media Interface (DMI) antara CPU dan chipset Intel.
	
 • Jaringan Interkoneksi: Struktur yang lebih kompleks, seperti crossbar switch pada sistem multiprosesor.

Contoh Kasus:
Dalam sebuah komputer, CPU, RAM, dan GPU terhubung melalui bus sistem. Ketika CPU meminta data dari RAM, data tersebut harus melewati bus terlebih dahulu. Jika GPU juga mengakses RAM pada saat yang sama, maka akan terjadi antrian yang bisa memperlambat kinerja.

## 2. Penyebab Penurunan Kinerja Saat Terlalu Banyak Perangkat Terhubung ke Bus

Ketika terlalu banyak modul atau perangkat dihubungkan ke bus, beberapa faktor yang menyebabkan penurunan kinerja adalah:

  1.	Kontensi Bus (Bus Contention) – Banyak perangkat bersaing untuk menggunakan bus, menyebabkan waktu tunggu lebih lama.
 
  2.	Kolisi Data (Data Collision) – Jika tidak ada mekanisme kontrol yang baik, beberapa perangkat bisa mengirim data secara bersamaan, mengakibatkan tabrakan data.
 
  3.	Overhead Manajemen Bus – Semakin banyak perangkat yang terhubung, semakin kompleks pengaturan prioritas aksesnya, yang bisa memperlambat operasi secara keseluruhan.
 
  4.	Latensi Propagasi – Data membutuhkan waktu lebih lama untuk dikirim karena jalur komunikasi harus melayani lebih banyak perangkat.
 
  5.	Bandwidth Terbatas – Bus memiliki kapasitas maksimal untuk mentransfer data, dan jika terlalu banyak perangkat menggunakannya, bandwidth tersebut harus dibagi, mengurangi kecepatan akses per perangkat.

Analogi:
Bayangkan sebuah jalan raya dengan beberapa jalur. Jika hanya sedikit mobil, semua bisa melaju dengan cepat. Tapi jika terlalu banyak mobil (perangkat), lalu lintas menjadi padat dan setiap mobil harus menunggu giliran untuk bergerak, sehingga kecepatan keseluruhan turun.

## 3. Mengapa Perangkat dengan Prioritas 16 Memiliki Waktu Tunggu Rata-Rata Paling Rendah?

Biasanya, perangkat dengan prioritas lebih tinggi mendapat kesempatan akses lebih dulu, sedangkan yang berprioritas rendah harus menunggu. Namun, dalam sistem tertentu, perangkat dengan prioritas 16 bisa memiliki waktu tunggu rata-rata lebih rendah karena:

  1. Sistem Preemptive Scheduling – Jika perangkat prioritas tinggi hanya digunakan sesekali, perangkat dengan prioritas lebih rendah bisa mendapatkan akses lebih sering.

  2. Burst Mode vs. Sporadic Mode – Jika perangkat prioritas tinggi sering mengambil alih bus dalam burst panjang, perangkat prioritas lebih rendah bisa tetap mendapatkan akses lebih cepat dalam selang waktu idle.

  3. Distribusi Beban Kerja – Jika beban kerja sistem lebih seimbang, perangkat dengan prioritas lebih rendah mungkin memiliki waktu tunggu lebih stabil dibandingkan perangkat prioritas tinggi yang sering tertunda karena antrian panjang.


Kondisi di Mana Hal Ini Tidak Berlaku:

• Starvation (Kelaparan Sumber Daya) – Jika perangkat prioritas tinggi terus-menerus menggunakan bus tanpa jeda, perangkat dengan prioritas lebih rendah bisa mengalami waktu tunggu yang sangat panjang.

• Sistem dengan Fixed Priority tanpa Preemption – Dalam sistem yang tidak mendukung interupsi berbasis prioritas, perangkat dengan prioritas lebih rendah akan selalu menunggu hingga yang lebih tinggi selesai.

• Beban Kerja Tidak Merata – Jika sistem lebih banyak melayani perangkat prioritas tinggi, perangkat dengan prioritas lebih rendah akan lebih lama menunggu giliran.

Analogi:
Bayangkan antrean di bank. Biasanya, pelanggan VIP (prioritas tinggi) dilayani lebih dulu. Namun, jika pelanggan VIP hanya sesekali datang, pelanggan biasa (prioritas lebih rendah) bisa mendapatkan layanan lebih cepat secara rata-rata. Tetapi jika terlalu banyak VIP datang sekaligus, pelanggan biasa harus menunggu lama.

-- phpMyAdmin SQL Dump
-- version 5.2.1
-- https://www.phpmyadmin.net/
--
-- Host: localhost:3306
-- Waktu pembuatan: 01 Jan 2024 pada 16.29
-- Versi server: 8.0.30
-- Versi PHP: 8.2.13

SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
START TRANSACTION;
SET time_zone = "+00:00";


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;

--
-- Database: `pkbm`
--

-- --------------------------------------------------------

--
-- Struktur dari tabel `admin`
--

CREATE TABLE `admin` (
  `id` int NOT NULL,
  `username` varchar(255) DEFAULT NULL,
  `nama` varchar(255) DEFAULT NULL,
  `password` longtext NOT NULL,
  `created_at` timestamp NULL DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

--
-- Dumping data untuk tabel `admin`
--

INSERT INTO `admin` (`id`, `username`, `nama`, `password`, `created_at`, `updated_at`) VALUES
(1, 'admin', 'admin', '$2y$12$V58XvgLH3mGPvEyWouYH6uokpntRpNwD3fgNruD2jncvXMnwUxAra', NULL, '2023-12-04 16:13:35');

-- --------------------------------------------------------

--
-- Struktur dari tabel `guru`
--

CREATE TABLE `guru` (
  `id` int NOT NULL,
  `username` varchar(255) DEFAULT NULL,
  `nama` varchar(255) DEFAULT NULL,
  `nip` varchar(30) DEFAULT NULL,
  `alamat` varchar(500) DEFAULT NULL,
  `jenis_kelamin` varchar(100) DEFAULT NULL,
  `password` longtext NOT NULL,
  `created_at` timestamp NULL DEFAULT NULL,
  `Updated_at` timestamp NULL DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

--
-- Dumping data untuk tabel `guru`
--

INSERT INTO `guru` (`id`, `username`, `nama`, `nip`, `alamat`, `jenis_kelamin`, `password`, `created_at`, `Updated_at`) VALUES
(13, 'Feni', 'Feni', '12345', 'Jln.Sepakat', 'Perempuan', '$2y$12$xds/pDJOotJU/zN.Bfbr2eMzwPoFTAVNgUxRdp4/I6s8D5wPHzhny', '2023-12-05 14:41:45', '2023-12-05 14:41:45'),
(14, 'fadhilah', 'Feni Febriani', '12345678', 'Jln.Jalan', 'Perempuan', '$2y$12$EWFufjh5EAnrUdygYd9cZejdBt3KeKqvtAriU8z09Az7C87WzlE6y', '2023-12-12 00:06:59', '2023-12-12 00:06:59'),
(16, 'Rayleigh', 'Silvers Rayleigh', '1234567890', 'Jln.Jalan', 'Laki-laki', '$2y$12$awamOMOrKkgDpAHZRjKT0.SmYFvEQAWeK6SEekX6bytM7FYde3MD.', '2023-12-16 02:23:40', '2023-12-16 02:23:40');

-- --------------------------------------------------------

--
-- Struktur dari tabel `kelas`
--

CREATE TABLE `kelas` (
  `id` int NOT NULL,
  `id_guru` int DEFAULT NULL,
  `nama_kelas` varchar(100) DEFAULT NULL,
  `created_at` timestamp NULL DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

--
-- Dumping data untuk tabel `kelas`
--

INSERT INTO `kelas` (`id`, `id_guru`, `nama_kelas`, `created_at`, `updated_at`) VALUES
(1, 13, 'KELAS I (A)', '2023-12-05 14:54:35', '2023-12-05 14:54:35'),
(3, 16, 'III (B)', '2023-12-16 02:24:38', '2023-12-16 02:24:38');

-- --------------------------------------------------------

--
-- Struktur dari tabel `kuis`
--

CREATE TABLE `kuis` (
  `id` int NOT NULL,
  `mapel_id` int NOT NULL,
  `nama_kuis` varchar(255) NOT NULL,
  `soal_kuis` varchar(255) NOT NULL,
  `opsi_a` varchar(255) NOT NULL,
  `opsi_b` varchar(255) NOT NULL,
  `opsi_c` varchar(255) NOT NULL,
  `opsi_d` varchar(255) NOT NULL,
  `kunci_jawaban` varchar(255) NOT NULL,
  `tenggat` datetime NOT NULL,
  `deskripsi` longtext NOT NULL,
  `created_at` timestamp NULL DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

--
-- Dumping data untuk tabel `kuis`
--

INSERT INTO `kuis` (`id`, `mapel_id`, `nama_kuis`, `soal_kuis`, `opsi_a`, `opsi_b`, `opsi_c`, `opsi_d`, `kunci_jawaban`, `tenggat`, `deskripsi`, `created_at`, `updated_at`) VALUES
(2, 3, 'Tokoh-tokoh Berpengaruh dalam Sejarah', 'Alexander the Great Adalah ?', 'Kaisar Romawi', 'Panglima Perang Yunani', 'Raja Persia', 'Filsuf Romawi', 'Panglima Perang Yunani', '2023-12-11 08:00:00', 'Silahkan pilih jawaban yang menurut anda paling benar.', '2023-12-06 21:27:10', '2023-12-12 16:35:22'),
(3, 3, 'Tokoh-tokoh Berpengaruh dalam Sejarah', 'Cleopatra', 'Ratu Mesir Kuno', 'Pemimpin Babilonia', 'Perdana Menteri Yunani', 'Ahli Matematika Romawi', 'Ratu Mesir Kuno', '2023-12-07 08:00:00', 'Silahkan pilih jawaban yang menurut anda paling benar.', '2023-12-06 21:29:01', '2023-12-06 21:29:01');

-- --------------------------------------------------------

--
-- Struktur dari tabel `mapel`
--

CREATE TABLE `mapel` (
  `id` int NOT NULL,
  `kelas_id` int DEFAULT NULL,
  `mapel` varchar(255) NOT NULL,
  `materi` longtext CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NOT NULL,
  `deskripsi` longtext NOT NULL,
  `created_at` timestamp NULL DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

--
-- Dumping data untuk tabel `mapel`
--

INSERT INTO `mapel` (`id`, `kelas_id`, `mapel`, `materi`, `deskripsi`, `created_at`, `updated_at`) VALUES
(2, 1, 'Ilmu Pengetahuan Alam', 'Tentang Algoritma', 'Menjelaskan tentang materi dasar dari Matematika hingga Algoritma', '2023-12-06 03:48:26', '2023-12-06 03:48:26'),
(3, 1, 'Ilmu Pengetahuan Sosial', 'Sosial Dasar', 'Menjelaskan tentang system ilmu sosial dasar dan praktek', '2023-12-06 03:49:00', '2023-12-06 03:49:00'),
(4, 3, 'Matematika', 'Rumus Persegi', 'Mtk sulit dipahami', '2023-12-16 02:28:58', '2023-12-16 02:28:58');

-- --------------------------------------------------------

--
-- Struktur dari tabel `nilai`
--

CREATE TABLE `nilai` (
  `id` int NOT NULL,
  `siswa_id` int NOT NULL,
  `kuis_id` int NOT NULL,
  `tugas_id` int NOT NULL,
  `ujian_id` int NOT NULL,
  `jawaban` varchar(255) NOT NULL,
  `nilai` float NOT NULL,
  `created_at` timestamp NULL DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

--
-- Dumping data untuk tabel `nilai`
--

INSERT INTO `nilai` (`id`, `siswa_id`, `kuis_id`, `tugas_id`, `ujian_id`, `jawaban`, `nilai`, `created_at`, `updated_at`) VALUES
(1, 4, 2, 0, 0, 'Kaisar Romawi', 0, '2023-12-12 16:20:35', '2023-12-12 16:20:35'),
(2, 4, 3, 0, 0, 'Ratu Mesir Kuno', 100, '2023-12-12 16:20:35', '2023-12-12 16:20:35'),
(3, 4, 0, 1, 0, 'a', 0, '2023-12-12 16:20:46', '2023-12-12 16:20:46');

-- --------------------------------------------------------

--
-- Struktur dari tabel `pengumuman`
--

CREATE TABLE `pengumuman` (
  `id` int NOT NULL,
  `judul` varchar(255) NOT NULL,
  `foto` varchar(500) NOT NULL,
  `deskripsi` longtext NOT NULL,
  `created_at` timestamp NULL DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

--
-- Dumping data untuk tabel `pengumuman`
--

INSERT INTO `pengumuman` (`id`, `judul`, `foto`, `deskripsi`, `created_at`, `updated_at`) VALUES
(2, 'PBL', 'app/image/beranda/2-1700281613-f35GO.jpg', 'ASDAsdasd', '2023-11-03 09:52:44', '2023-11-17 21:26:53');

-- --------------------------------------------------------

--
-- Struktur dari tabel `siswa`
--

CREATE TABLE `siswa` (
  `id` int NOT NULL,
  `id_kelas` int NOT NULL,
  `username` varchar(255) NOT NULL,
  `nama` varchar(255) NOT NULL,
  `nim` varchar(255) NOT NULL,
  `jenis_kelamin` varchar(25) NOT NULL,
  `alamat` varchar(500) NOT NULL,
  `email` varchar(50) NOT NULL,
  `password` longtext NOT NULL,
  `tanggal_lahir` date NOT NULL,
  `no_hp` varchar(15) NOT NULL,
  `created_at` timestamp NULL DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

--
-- Dumping data untuk tabel `siswa`
--

INSERT INTO `siswa` (`id`, `id_kelas`, `username`, `nama`, `nim`, `jenis_kelamin`, `alamat`, `email`, `password`, `tanggal_lahir`, `no_hp`, `created_at`, `updated_at`) VALUES
(3, 1, 'fadhilah', 'Feni Febriani', '3042022042', 'Perempuan', 'Jln.Jalan', 'febrianifeni012@gmail.com', '$2y$12$5tpo6hZwK7PxlUpDS9RUoeb/re6uWd/pPlPIDev2FnApioAiXYSGK', '2000-12-12', '0895332009038', '2023-12-06 03:28:23', '2023-12-06 03:28:23'),
(4, 1, 'yusuf', 'Muhammad Yusuf', '30420220423', 'Laki-laki', 'North Blue', 'hakim@gmail.com', '$2y$12$VRXi0NULNYVuIIFjenHthOS2C8TEMgsvbcNz6z0a3azfAKOawJu8O', '2023-12-13', '0895332009039', '2023-12-06 20:32:17', '2023-12-06 20:32:17'),
(5, 3, 'Luffy', 'Monkey D. Luffy', '1234567890', 'Laki-laki', 'East Blue', 'Luffy12@gmail.com', '$2y$12$pDdBjL9gWThqA8BOksStY.jlhOiz0eQm1/BnQwzE805UxFm6NHIhG', '2004-02-29', '0895332009037', '2023-12-16 02:27:32', '2023-12-16 02:27:32');

-- --------------------------------------------------------

--
-- Struktur dari tabel `soal_ujian`
--

CREATE TABLE `soal_ujian` (
  `id` int NOT NULL,
  `ujian_id` int NOT NULL,
  `soal` varchar(255) NOT NULL,
  `opsi_a` varchar(255) NOT NULL,
  `opsi_b` varchar(255) NOT NULL,
  `opsi_c` varchar(255) NOT NULL,
  `opsi_d` varchar(255) NOT NULL,
  `kunci_jawaban` varchar(255) NOT NULL,
  `created_at` timestamp NULL DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

--
-- Dumping data untuk tabel `soal_ujian`
--

INSERT INTO `soal_ujian` (`id`, `ujian_id`, `soal`, `opsi_a`, `opsi_b`, `opsi_c`, `opsi_d`, `kunci_jawaban`, `created_at`, `updated_at`) VALUES
(1, 1, 'Pulau Komodo terletak di provinsi?\n\n\n', ' Bali\n\n', ' NTT\n\n', ' NTB', ' Jawa Timur', 'NTT', '2023-12-12 00:40:04', '2023-12-12 00:40:04'),
(2, 1, 'Siapa Presiden Indonesia ketiga Indonesia? ', ' BJ. Habibie', ' Joko Widodo', ' Soekarno', ' Abdurrahman Wahid', ' BJ. Habibie', '2023-12-12 00:40:04', '2023-12-12 00:40:04'),
(3, 1, 'Apa singkatan dari MPR? ', ' Majelis Perwakilan Rakyat', ' Majelis Permusyawaratan Rakyat', ' Majelis Perhimpunan Rakyat', ' Majelis Perserikatan Rakyat', ' Majelis Permusyawaratan Rakyat', '2023-12-12 00:40:04', '2023-12-12 00:40:04'),
(4, 1, ' Pada tanggal berapakah Hari Lahir Pancasila diperingati? ', ' 17 Agustus', ' 1 Maret', ' 1 Juni ', ' 1 Desember ', ' 1 Juni ', '2023-12-12 00:40:04', '2023-12-12 00:40:04'),
(5, 1, 'Apa julukan terkenal dari negara Korea Selatan?', ' Negeri Tirai Bambu', ' Negeri Gingseng', ' Zamrud Khatulistiwa', ' Negeri Kincir Angin', ' Negeri Gingseng', '2023-12-12 00:40:04', '2023-12-12 00:40:04'),
(6, 1, ' Tanah yang baik untuk pertanian adalah?', ' Humus', ' Pasir', ' Liat', ' Cadas', 'Humus', '2023-12-12 00:40:04', '2023-12-12 00:40:04'),
(7, 1, ' Bumi berputar pada porosnya pada kemiringan… derajat.', ' 23,5', ' 25,5', ' 24,5', ' 26,5', ' 23,5', '2023-12-12 00:40:04', '2023-12-12 00:40:04'),
(8, 1, ' Apa nama mata uang dari negara Thailand? ', ' Won', ' Rupiah', ' Dollar', ' Baht', ' Baht', '2023-12-12 00:40:04', '2023-12-12 00:40:04'),
(9, 1, 'Danau terbesar di dunia adalah… ', ' Danau Toba', ' Danau Baikal', ' Danau Kaspia', ' Danau Victoria', ' Danau Kaspia', '2023-12-12 00:40:04', '2023-12-12 00:40:04'),
(10, 1, 'Disebut apakah binatang yang dapat hidup di dua alam, yaitu darat dan laut? ', ' Amfibi ', ' Mamalia', ' Reptil', ' Pisces', ' Amfibi ', '2023-12-12 00:40:04', '2023-12-12 00:40:04'),
(11, 1, 'Yang \'bukan\' merupakan ciri surat dinas adalah ', ' Terdapat kop surat', ' Bahasa bebas', ' Terdapat nomor, perihal, dan lampiran', ' Ada stempel lembaga', ' Bahasa bebas', '2023-12-12 00:40:04', '2023-12-12 00:40:04'),
(12, 1, 'Dikisahkan hiduplah sekelompok binatang di sebuah kampung.\n\nPernyataan tersebut merupakan bagian struktur isi fabel yaitu', ' orientasi', ' konflik', ' klimaks', ' resolusi', ' orientasi', '2023-12-12 00:40:04', '2023-12-12 00:40:04'),
(13, 1, 'Kus mulai menawarkan kerja sama dengan Jiji.\n\nPernyataan tersebut merupakan bagian struktur fabel yaitu', ' orientasi', ' klimaks', ' resolusi', ' koda', ' koda', '2023-12-12 00:40:04', '2023-12-12 00:40:04'),
(14, 1, 'Apa fungsi dari kalimat interrogatif?', ' Memberikan perintah', ' Menanyakan sesuatu', ' Memberikan penjelasan', ' Menyatakan fakta', ' Menanyakan sesuatu', '2023-12-12 00:40:04', '2023-12-12 00:40:04'),
(15, 1, 'Berikut ini yang termasuk dalam karya sastra adalah', ' Majalah\n', ' Surat kabar', ' Novel', ' Panduan wisata', ' Novel', '2023-12-12 00:40:04', '2023-12-12 00:40:04'),
(16, 1, 'Perhatikan kalimat berikut: \"Saya akan pergi ke pasar\". Kata yang termasuk dalam kalimat tersebut adalah', ' Subjek', ' Predikat', ' Objek', ' Keterangan', ' Subjek', '2023-12-12 00:40:04', '2023-12-12 00:40:04'),
(17, 1, 'Kalimat \"Ani membeli bunga di toko\" menggunakan pola', ' SPO', ' SOP', ' OPS', ' OSP', ' SPO', '2023-12-12 00:40:04', '2023-12-12 00:40:04'),
(18, 1, 'Apa yang dimaksud dengan sinonim?', ' Kata yang memiliki arti yang sama', ' Kata yang memiliki arti yang berlawanan', ' Kata yang tidak memiliki arti', ' Kata yang tidak memiliki ejaan yang sama', ' Kata yang memiliki arti yang sama', '2023-12-12 00:40:04', '2023-12-12 00:40:04');

-- --------------------------------------------------------

--
-- Struktur dari tabel `telusuri`
--

CREATE TABLE `telusuri` (
  `id` int NOT NULL,
  `judul` varchar(255) NOT NULL,
  `link` longtext NOT NULL,
  `created_at` timestamp NULL DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

--
-- Dumping data untuk tabel `telusuri`
--

INSERT INTO `telusuri` (`id`, `judul`, `link`, `created_at`, `updated_at`) VALUES
(3, 'DJ JEJE RIMEX', 'd9AEIWblTaA?si=I8jB1BZXvjrSQzOJ', '2023-11-08 23:59:08', '2023-11-17 21:20:38'),
(5, 'UJIAN MODUL Pusat Kegiatan Belajar Masyarakat [PKBM]', 'A94y-rKcfDE?si=dzT_-6eR2BhOCNBb', '2023-12-10 22:41:07', '2023-12-10 22:41:07');

-- --------------------------------------------------------

--
-- Struktur dari tabel `tugas`
--

CREATE TABLE `tugas` (
  `id` int NOT NULL,
  `mapel_id` int NOT NULL,
  `nama_tugas` varchar(255) NOT NULL,
  `soal_tugas` varchar(255) NOT NULL,
  `opsi_a` varchar(255) NOT NULL,
  `opsi_b` varchar(255) NOT NULL,
  `opsi_c` varchar(255) NOT NULL,
  `opsi_d` varchar(255) NOT NULL,
  `kunci_jawaban` varchar(255) NOT NULL,
  `tenggat` datetime NOT NULL,
  `deskripsi` longtext NOT NULL,
  `created_at` timestamp NULL DEFAULT NULL,
  `Updated_at` timestamp NULL DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

--
-- Dumping data untuk tabel `tugas`
--

INSERT INTO `tugas` (`id`, `mapel_id`, `nama_tugas`, `soal_tugas`, `opsi_a`, `opsi_b`, `opsi_c`, `opsi_d`, `kunci_jawaban`, `tenggat`, `deskripsi`, `created_at`, `Updated_at`) VALUES
(1, 2, 'Ilmu Pengetahuan Alam', 'hgdhjasdghasd', 'a', 'b', 'c', 'd', 'b', '2023-12-07 20:00:00', 'asasasas', '2023-12-07 12:40:25', '2023-12-07 12:40:25');

-- --------------------------------------------------------

--
-- Struktur dari tabel `ujian`
--

CREATE TABLE `ujian` (
  `id` int NOT NULL,
  `mapel_id` int NOT NULL,
  `nama_ujian` varchar(255) NOT NULL,
  `tenggat` datetime NOT NULL,
  `deskripsi` longtext NOT NULL,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  `updated_at` timestamp NULL DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

--
-- Dumping data untuk tabel `ujian`
--

INSERT INTO `ujian` (`id`, `mapel_id`, `nama_ujian`, `tenggat`, `deskripsi`, `created_at`, `updated_at`) VALUES
(1, 3, 'ppp', '2023-12-09 08:00:00', 'kucing putihh', '2023-12-08 20:37:14', '2023-12-08 20:37:14'),
(2, 3, 'Ujian Tingkat Dasar', '2023-12-09 22:00:00', 'Jesgdjagsjd', '2023-12-09 10:16:13', '2023-12-09 10:16:13');

-- --------------------------------------------------------

--
-- Struktur dari tabel `users`
--

CREATE TABLE `users` (
  `id` int NOT NULL,
  `id_admin` int DEFAULT NULL,
  `id_siswa` int DEFAULT NULL,
  `id_guru` int DEFAULT NULL,
  `password` int DEFAULT NULL,
  `role` int DEFAULT NULL,
  `created_at` timestamp NULL DEFAULT NULL,
  `Updated_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

--
-- Indexes for dumped tables
--

--
-- Indeks untuk tabel `admin`
--
ALTER TABLE `admin`
  ADD PRIMARY KEY (`id`);

--
-- Indeks untuk tabel `guru`
--
ALTER TABLE `guru`
  ADD PRIMARY KEY (`id`);

--
-- Indeks untuk tabel `kelas`
--
ALTER TABLE `kelas`
  ADD PRIMARY KEY (`id`);

--
-- Indeks untuk tabel `kuis`
--
ALTER TABLE `kuis`
  ADD PRIMARY KEY (`id`);

--
-- Indeks untuk tabel `mapel`
--
ALTER TABLE `mapel`
  ADD PRIMARY KEY (`id`);

--
-- Indeks untuk tabel `nilai`
--
ALTER TABLE `nilai`
  ADD PRIMARY KEY (`id`);

--
-- Indeks untuk tabel `pengumuman`
--
ALTER TABLE `pengumuman`
  ADD PRIMARY KEY (`id`);

--
-- Indeks untuk tabel `siswa`
--
ALTER TABLE `siswa`
  ADD PRIMARY KEY (`id`);

--
-- Indeks untuk tabel `soal_ujian`
--
ALTER TABLE `soal_ujian`
  ADD PRIMARY KEY (`id`);

--
-- Indeks untuk tabel `telusuri`
--
ALTER TABLE `telusuri`
  ADD PRIMARY KEY (`id`);

--
-- Indeks untuk tabel `tugas`
--
ALTER TABLE `tugas`
  ADD PRIMARY KEY (`id`);

--
-- Indeks untuk tabel `ujian`
--
ALTER TABLE `ujian`
  ADD PRIMARY KEY (`id`);

--
-- Indeks untuk tabel `users`
--
ALTER TABLE `users`
  ADD PRIMARY KEY (`id`);

--
-- AUTO_INCREMENT untuk tabel yang dibuang
--

--
-- AUTO_INCREMENT untuk tabel `admin`
--
ALTER TABLE `admin`
  MODIFY `id` int NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=2;

--
-- AUTO_INCREMENT untuk tabel `guru`
--
ALTER TABLE `guru`
  MODIFY `id` int NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=17;

--
-- AUTO_INCREMENT untuk tabel `kelas`
--
ALTER TABLE `kelas`
  MODIFY `id` int NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=4;

--
-- AUTO_INCREMENT untuk tabel `kuis`
--
ALTER TABLE `kuis`
  MODIFY `id` int NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=4;

--
-- AUTO_INCREMENT untuk tabel `mapel`
--
ALTER TABLE `mapel`
  MODIFY `id` int NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=5;

--
-- AUTO_INCREMENT untuk tabel `nilai`
--
ALTER TABLE `nilai`
  MODIFY `id` int NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=4;

--
-- AUTO_INCREMENT untuk tabel `pengumuman`
--
ALTER TABLE `pengumuman`
  MODIFY `id` int NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=3;

--
-- AUTO_INCREMENT untuk tabel `siswa`
--
ALTER TABLE `siswa`
  MODIFY `id` int NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=6;

--
-- AUTO_INCREMENT untuk tabel `soal_ujian`
--
ALTER TABLE `soal_ujian`
  MODIFY `id` int NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=21;

--
-- AUTO_INCREMENT untuk tabel `telusuri`
--
ALTER TABLE `telusuri`
  MODIFY `id` int NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=6;

--
-- AUTO_INCREMENT untuk tabel `tugas`
--
ALTER TABLE `tugas`
  MODIFY `id` int NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=2;

--
-- AUTO_INCREMENT untuk tabel `ujian`
--
ALTER TABLE `ujian`
  MODIFY `id` int NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=3;

--
-- AUTO_INCREMENT untuk tabel `users`
--
ALTER TABLE `users`
  MODIFY `id` int NOT NULL AUTO_INCREMENT;
COMMIT;

/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;

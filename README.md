-- phpMyAdmin SQL Dump
-- version 4.8.5
-- https://www.phpmyadmin.net/
--
-- Host: 127.0.0.1
-- Generation Time: Apr 14, 2020 at 04:34 AM
-- Server version: 10.1.38-MariaDB
-- PHP Version: 7.3.2

SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
SET AUTOCOMMIT = 0;
START TRANSACTION;
SET time_zone = "+00:00";


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;

--
-- Database: `penyewaan_lapangan_futsal`
--

-- --------------------------------------------------------

--
-- Table structure for table `menyewa`
--

CREATE TABLE `menyewa` (
  `id_menyewa` varchar(10) NOT NULL,
  `Tanggal_main` varchar(50) NOT NULL,
  `id_pelanggan` varchar(10) NOT NULL,
  `id_waktu_main` varchar(10) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

--
-- Dumping data for table `menyewa`
--

INSERT INTO `menyewa` (`id_menyewa`, `Tanggal_main`, `id_pelanggan`, `id_waktu_main`) VALUES
('MY0001', '15 Maret 2020', 'PL0001', 'WK0003'),
('MY0002', '15 Maret 2020', 'PL0002', 'WK0004'),
('MY0003', '16 Maret 2020', 'PL0003', 'WK0001'),
('MY0004', '16 Maret 2020', 'PL0004', 'WK0003'),
('MY0005', '17 Maret 2020', 'PL0005', 'WK0005'),
('MY0006', '17 Maret 2020', 'PL0006', 'WK0004'),
('MY0007', '17 Maret 2020', 'PL0007', 'WK0001'),
('MY0008', '18 Maret 2020', 'PL0008', 'WK0003'),
('MY0009', '18 Maret 2020', 'PL0009', 'WK0004'),
('MY0010', '19 Maret 2020', 'PL0010', 'WK0003');

-- --------------------------------------------------------

--
-- Table structure for table `pelanggan`
--

CREATE TABLE `pelanggan` (
  `id_pelanggan` varchar(10) NOT NULL,
  `Nama_lengkap` varchar(50) NOT NULL,
  `Alamat` text NOT NULL,
  `No_ktp` varchar(50) NOT NULL,
  `No_hp` varchar(15) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

--
-- Dumping data for table `pelanggan`
--

INSERT INTO `pelanggan` (`id_pelanggan`, `Nama_lengkap`, `Alamat`, `No_ktp`, `No_hp`) VALUES
('PL0001', 'Muharrys', 'Desa Canden,Kecamatan Jetis,Kabupaten Bantul, Ypgyakarta', '7376620607921006', '089627858976'),
('PL0002', 'Rian Putra Saji', 'Desa Panggungharjo,Kecamatan Sewon, Kabupaten Bantul, Yogyakarta', '1627358439275835', '082163789547'),
('PL0003', 'Puja Anwar', 'Desa Bangunjiwo, Kecamatan Kasihan, Kabupaten Bantul, Yogyakarta', '2746890267836749', '082189468263'),
('PL0004', 'Darul Hanafi', 'Desa Sidomulyo,Kecamatan Bambanglipuro, Kabupaten Bantul,Yogyakarta', '7946837290184729', '085702781925'),
('PL0005', 'Jupri Istomo', 'Desa Wirokerten, Kecamatan Banguntapan, Kabupaten Bantul, Yogyakarta', '5673896729067356', '085782678903'),
('PL0006', 'Ronald Ramadhan', 'Desa Mulyodadi, Kecamatan Bambanglipuro, Kabupaten Bantul, Yogyakarta', '5637890263784986', '089625367281'),
('PL0007', 'Lesmana', 'Desa Timbulharjo, Kecamatan Sewon, Kabupaten Bantul, Yogyakarta', '8367426837126748', '082174683792'),
('PL0008', 'Chandra Aksa', 'Desa Tirtonirmolo, Kecamatan Kasihan, Kabupaten Bantul, Yogyakarta', '6364528167493326', '085724356422'),
('PL0009', 'Ripo Ardyan', 'Desa Wonokromo, Kecamatan Pleret, Kabupaten Bantul , Yogyakarta', '6357285391426783', '082175638296'),
('PL0010', 'Muhammad Gibran', 'Desa Panjangrejo, Kecamatan Pundong, Kabupaten Bantul, Yogyakarta', '5367256392016482', '081274528364');

-- --------------------------------------------------------

--
-- Table structure for table `waktu_main`
--

CREATE TABLE `waktu_main` (
  `id_waktu_main` varchar(10) NOT NULL,
  `Jam_main` varchar(50) NOT NULL,
  `Tarif` varchar(50) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

--
-- Dumping data for table `waktu_main`
--

INSERT INTO `waktu_main` (`id_waktu_main`, `Jam_main`, `Tarif`) VALUES
('WK0001', '08:00-14:00', '65.000'),
('WK0002', '14:00-15:00', '75.000'),
('WK0003', '15:00-18:00', '85.000'),
('WK0004', '18:00-19:00', '100.000'),
('WK0005', '19:00-24:00', '110.000');

--
-- Indexes for dumped tables
--

--
-- Indexes for table `menyewa`
--
ALTER TABLE `menyewa`
  ADD PRIMARY KEY (`id_menyewa`),
  ADD UNIQUE KEY `id_pelanggan` (`id_pelanggan`,`id_waktu_main`),
  ADD KEY `id_waktu_main` (`id_waktu_main`);

--
-- Indexes for table `pelanggan`
--
ALTER TABLE `pelanggan`
  ADD PRIMARY KEY (`id_pelanggan`);

--
-- Indexes for table `waktu_main`
--
ALTER TABLE `waktu_main`
  ADD PRIMARY KEY (`id_waktu_main`);

--
-- Constraints for dumped tables
--

--
-- Constraints for table `menyewa`
--
ALTER TABLE `menyewa`
  ADD CONSTRAINT `menyewa_ibfk_1` FOREIGN KEY (`id_pelanggan`) REFERENCES `pelanggan` (`id_pelanggan`),
  ADD CONSTRAINT `menyewa_ibfk_2` FOREIGN KEY (`id_waktu_main`) REFERENCES `waktu_main` (`id_waktu_main`);
COMMIT;

/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;

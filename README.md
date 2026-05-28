# Pertemuan 9 - Algoritma Genetika (Masalah Knapsack)

**Nama:** Nayla Octavia Ramadhani
**NIM:** H1D024115

## Ringkasan

Proyek ini menerapkan **Algoritma Genetika (GA)** untuk menyelesaikan **Masalah Knapsack**. Tujuan utamanya adalah memilih kombinasi barang yang memberikan **nilai total maksimum** tanpa melampaui **kapasitas ransel**.

## Data Barang

| No  | Nama     | Nilai | Berat |
| --- | -------- | ----- | ----- |
| 1   | Barang 1 | 60    | 10    |
| 2   | Barang 2 | 100   | 20    |
| 3   | Barang 3 | 120   | 30    |
| 4   | Barang 4 | 90    | 25    |
| 5   | Barang 5 | 69    | 11    |
| 6   | Barang 6 | 70    | 9     |
| 7   | Barang 7 | 80    | 15    |
| 8   | Barang 8 | 90    | 10    |
| 9   | Barang 9 | 25    | 3     |

**Kapasitas Ransel:** 50

## Parameter GA

| Parameter        | Nilai |
| ---------------- | ----- |
| Jumlah Generasi  | 50    |
| Ukuran Populasi  | 20    |
| Prob. Crossover  | 0.5   |
| Prob. Mutasi     | 0.1   |
| Kapasitas Ransel | 50    |

## Deskripsi Modul

### `InisiasiPopulasi.py`

Membangkitkan populasi awal secara acak. Setiap individu direpresentasikan sebagai kromosom biner (daftar 0 dan 1):

- `1` berarti barang dipilih
- `0` berarti barang tidak dipilih

### `EvaluasiFitness.py`

Menghitung fitness tiap individu berdasarkan jumlah nilai barang yang dipilih. Jika total berat melebihi kapasitas, individu itu mendapatkan fitness **0** sebagai penalti.

### `selection.py`

Menyediakan dua metode pemilihan parent:

- **Roulette Wheel Selection** — peluang dipilih proporsional terhadap fitness.
- **Tournament Selection** — memilih terbaik dari beberapa kandidat acak.

### `crossover.py`

Berisi beberapa teknik crossover:

- **One-Point** — potong satu titik lalu tukar segmen.
- **Two-Point** — potong dua titik lalu tukar segmen tengah.
- **Uniform** — gunakan mask acak untuk menentukan gen yang ditukar.

### `mutation.py`

Berisi metode mutasi berikut:

- **Swap Mutation** — tukar posisi dua gen secara acak.
- **Inversion Mutation** — balik urutan potongan gen.
- **Uniform Mutation (Bit-Flip)** — balikkan bit (0→1 atau 1→0) berdasarkan probabilitas.

### `main.py`

File utama yang mengkoordinasikan proses evolusi:

1. Inisialisasi populasi
2. Evaluasi fitness
3. Seleksi parent (mis. Roulette Wheel)
4. Crossover (mis. One-Point)
5. Mutasi (mis. Swap)
6. Ulangi sampai jumlah generasi terpenuhi
7. Tampilkan grafik perkembangan dan solusi terbaik

## Cara Menjalankan

```bash
python main.py
```

Setiap modul juga dapat dijalankan terpisah untuk tujuan pengujian:

```bash
python InisiasiPopulasi.py
python EvaluasiFitness.py
python selection.py
python crossover.py
python mutation.py
```

## Output

### Grafik Perkembangan Fitness

![Grafik Perkembangan Fitness](output/fitness_history.png)

Keterangan grafik:

- 🔵 Fitness tertinggi tiap generasi
- 🔴 Fitness rata-rata tiap generasi
- 🟡 Fitness terendah tiap generasi
- ⚫ Sebaran fitness seluruh individu

### Contoh Hasil

```
Grafik disimpan sebagai output/fitness_history.png
Nilai Fitness Terbaik: 329
Total Bobot: 50
Barang Terpilih:
- Barang 2
- Barang 5
- Barang 6
- Barang 8
```

## Dependensi

- Python 3.x
- matplotlib — untuk visualisasi
- numpy — untuk perhitungan numerik

Instalasi dependensi:

```bash
pip install matplotlib numpy
```

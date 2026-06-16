# Laporan Praktikum Jaringan Komputer – IEEE 802.11 (WiFi)

| Item | Keterangan |
|------|-----------|
| Nama | Laura Chyndearni Saragih |
| NIM | 103072400049 |
| Kelas | IF-04-01 |

---

## Tujuan Praktikum

1. Mengamati Beacon Frame pada jaringan IEEE 802.11.
2. Menganalisis proses Association Request.
3. Menganalisis proses Association Response.
4. Mengamati Data Frame pada jaringan WiFi.
5. Memahami proses komunikasi antara Station dan Access Point.

---

## Langkah Praktikum

1. Membuka file capture `Wireshark_802_11.pcap` menggunakan Wireshark.
2. Mengamati Beacon Frame menggunakan filter:

   ```
   wlan.fc.type_subtype == 0x08
   ```

3. Mengamati Association Request menggunakan filter:

   ```
   wlan.fc.type_subtype == 0
   ```

4. Mengamati Association Response menggunakan filter:

   ```
   wlan.fc.type_subtype == 1
   ```

5. Mengamati Data Frame menggunakan filter:

   ```
   wlan.fc.type_subtype == 0x20
   ```

6. Menganalisis informasi yang ditampilkan pada setiap frame IEEE 802.11.

---

## 1. Analisis Beacon Frame

Filter yang digunakan:

```text
wlan.fc.type_subtype == 0x08
```

Beacon Frame merupakan frame yang dikirim secara periodik oleh Access Point untuk mengumumkan keberadaan jaringan WiFi kepada perangkat di sekitarnya.

Berikut tampilan Beacon Frame:

(assets/wifi_beacon_frame.png)

![Beacon Frame](assets/wifi_beacon_frame.png)

### Analisis

- Beacon Frame dikirim oleh Access Point.
- Beacon berisi informasi SSID jaringan.
- Beacon digunakan perangkat klien untuk menemukan jaringan WiFi yang tersedia.
- Beacon dikirim secara berkala selama Access Point aktif.

---

## 2. Analisis Association Request

Filter yang digunakan:

```text
wlan.fc.type_subtype == 0
```

Association Request dikirim oleh perangkat klien kepada Access Point untuk meminta bergabung ke jaringan WiFi.

Berikut tampilan Association Request:

(assets/wifi_association_request.png)

![Association Request](assets/wifi_association_request.png)

### Analisis

- Association Request berasal dari perangkat klien.
- Frame ini berisi kemampuan perangkat yang akan bergabung ke jaringan.
- Klien mengirimkan permintaan asosiasi kepada Access Point.
- Proses ini dilakukan sebelum komunikasi data berlangsung.

---

## 3. Analisis Association Response

Filter yang digunakan:

```text
wlan.fc.type_subtype == 1
```

Association Response merupakan balasan dari Access Point terhadap Association Request yang dikirimkan oleh klien.

Berikut tampilan Association Response:

(assets/wifi_association_response.png)

![Association Response](assets/wifi_association_response.png)

### Analisis

- Association Response dikirim oleh Access Point.
- Frame ini menunjukkan hasil dari permintaan asosiasi klien.
- Jika berhasil, perangkat dapat mulai berkomunikasi pada jaringan.
- Association Response menjadi tanda bahwa klien telah diterima oleh Access Point.

---

## 4. Analisis Data Frame

Filter yang digunakan:

```text
wlan.fc.type_subtype == 0x20
```

Data Frame digunakan untuk membawa data aktual antara perangkat klien dan Access Point.

Berikut tampilan Data Frame:

(assets/wifi_data_frame.png)

![Data Frame](assets/wifi_data_frame.png)

### Analisis

Hasil capture menunjukkan:

```text
Type = Data frame (2)
Subtype = Data (0)
```

Interpretasi:

- Frame termasuk kategori Data Frame.
- Data Frame digunakan untuk membawa payload data pengguna.
- Setelah proses asosiasi berhasil, komunikasi berlangsung menggunakan Data Frame.
- Frame ini merupakan frame utama yang digunakan selama koneksi WiFi aktif.

---

## Kesimpulan

Pada praktikum ini dilakukan analisis terhadap beberapa jenis frame IEEE 802.11 menggunakan Wireshark.

Hasil menunjukkan bahwa:

- Beacon Frame digunakan untuk mengumumkan keberadaan jaringan WiFi.
- Association Request digunakan klien untuk meminta bergabung ke jaringan.
- Association Response digunakan Access Point untuk memberikan konfirmasi asosiasi.
- Data Frame digunakan untuk mengirimkan data aktual selama komunikasi berlangsung.
- IEEE 802.11 menggunakan berbagai jenis frame untuk mengatur komunikasi antara perangkat klien dan Access Point.

Praktikum berhasil dijalankan dan seluruh jenis frame dapat diamati menggunakan Wireshark.

Baik, berikut ini adalah contoh program ESP32 menggunakan bahasa pemrograman Arduino IDE untuk melakukan scan jaringan WiFi dan menampilkan hasilnya di Serial Monitor:

#include <WiFi.h>

void setup() {
  Serial.begin(115200);
  WiFi.mode(WIFI_STA);
}

void loop() {
  Serial.println("Scanning WiFi...");
  int networkCount = WiFi.scanNetworks();
  Serial.println("WiFi Scan Complete.");
  if (networkCount == 0) {
    Serial.println("No networks found.");
  } else {
    Serial.print(networkCount);
    Serial.println(" networks found:");
    for (int i = 0; i < networkCount; ++i) {
      Serial.print(WiFi.SSID(i));
      Serial.print(" (");
      Serial.print(WiFi.RSSI(i));
      Serial.println(")");
    }
  }
  delay(5000);
}
Penjelasan singkat mengenai kode di atas:

Pada blok setup(), kita mengatur baud rate Serial Monitor dan mode WiFi sebagai STA (station).
Pada blok loop(), kita memulai scanning WiFi dengan memanggil fungsi WiFi.scanNetworks().
Kemudian kita menampilkan jumlah jaringan yang ditemukan dan daftar SSID jaringan beserta nilai RSSI-nya.
Akhirnya, kita memberi jeda 5 detik sebelum memulai scanning kembali.
Pastikan Anda sudah memilih board ESP32 di menu Tools -> Board pada Arduino IDE dan sudah menghubungkan ESP32 ke komputer melalui kabel USB sebelum mencoba kode di atas.

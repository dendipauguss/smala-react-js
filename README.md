/* ------------------------------------------------------------
README — Cara Pakai Cepat
---------------------------------------------------------------
1) Buat proyek React (contoh Vite):
npm create vite@latest fall-dashboard -- --template react
cd fall-dashboard


2) Install dependency yang dipakai komponen ini:
npm i recharts framer-motion lucide-react
# (Opsional, styling Tailwind)
npm i -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
# lalu konfigurasi tailwind sesuai dokumentasi (content di index.html + src/**)


3) Salin file ini sebagai src/FallDetectionDashboard.jsx lalu gunakan di App.jsx:
import React from 'react'
import FallDetectionDashboard from './FallDetectionDashboard'
export default function App(){
return <FallDetectionDashboard />
}


4) Jalankan:
npm run dev


5) Ganti DEFAULT_WS_URL di atas dengan alamat WebSocket ESP32 kamu, contoh:
ws://192.168.1.123:81


---------------------------------------------------------------
FORMAT PESAN DARI ESP32
---------------------------------------------------------------
Harap kirim JSON seperti:
{ "ax": 0.02, "ay": -0.98, "az": 0.05, "fall": false, "ts": 1710000000000 }
- ax, ay, az : percepatan sumbu (g) atau nilai terukur lain
- fall : boolean deteksi jatuh dari firmware (true/false)
- ts : timestamp epoch milliseconds (optional, jika kosong akan diisi browser)
Komponen juga menerima fallback CSV: ax,ay,az,fall,ts


---------------------------------------------------------------
Contoh Firmware ESP32 (Arduino) — WebSocket JSON
---------------------------------------------------------------
// Library yang dibutuhkan:
// - arduinoWebSockets (WebSocketsServer)
// - WiFi / WiFi.h
// - Sensor IMU (contoh MPU6050 / MPU6886 / ADXL345 sesuai modul)
// Catatan: endpoint WS pada dashboard default: ws://<ip>:81


#include <WiFi.h>
#include <WebSocketsServer.h>


const char* SSID = "YOUR_SSID";
const char* PASS = "YOUR_PASSWORD";
WebSocketsServer webSocket = WebSocketsServer(81);


// TODO: ganti dengan pembacaan sensor asli
float readAx(){ return 0.02; }
float readAy(){ return -0.98; }
float readAz(){ return 0.05; }


*/
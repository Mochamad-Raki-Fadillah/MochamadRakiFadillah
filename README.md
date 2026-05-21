# Enterprise Network Architecture & Secure Wireless LAN Implementation

## 📌 Project Overview
Proyek ini merupakan implementasi infrastruktur jaringan terintegrasi untuk skala lokal (LAN & WLAN). Fokus utama dari proyek ini adalah membangun jaringan yang **tersegmentasi dengan rapi antar divisi (menggunakan VLAN)**, memastikan interkoneksi antar segmen berjalan lancar via **Inter-VLAN Routing**, serta menyediakan akses nirkabel (*Wireless LAN*) yang aman menggunakan autentikasi enkripsi kunci berbasis SSID dan WPA2-PSK.

*Proyek ini diadaptasi dari tugas praktikum Ujian Kompetensi Keahlian (UKK) Teknik Komputer dan Jaringan.*

---

## 🛠️ Tech Stack & Key Features
- **Switching & Segmentation:** VLAN (Virtual LAN) & Trunking untuk efisiensi jalur kabel.
- **Routing:** Inter-VLAN Routing pada Router sebagai pusat kendali trafik antar divisi.
- **Network Services:** DHCP Server Deployment (alokasi IP otomatis di setiap segmen VLAN & Wireless).
- **Wireless Security:** WPA2-PSK Encryption untuk mengamankan akses Wi-Fi menggunakan Network Security Key (Password).
- **Hardware/Simulators:** MikroTik RouterOS, Access Point, Cisco Packet Tracer.

---

## 🗺️ Network Topology
Berikut adalah arsitektur topologi jaringan yang dirancang dan diimplementasikan:

![Network Topology](Topologi Jaringan)

### Network Segmentation & Wireless Addressing Plan
| Division / SSID | VLAN ID | IP Network | Gateway | Security / Authentication |
| :--- | :--- | :--- | :--- | :--- |
| **VLAN_Admin**  | VLAN 10 | 192.168.10.0/29 | 192.168.10.1 | Wired / Ringkas |
| **VLAN_Dept A** | VLAN 20 | 192.168.20.0/27 | 192.168.20.1 | Wired / Ringkas |
| **VLAN_Dept B** | VLAN 30 | 192.168.30.0/26 | 192.168.30.1 | Wired / Ringkas |
| **Hotspot**     |     -   | 192.168.40.0/24 | 192.168.40.1 | WPA2-PSK (Password Protected) |

---

## 🚀 Key Implementation Details

### 1. VLAN & Trunking Deployment
Memisahkan jaringan fisik menjadi beberapa jaringan logis (VLAN) pada Cisco Switch. Jalur dari Switch ke Router dikonfigurasi sebagai *Trunk Link* untuk melewatkan beberapa VLAN ID (VLAN 10, 20, dan 30) hanya melalui satu kabel fisik, guna menghemat port hardware dan merapikan manajemen kabel.

### 2. Inter-VLAN Routing & Core Services
Mengonfigurasi Router sebagai *Gateway* utama untuk seluruh VLAN (metode *Router-on-a-Stick* atau integrasi *interface* VLAN). Router juga bertindak sebagai DHCP Server terpisah untuk masing-masing divisi, memastikan setiap perangkat mendapatkan IP yang sesuai dengan segmennya secara otomatis begitu terhubung.

### 3. Secure Wireless LAN (WLAN) Configuration
Mengonfigurasi Access Point nirkabel dengan memetakan SSID khusus ke dalam segmen VLAN 30. Keamanan jaringan nirkabel dioptimalkan menggunakan enkripsi **WPA2-PSK (Pre-Shared Key)**, sehingga hanya pengguna yang memiliki *security key* (kata sandi) valid yang dapat berasosiasi dengan jaringan dan mendapatkan hak akses internet.

---

## 📊 Verification & Testing (Proof of Work)
Kondisi operasional jaringan yang berhasil diverifikasi:
1. **Verifikasi VLAN & DHCP:** Perangkat klien di setiap port switch (VLAN 10 & 20) berhasil mendapatkan IP Address otomatis dari *pool* segmen masing-masing.
2. **Pengujian Wireless LAN:** Perangkat *smartphone* atau laptop berhasil mendeteksi SSID, melakukan jabat tangan keamanan (*security handshake*) menggunakan password WPA2, dan mendapatkan alokasi IP dari VLAN 30.
3. **Pengujian Routing:** Klien nirkabel maupun kabel dapat saling melakukan `ping` ke gateway dan terhubung ke internet secara stabil melalui konfigurasi NAT di Router.

---

## 📁 Repository Structure
- `/topology` : File desain arsitektur jaringan (.pkt / .drawio).
- `/docs` : Dokumentasi foto perangkat keras dan *screenshot* hasil pengujian.

---
💡 **Contact & Professional Network:**
- **LinkedIn:** [Nama LinkedIn Kamu](https://linkedin.com/in/username-kamu)
- **Email:** fadillahraki@gmail.com

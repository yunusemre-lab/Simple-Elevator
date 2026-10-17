# 🛗 Simple Elevator Control System with PLC & HMI

Siemens TIA Portal ortamında PLC (Ladder Diagram) ve SIMATIC HMI kullanılarak tasarlanmış, çok katlı asansör kontrolü, kabin/kat kapı mekanizması ve kat durumu takip algoritmalarını içeren endüstriyel otomasyon projesidir.

---

## 📌 Proje Özeti
Bu proje; kat çağrı butonları, kabin içi kat seçimleri, sınır switch’ler (limit switch), kapı açma/kapama zamanlayıcıları ve kat konum takibini modüler bir yapıda yöneten 3 katlı bir asansör otomasyon sistemidir.

### 🎥 HMI & Sistem Simülasyonu (PLC-Sim)

<img width="800" alt="Asansör HMI Simülasyonu" src="https://github.com/user-attachments/assets/d6243aae-b887-4a94-a1da-9ccdfa118338" />

---

## ⚙️ Özellikler ve Çalışma Mantığı

* **Kat Çağrı ve Kabin İçi Seçim Yönetimi:** Katlarda bulunan yukarı/aşağı çağrı butonları ve kabin içi kat butonları mühürleme (latch) mantığı ile hafızaya alınır.
* **Akıllı Yön ve Hareket Kontrolü:** Asansörün anlık bulunduğu kat ile hedef kat karşılaştırılarak yukarımı yoksa aşağı mı hareket edeceği belirlenir.
* **Kapı Otomasyonu (FB4 - Kapı Durum):** Asansör hedeflenen kata ulaştığında durur, otomatik olarak kapıyı açar, belirlenen süre kadar bekler ve kapıyı güvenli bir şekilde kapatır.
* **Kat Konum Takibi (FB3 - Kat Durum):** Kat sensörleri ve sınır anahtarlarından gelen veriler doğrultusunda asansörün anlık bulunduğu kat bilgisi dinamik olarak hesaplanır ve HMI paneline aktarılır.
* **Emniyet Kilitleri:** Hareket esnasında kapıların açılmasını engelleyen güvenlik kilitleri ve limit switch kontrolleri entegre edilmiştir.

---

## 🛠️ PLC Mimari ve Kod Yapısı

### 1. Ana Kontrol Blokları (Main OB1)

**Network 1 : Kat Çağrılarının Hafızaya Alınması ve Mühürleme Mantığı**
![Main Network 1](https://github.com/user-attachments/assets/8a3e9d32-f77e-4495-8c5d-0456f18a11c5)
![Main Network 2](https://github.com/user-attachments/assets/2ad16d1d-dd84-4ef6-8fcd-87d3b797b289)
![Main Network 3](https://github.com/user-attachments/assets/a630ab8b-1bd0-48d6-a544-5b248641460a)
![Main Network 4](https://github.com/user-attachments/assets/302a5955-e52f-45e8-9b5e-050d265ab746)

Yukarı / Aşağı Motor Hareket Koşulları ve Kilitler**
![Main Network 5](https://github.com/user-attachments/assets/9167c6be-b983-405a-b22e-c1cbb5aaea6d)
![Main Network 6](https://github.com/user-attachments/assets/85cd229a-3822-4cec-8b7a-7998fc01eb16)
![Main Network 7](https://github.com/user-attachments/assets/c12756bb-24df-4b30-b62c-9ebcb5289e7f)
![Main Network 8](https://github.com/user-attachments/assets/ae7b1c5c-f5e9-449d-89f0-02dced07d081)

 Durdurma, Sınır Anahtarları ve Emniyet Devreleri**
![Main Network 9](https://github.com/user-attachments/assets/a5bf1191-0bed-4ad5-879a-4efb9bb63e60)
![Main Network 10](https://github.com/user-attachments/assets/bb9ab23c-4786-4ef9-ba97-9b90a186bd5c)
![Main Network 11](https://github.com/user-attachments/assets/506a34ea-e783-4fc5-9eee-734938c454cc)
![Main Network 12](https://github.com/user-attachments/assets/8f2a874d-48ae-47e0-9297-9dde15b8c16f)

Fonksiyon Blok Çağrıları (FB3 & FB4 Entegrasyonu)**
![Main Network 13](https://github.com/user-attachments/assets/b1c0df9c-1b2c-46cf-baa7-1033f477b6f0)
![Main Network 14](https://github.com/user-attachments/assets/5705baad-c20f-430d-bc12-3f65e464ffd1)
![Main Network 15](https://github.com/user-attachments/assets/55e4f1b8-d14f-4647-b343-c29a8a4699a2)
![Main Network 16](https://github.com/user-attachments/assets/eaa342aa-f9cf-455d-800c-0787b6ec6538)

---

### 2. Modüler Fonksiyon Blokları (FB)

#### 🚪 FB4: Kapı Durum ve Zamanlayıcı Kontrol Bloğu
Asansör kata ulaştığında kapının otomatik açılması, bekleme süresi (`TON` Timer) ve kapanma sürecini yönetir.

![FB4 Network 1](https://github.com/user-attachments/assets/806b9e98-760e-4f53-b9fc-26c9d7fd2334)
![FB4 Network 2](https://github.com/user-attachments/assets/613f000c-d0dc-43b1-a0b7-3e445652549d)

---

#### 🏢 FB3: Kat Durum ve Konum Tespit Bloğu
Kat sensörlerinden gelen sinyalleri işleyerek anlık kat bilgisini günceller ve HMI ekranında gösterilecek veri değerini hesaplar.

![FB3 Network 1](https://github.com/user-attachments/assets/96813aa2-2b61-4f20-88a7-cb7643622c16)

---

## 🛠️ Kullanılan Teknolojiler

* **Yazılım:** Siemens TIA Portal
* **Programlama Dili:** Ladder Diagram (LAD)
* **Arayüz (HMI):** SIMATIC HMI Touch Panel Simulation
* **Simülasyon:** S7-PLCSIM

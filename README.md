# 🚀 İstanBuilders: Yapay Zeka Destekli Akıllı Başvuru Takip Sistemi

Bu proje, **İBB Tech Istanbul Yapay Zeka Hackathonu (Aralık 2025)** kapsamında **IstanBuilders** ekibi tarafından 32 saatlik kesintisiz bir maraton sürecinde geliştirilmiştir. Projemiz, "Akıllı Şehir" teması altında, var olan belediye hizmetlerinin yapay zeka ile iyileştirilmesi vizyonuna odaklanmıştır.

## 📋 Problem Tanımı & Çözüm Vizyonu

İstanbul Büyükşehir Belediyesi'ne gelen vatandaş şikayetlerinin manuel olarak yönlendirilmesi; zaman alıcı, hataya açık ve maliyetli bir süreçtir. Doğru kategorizasyon, belediye hizmet verimliliği için kritiktir.

**IstanBuilders olarak çözümümüz:**

* 
**Otomatik Sınıflandırma:** Gelen serbest metin şikayetlerini semantik analiz ile otomatik olarak 12 farklı kategoriye ayırır.


* 
**Anlık Operasyonel Takip:** Şikayetler anlık olarak ilgili birimin PowerBI tabanlı dashboard'una düşer ve harita üzerinden lokasyon bazlı takip edilebilir.


* **Genişletilebilirlik:** Sistem, sesli şikayetler (Alo 153) veya görsel veriler üzerinde de çalışabilecek esnekliktedir.

---

## 🛠 Teknik Mimari

Projemizin en büyük farkı, yüksek maliyetli kapalı kaynaklı LLM'ler (ChatGPT vb.) yerine **tamamen yerel ve masrafsız** bir NLP mimarisi kullanmasıdır.

* 
**Model:** `emrecan/bert-base-turkish-cased-mean-nli-stsb-tr` (TurkishBERT).


* 
**Vektör Veritabanı:** PostgreSQL üzerinde **pgvector** eklentisi ile 768 boyutlu vektör benzerlik araması (cosine similarity).


* 
**Entegrasyon:** Dockerized mimari ve anlık veri aktarımı.



### 📊 Sınıflandırılan Kategoriler

Sistem, şikayetleri aşağıdaki ana departmanlara otomatik olarak yönlendirir:

1. Su & Kanalizasyon
2. Atık Yönetimi
3. Temizlik
4. Ulaşım & Trafik
5. Yol & Altyapı
6. Yeşil Alan & Bahçe
7. Aydınlatma
8. Sosyal Yardım
9. Fatura & Ödeme
10. Başvuru & Ruhsat
11. Şikayet Takip
12. Dijital Sistemler

---

## 🚀 Kurulum ve Çalıştırma

### 1. Veritabanını Başlatın (Docker)

PostgreSQL 16 ve pgvector eklentisini içeren container'ı ayağa kaldırın:

```bash
docker-compose up -d

```

### 2. Bağımlılıkları Yükleyin

```bash
pip install sentence-transformers transformers scikit-learn pandas matplotlib seaborn numpy psycopg2-binary pgvector

```

### 3. Notebook'u Çalıştırın

`istanbuilders_final.ipynb` dosyasını açarak hücreleri sırasıyla takip edin. Sistem otomatik olarak:

* BERT modelini yükler,
* Şikayet taslaklarını vektörize eder,
* Verileri PostgreSQL'e aktarır ve sınıflandırma analizini gerçekleştirir.

---

## 🏗 Veritabanı Şeması

* **`departments`**: Kategori tanımları ve açıklamaları.
* **`complaints`**: Ham metin, tahmin edilen kategori, güven skoru ve zaman damgası.
* **`complaint_embeddings`**: Hızlı semantik arama için `vector(768)` tipinde saklanan embeddingler.

---

## 👥 Ekibimiz: IstanBuilders

* **Rana İşlek**
* **Yiğit**
* **Zeynep**

> "Dereceye girmemiş olsak da, 32 saat boyunca çalışan bir ürün ortaya koymak ve gerçek bir veri setini uçtan uca işlemek bizim için paha biçilemez bir deneyimdi." 
> 
> 

---

**İBB Tech Istanbul 2025** 

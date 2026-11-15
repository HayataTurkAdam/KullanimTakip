# Kullanım Takip v1.2 (Android, Java, bağımlılıksız)

İki bölüm: **Analiz** (saatlik/günlük/haftalık kullanım) ve **Limit** (uygulama başına günlük süre sınırı).
İnternet izni YOK. Sistem ayarlarına dokunmaz, root gerektirmez.

## APK alma
GitHub'a yükle → Actions > apk > Artifacts (`.github/workflows/apk.yml` ile).

## İlk kurulum
1. Açılışta "Kullanım erişimi" iznini ver (Analiz için).
2. Limit sekmesi → ebeveyn PIN'i belirle.
3. "Erişilebilirlik ayarlarını aç" → "Kullanım Takip Limit" hizmetini aç.
   Android 13+ ve APK dışarıdan kurulduysa seçenek gri olabilir:
   Ayarlar > Uygulamalar > Kullanım Takip > ⋮ > "Kısıtlı ayara izin ver", sonra tekrar dene.
4. "+ Ekle" → uygulamayı seç → günlük dakika gir.

## Nasıl çalışır
Limitli uygulama öne gelince tek bir sayaç kurulur (yoklama yok). Bitmesine 5 dk kala uyarı verir,
süre dolunca Ana Ekran'a döndürür ve engel ekranı gösterir. Limit gece yarısı sıfırlanır.

## v1.2 düzeltmesi (limit aşılınca engellememe)
- Pencere olayı UsageStats kaydından önce gelince ön plan yanlış (Ana Ekran) görünüyordu ve sayaç hiç kurulmuyordu;
  artık olay paketi ipucu sayılır ve ön plan doğrulanana kadar yeniden denenir.
- Ekran açıkken 15 sn'lik güvenlik kontrolü: oyun zaten açıkken limit eklense / olay kaçsa bile yakalanır.
- Hizmet bağlanınca ve limit kaydedilince anında kontrol.
- Limit sekmesinde canlı durum satırı: hizmet gerçekten çalışıyor mu görünür.

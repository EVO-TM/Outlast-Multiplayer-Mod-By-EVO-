# Kurulum ve birlikte oynama

## İndir ve kur

1. [0.2.1 yayınını](https://github.com/EVO-TM/evo-outlast/releases/tag/v0.2.1) aç.
2. `EVO-Outlast-Coop-Setup-0.2.1.exe` dosyasını indir. `SHA256SUMS.txt` dosyası aynı yayında bulunur.
3. Outlast'ı kapat. Kurulumu çalıştır ve Outlast ana klasörünü seç; klasörün içinde `Binaries` ve `OLGame` olmalı.
4. **KUR / GÜNCELLE** düğmesine bas. Oyun sürümü uyuşmuyorsa kurulum durur.
5. Outlast'ı kendi normal başlatıcısından aç. Ana menüden **Co-op** seçeneğine gir.

Kurulum kendi destek dosyalarını `%LOCALAPPDATA%\EvoOutlast` altına, mod DLL'sini oyunun `Binaries\Win64` klasörüne yerleştirir. Başka bir moda ait `dinput8.dll` üzerine yazılmaz. Bu EXE bir Authenticode sertifikasıyla imzalanmış değildir; dosya bütünlüğü yayın SHA-256 değeriyle karşılaştırılabilir.

## Host

1. Herkes Radmin VPN'de aynı özel ağa katılsın.
2. Oyundaki Co-op panelinde adını ve en az 8 karakterli oda kodunu gir.
3. **Oda aç ve başlat** düğmesine bas. Yeni co-op oyunu başlangıç kontrol noktasından açılır.
4. Radmin IPv4 adresini, oda kodunu ve portunu yalnızca birlikte oynayacağın kişilere ver.

## Katılımcı

1. Aynı mod sürümünü kur ve hostla aynı Radmin ağına katıl.
2. Co-op paneline hostun **Radmin IPv4 adresini** yaz; `127.0.0.1` başka bilgisayara bağlanmaz.
3. Hostla aynı oda kodunu ve portunu kullan. Varsayılan port **UDP 27851**.
4. **Katıl ve başlat** düğmesine bas. Bağlantı kurulunca hostun kontrol noktası yüklenir.

Bağlantı kurulamıyorsa önce Radmin ağı, adres, oda kodu ve portu karşılaştır. Güvenlik duvarında yalnızca oyunun gerekli bağlantısına uygun ağ kapsamında izin ver; güvenlik duvarını bütünüyle kapatma. Kurulum ağ/güvenlik duvarı ayarlarını değiştirmez.

## Kayıt ve devam

Oyun sırasında **F9 → Co-op kaydet**. Kayıtlar `%LOCALAPPDATA%\EvoOutlast\CoopSaves` klasöründedir. Kontrol noktası, oda ayarları ve desteklenen ortak olaylar tutulur; her karakter/NPC konumunu ve bütün dünya değişkenlerini saklayan anlık kayıt değildir.

Devam ederken host önce kendi kaydını açsın; diğer oyuncular aynı odaya bağlansın. **Continue** veya **Co-op kaydından devam et** kullanılabilir. Kaydet → menü → devam et akışında donma bildirilmiştir; bu akışın son düzeltmesi tam olarak yeniden doğrulanmadı. Denemeden önce `CoopSaves` klasörünü yedekle.

## Güncelle ve kaldır

Güncelleme için oyunu kapatıp yeni kurulum dosyasını çalıştır. Kendi eski DLL'si değiştiriliyorsa kopyası `%LOCALAPPDATA%\EvoOutlast\Backups` klasöründe saklanır. Oda ayarları ve co-op kayıtları korunur.

Kaldırmak için oyun kapalıyken `%LOCALAPPDATA%\EvoOutlast\EvoOutlast.exe` başlatıcısını açıp **Modu kaldır** düğmesini kullan. Co-op kayıtları silinmez.

## Dosya bütünlüğü

PowerShell'de indirdiğin dosyayı kontrol etmek için:

```powershell
Get-FileHash .\EVO-Outlast-Coop-Setup-0.2.1.exe -Algorithm SHA256
```

Sonucu aynı yayındaki `SHA256SUMS.txt` ile karşılaştır. Sağlama toplamı dijital yayıncı imzası değildir.

## Steam uyumluluğu

Proje sahibi Steam sürümünde de çalıştığını bildirdi. Denenen Steam sürümü ve EXE özeti henüz kaydedilmedi. Kurucunun tek SHA-256 kontrolü değişmedi; farklı bir Steam EXE dosyası reddedilebilir. Ayrıntılar için [İngilizce uyumluluk bölümüne](INSTALL.en.md#compatibility) bak. İngilizce kurulum aynı yayında `EVO-Outlast-Coop-Setup-0.2.1-English.exe` adıyla bulunur.

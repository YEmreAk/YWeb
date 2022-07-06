---
description: Web üzerinde çalışanlar için fayda sağlayacak notlar
---

# 👨‍💼 Web Sitesi Yönetimi

## 🌎 Sitenizi Kendi Alan Adınıza Bağlama (Domain) <a href="#sitenizi-kendi-alan-adiniza-baglama-domain" id="sitenizi-kendi-alan-adiniza-baglama-domain"></a>

CNAME kayıtları ile halledilen bir işlemdir‌

* Domaininiz bağlamak istediğiniz siteye girin ve oradaki yönergeleri takip ederek, hosting (sunucu) urli alın.
* Domaini satın aldığınız siteye giriş yapın ve **DNS Hizmeti ve Yönetimi** alanına girin
* **CNAME Kayıtları** altında:
  * `Alt alan adı` olarak belirtilen yere _subdomain_''i yazın (örn: wiki.yemreak.com)
  * `Sunucu` alanına size verilen bağlantıyı kopyalayın. (örn: hosting.github.com)

{% content-ref url="Natro Hosting.md" %}
[Natro Hosting.md](<Natro Hosting.md>)
{% endcontent-ref %}

## 🔍 Arama Motoru Yönetimi <a href="#arama-motoru-yoenetimi" id="arama-motoru-yoenetimi"></a>

* ​[Google Search Console](https://search.google.com/search-console/welcome?utm\_source=about-page)'a giriş yapın
* Çıkan seçeneklerden **domain** alanını seçin ve domaininizi yazın
* Domaini satın aldığınız siteye giriş yapın ve **DNS Hizmeti ve Yönetimi** alanına girin
* **TXT Kayıtları** altında:
  * `Key` alanını boş bırakın
  * `Value` alanına Google'ın size verdiği metni kopyalayın.
    * (örn: `google-site-verification=********************************`)
* Çıkan arayüzde arama alanına URL'lerinizi yazın, indekslenmeyen URL için talepte bulunun

{% hint style="warning" %}
📢 Eğer sitenizde birden fazla sayfa varsa **Sitemaps.xml** dosyasını Google Search Console üzerine yükleyin
{% endhint %}

### 🧹 Eski Google Sonuçlarını Temizleme

* 🧼 [Remove outdated content](https://www.google.com/webmasters/tools/removals) alanından istediğiniz google sonucu temizleyebilirsiniz
* 📢 Gerekli alana [Find a webpage Url](https://support.google.com/webmasters/answer/63758) alanından veya [Google Search Console](https://search.google.com/search-console/removals?resource\_id=sc-domain%3Ayemreak.com) üzerinden açıklandığı şekilde veri giriniz
* 🚀 Tek tek girmek yerine bir dosyaya kaydedip [buradaki](https://github.com/noitcudni/google-webmaster-tools-bulk-outdated-content-removal) bağlantıdan harici eklentiyi kullanabilirsiniz

{% hint style="info" %}
👨‍💻 Eğer python diline hakim isen [YPackage](https://pypi.org/project/ypackage/) üzerindeki **🔍 Google Arama Motoru** ile tüm sonuçları toplayabilir,[ HTTP Status IO](https://httpstatus.io/) üzerinden durum kodlarına bakabilirsin
{% endhint %}

## 📊 Sitenize Gelenleri Analiz Etme <a href="#sitenize-gelenleri-analiz-etme" id="sitenize-gelenleri-analiz-etme"></a>

* ​[Google Analytics](http://analytics.google.com/)'e giriş yapın
* Sol alt köşedeki ⚙ Admin butonuna tıklayın
* `Property` alanında hiç hesap yoksa, `Add Propery`'e tıklayın, varsa isterseniz onu seçin
* `Tracking Info` alanından `Tracking Code`'u açın
  * **Tracking Id**'yi kopyalayın
  * Eğer sitenizin desteği yoksa **Website Tracking** adı altındaki **HTML** kodlarını kopyalayın.
* Sitenizin **HTML** kodlarına girin ve en üste `<scripts>`'lerinizin olduğu alana yapıştırın

### 💠 Filtre Uygulama <a href="#filtre-uygulama" id="filtre-uygulama"></a>

Admin - Property - Filter - Add Filter alanından aşağıdaki özelliklere sahip filtre ekleyin‌

* Filter Type: Custom
* Include
* Pattern `\.domain\.com` (örn: `\.yemreak\.com`) yazın
* Filter Verification alanından kontrol edip kaydedin.

## 🚙 Web Sitesi Yönlendirmesi <a href="#web-sitesi-yoenlendirmesi" id="web-sitesi-yoenlendirmesi"></a>

### 💨 Direkt Yönlendirme <a href="#direkt-yoenlendirme" id="direkt-yoenlendirme"></a>

```
<script type='text/javascript'>  var d='<data:blog.url/>';  d=d.replace(/.*\/\/[^\/]*/, '');  location.href = 'https://lib.yemreak.com';</script>
```

### 👨‍💼 Belirli URL'i Yönlendirme <a href="#belirli-urli-yoenlendirme" id="belirli-urli-yoenlendirme"></a>

```
<script>if(window.location.href == '<strong>Page URL</strong>'){window.location="https://lib.yemreak.com";}</script>
```

### 🕐 Gecikmeli Yönlendirme <a href="#gecikmeli-yoenlendirme" id="gecikmeli-yoenlendirme"></a>

Baştaki 5 sayısı kadar saniye olmak üzere bekler.

```
<meta content='5;URL=&quot;<url>/&quot;' http-equiv='refresh'/>
```

### 🧐 Daha fazla bilgi <a href="#daha-fazla-bilgi" id="daha-fazla-bilgi"></a>

{% embed url="http://www.marketingextremist.com/redirect-blogger-blog-page-another-blog-website-956/​" %}

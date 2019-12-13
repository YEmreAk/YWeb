# 🔰 Nodejs Giriş

## ❔ Nodejs Nedir <a id="nodejs-nedir"></a>

Node.js js \(javascript\) tabanlı bir platformdur.

* Kullandığı motor: v8 java-engine'dir. Ki bu motor, chrome için Google tarafından geliştirilmiştir. Chrome, chromium, opera gibi tarayıcılarda kullanılmaktadır.
* Temel olarak 2 yapıda çalışır:
  * Script işleme
  * A REPL \(Read Eval Print Loop\)

## Event Loop <a id="event-loop"></a>

* Normal çalışma mantığında; Kodlar todo list'e atılır. Ve yapılacak işlemler bitince motor durur.
* Node.js; Kodlar todo list'e atılır ve her kod yeni bir işlem daha oluşturur, böylece sonsuz döngüye girer ve motor durmaz. \(serverlar böyle tasarlanır.\)

## Asenkron Yapısı <a id="asenkron-yapisi"></a>

Normal işlemler sıra ile yapılır:

* Siteden database'ye mesaj gönderilir.
* Database mesajı alır ve hazırlar, cevap verme sürecine geçer.
* Bu süreçte server beklemede kalır, devam etmez ! \(Blocking\)

Nodejs'in asenkron yapısıyla:

* Database'den cevap gelene kadar, server diğer işlemlerine devam eder.
* Cevap geldiğinde database verisini işlemeye başlar \(Non-Blocking / asynchronize \)

## Node Module System <a id="node-module-system"></a>

* Bir dosyayı derleyerek bütün dosyaların çalışması sağlanır.
  * `var lib = require('.lib/');`
    * Dosyanın modülü, değişkene atanır.
    * ".lib/" değişkendir.
  * module.exports = veri;
    * Modulümüzün "require" ile çağrıldığında, göndereceği veriyi \("veri"\) atıyoruz.
* Bu şekilde tüm istenen dosyalar birbirine bağlı oluyor ve tek bir dosyadan derleniyor.

### Modül Sistemine Örnek <a id="moduel-sistemine-oernek"></a>

```text
var aktarılanFonksiyon = require('dosya2');​aktarılanFonksiyon.test();
```

```text
var kütüphane = {};​kütüphane.test = function() {    console.log('selam')}​Dışarı aktarılacak olan objemizi ayarladık.module.export = kütüphane;
```

> Artık "node dosya1.js" diyerek iki dosyayı da derleyebiliyoruz.

## Sonuç olarak <a id="sonuc-olarak"></a>

* Okumak istediğimiz dosyayı okuyur \(Yukarıdaki örnekte "dosya1.js"\)
* Bu dosyaya bağlı olan tüm diğer dosyaları da okur.
* Bu dosyalardaki senkronize görevleri işlemeye başlar.
* "todo list" teki kodları ,yapılacak herhangi bir iş kalmayana kadar, "event loop" ile tekrarlı olarak işlemeye başlar.


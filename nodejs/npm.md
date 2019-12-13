# 🥬 NPM

## CLI Uygulaması Yapma <a id="cli-uygulamasi-yapma"></a>

### CLI Args \(Komut Argümanları\) <a id="cli-args-komut-arguemanlari"></a>

Komut argümanları `node index.js arg1 arg2 ...` ile verilir.

* `process.argv` ile erişilir
* `process.argv[0]` Node'un yolu
* `process.argv[1]` Script'in yolu
* Geri kalanları kullanıcının yazıdığı parametrelerdir
* `process.argv.slice(2)` ile kullanıcı parametrelerine erişilir

#### Yargs ile Args Yönetme <a id="yargs-ile-args-yoenetme"></a>

Nodejs sitesindenki açıklamaya [buradan](https://nodejs.org/en/knowledge/command-line/how-to-parse-command-line-arguments/) erişebilirsin.

#### Minimist ile Args Yönetme <a id="minimist-ile-args-yoenetme"></a>

* İlk olarak projeye dahil edilmeli `npm install -save minimist`

```text
minimist(process.argv.slice(2))
```

> Ek bağlantılar:
>
> * *

### Bin Klasörü <a id="bin-klasoerue"></a>

Özel komutların tanımlanmasını sağlar.

* `<komut1>` Örnek komut ismidir
  * Örn: `yemreak`

**Dizin yapısı:**

```text
+ bin  - <komut1>  - <komut2>- index.js- README.md
```

**Dosya içeriği:**

```text
#!/usr/bin/env node require('../')() 
```

**Package json'a eklenecek ayar:**

Bu ayar ile bin dosyamız indirilip gerekli yere konumlandırılacaktır.

```text
"bin": {    "<komut1>": "bin/<komut1>",    "<komut2>": "bin/<komut2>"},
```

## Paket Yapımı Örnekleri <a id="paket-yapimi-oernekleri"></a>

* 
## Paketleri Online Test Etme <a id="paketleri-online-test-etme"></a>

* Paketleri indirmeden önce [buradan](https://npm.runkit.com/) test edebilirsin.

## Paket Oluşturma ve Yayınlama <a id="paket-olusturma-ve-yayinlama"></a>

* İlk olarak npm hesabını [buradan](https://www.npmjs.com/signup) oluşturun
* `npm adduser` ile kullanıcı oluşturun
  * `npm login` komutunu da kullana bilirsiniz
  * Oluşturulan token bilgisine [buradan](https://www.npmjs.com/settings/yedhrab/tokens) bakabilirsiniz
* `npm version v1.0.0` ile paketin sürümünü tanımlayın
* `npm publish` ile [npm sitesine](https://www.npmjs.com/) yükleyebilirsiniz

### Paket için Package.json Ayarları <a id="paket-icin-package-json-ayarlari"></a>

**Node sürümü ayarı:**

```text
"engines": {    "node": ">=8"}
```

**Global yükleme önerisi:**

**Tam Örnek:**

```text
{  "name": "ytools",  "version": "1.0.0",  "description": "Faydalı olacak araçların, toparlanmış hali",  "main": "index.js",  "scripts": {    "test": "echo \"Error: no test specified\" && exit 1"  },  "engines": {    "node": ">=8"  },  "preferGlobal": true,  "bin": {    "ytools": "bin/ytools"  },  "keywords": [    "yemreak",    "tools",  ],  "repository": {    "type": "git",    "url": "git+https://github.com/yedhrab/YTools.git"  },  "keywords": [    "tools"  ],  "author": "yedhrab",  "license": "MIT",  "bugs": {    "url": "https://github.com/yedhrab/YTools/issues"  },  "homepage": "https://github.com/yedhrab/YTools#readme",  "dependencies": {    "yargs": "^13.2.4"  }}
```

> Video örneğine [buradan](https://www.google.com/search?q=make+npm+module&oq=make+npm+module&aqs=chrome.0.0l6.2476j0j7&sourceid=chrome&ie=UTF-8#kpvalbx=1) erişebilirsin.


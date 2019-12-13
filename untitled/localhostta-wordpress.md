---
description: Wordpress'i localhost üzerinde çalıştırma
---

# 🏠 Localhost'ta Wordpress

## ⏬ XAMPP Kurulumu

XAMPP kurulum yönergeleri için alttaki işletim sistemlerine tıklayabilirsin:

* [Linux](https://github.com/yedhrab/YWiki/tree/169abadfd1b8862c004399268f6ca1f9f9359d61/1%20-%20Programlama%20Notları/5%20-%20Web%20Programlama/İşletim%20Sistemi%20Notları/Linux%20Notları.md#xampp-kurulumu)
* [Windows & MacOS](https://www.apachefriends.org/download.html)

## ✨ PHPMyAdmin Database Oluşturma

Wordpress kurulumu için veritabanı gerekmektedir.

* XAMPP üzerinden _MySQL_, _Apache_ sunucuları çalıştırın
* ​[Yerel sunucu sayfası](http://localhost/phpmyadmin/) olan `localhost/phpmyadmin` sayfasına girin
* Sol üst kısımdan `New` bağlantısına ya da [buraya](http://localhost/phpmyadmin/server_databases.php?server=1) tıklayın
* Database ismi ve karakter formatı belirleyin
  * Örn: `yemreak` `utf8_general_ci`
* İstediğiniz şekilde tablo ve sütunlar ekleyebilirsiniz

## 🚧 Wordpress Dosyalarının İndirilmesi ve Hazırlanması

_Wordpress_ dosyalarını indirmek için [buraya](https://wordpress.org/download/) tıklayabilirsiniz.

* İndirilen dosyaları çıkartıp XAMPP'ın `htdocs` dizinine taşıyın
  * Taşıdığınız `wordpress` adlı dosyasına ve alt dosyalarına **okuma ve yazma** erişimimizin olmasını sağlayın.
  * Linux için `sudo nautilus /opt/lampp/htdocs` ile dosya gezginini açıp, alttaki dosyalara sağ tıklayıp `Özellikler > İzinler` alanından her kullanıcıya \(_other_ en alttaki\) **okuma ve yazma** izinlerini verin.
    * Terminal ile bu komut yardımıyla `sudo chmod -R 757 /opt/lampp/htdocs/wordpress/` ya da el ile yetki verin.
    * `wordpress`
    * `wordpress/wp-content`
    * `wordpress/wp-admin`
    * `wordpress/wp-includes`
  * _Wordpress_'in oluşturduğu dosyalardaki kullanıcı adı `deamon`'dur. \(Dosya izinleri için gerekebilir\)
* İster [buraya](http://localhost/wordpress) tıklayarak, isterseniz `localhost/wordpress` yolu ile kopyaladığınız dizine tarayıcıdan erişin.
* İstenen bilgileri girin
  * Kullanıcı adı ve şifre işlemleri için [buraya](https://www.coderhold.com/how-to-change-or-set-phpmyadmin-password-on-xampp.html) bakabilirsiniz
* Yapılandırma dosyalarının oluşumunda hata meydana gelirse, XAMPP içerisindeki `htdocs/wordpress` dizinine `wp-config.php` dosyası oluşturup, içerisine yapılandırma bilgilerinizi yapıştırın.
* FTP kullanmak için `wp-config.php` dosyanıza `define('FS_METHOD', 'direct');` satırını ekleyin.
  * FTP için kullanıcı adı ve şifreniz **PC**'nizin bilgileridir, wordpress hesabınızın değil.
  * FTP ile yerel dosya işlemleri yapabilirsiniz
  * İnternet'ten tema indirme, deneme vs.

## 🏹 Wordpress'in Aktarılması

_Wordpress_'in aktarılması için:

* Tüm dosyaların aktarılması
* Veriler _database_'de tutulduğu için, _database_'in aktarılması
* Yapılandırma dosyasının aktarılması ya da yeniden oluşturulması

gerekmektedir.


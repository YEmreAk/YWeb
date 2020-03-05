# 💳 OpenCart

## Model View Controller Yapısı <a id="model-view-controller-yapisi"></a>

> MVC hakkında bilgi sahibi olmak istersen [buraya](https://github.com/yedhrab/YWiki/tree/169abadfd1b8862c004399268f6ca1f9f9359d61/1%20-%20Programlama%20Notlar%C4%B1/5%20-%20Web%20Programlama/Proje%20Y%C3%B6netimi%20Notlar%C4%B1/Proje%20Y%C3%B6netimi/README.md#Model%20View%20Controller%20Yap%C4%B1s%C4%B1) tıklayabilirsin.

* Lazım ise veri tabanında `[name]` adı verilen sütun oluşturulur.
  * MySQL sorgu örneği için [buraya]() tıklayın.

> `[Name]` bir değişken ismidir. _Örn: product\_info_

* **Model** dizinindeki gerekli veri tabanı metodlarını güncelleme
  * `add*`, `edit*` metodlarındaki mySQL sorguları \(_Insert, Update_\) güncellenir
  * Dosya ve dizin yolları:
    * _...\webadmin\model_
    * _...\model_
    * _...\webadmin\model_ _`dizin`_ _`dosya adı`.php_
* **Controller** dizinindeki uygun dosyadan model yüklenir.
  * Model yüklenir. Kod örneği için [buraya]() tıklayabilirsin.
  * Veri modelden alınır. Kod örneği için [buraya]() tıklayabilirsin.
  * View'a veriyi gönderme: Kod örneği için [buraya]() tıklayabilirsin.
  * Dosya ve dizin yolları:
    * _...\webadmin\controller_
    * _...\controller_
    * _...\webadmin\controller_ _`dizin`_ _`dosya adı`.php_

      > `$data` değikeni içindeki veriler _view_'a iletilir.
* **View** dizinindeki TPL uzantılı dosya üzerinde görsel düzenleme yapılır.
  * Dosya ve dizin yolları:
    * _...\webadmin\view_
    * _...\view_
    * _...\webadmin\view_ _`dizin`_ _`dosya adı`.tpl_

### Modeli yükleme <a id="modeli-yuekleme"></a>

```text
$this->load->model('catalog/manufacturer');
```

### Veriyi modelden alma <a id="veriyi-modelden-alma"></a>

```text
$[veri adı] = $this->[model]->[get metodu]();
```

### Veriyi view'a gönderme <a id="veriyi-viewa-goenderme"></a>

## CSS dosyaları <a id="css-dosyalari"></a>

* Örnek dizin: `...\catalog\view\asset\style\`
* Tam dizin: `C:\xampp\htdocs\ecommerce2\catalog\view\asset\style\custom.scss`

## Ana sayfaya satır ekleme <a id="ana-sayfaya-satir-ekleme"></a>

* Lazım ise veri tabanında `[name]` adı verilen sütun oluşturulur.
  * MySQL sorgu örneği için [buraya]() tıklayın.
* View için değişken oluşturma. Kaynak kod örneği için [buraya]() tıklayabilirsin.
  * View kısmında `$[veri ismi]` olarak kullanabilirsin.

## Form / List Ekleme <a id="form-list-ekleme"></a>

* Veri tabanında `[name]` adı verilen sütun oluşturulur.

  * MySQL sorgu örneği için [buraya]() tıklayın.

  > `[Name]` bir değişken ismidir. _Örn: product\_info_

* **Model** dizinindeki gerekli veri tabanı metodlarını güncelleme

  > MySQL üzerindeki verileri sorgular yardımıyla projeye ekleyen yapıdır.
  >
  > * `add*`, `edit*` metodlarındaki mySQL sorguları \(_Insert, Update_\) güncellenir
  > * _Örnek Yol: webadmin\model_
  > * _Örn: C:\xampp\htdocs\ecommerce2\webadmin\model\sale\special\_promotions.php_

* **Controller** dizinindeki Uygun dosyanın `getForm` / `getList` metodunda entry değişkenlerini ve verileri oluşturma

  > Veriler $data değişkeni ile _.tpl_ uzantılı dosyaya aktarılır.
  >
  > * Entry eklenir. Kaynak kodu için [buraya]() tıklayabilirsin.
  > * Veri oluşturma. Kaynak kod için [buraya]() tıklayabilirsin.
  > * _Örnek Yol: webadmin\controller_
  > * _Örn: C:\xampp\htdocs\ecommerce2\webadmin\controller\sale\special\_promotions.php_

* **Languages** dizinindeki PHP uzantılı dil dosyası üzerinde değişken oluşturulur.

  > Dillere özgü metinler oluşturmak adına kullanılır.
  >
  > * _Örnek Yol: webadmin\language\turkish_
  > * _Örn: ecommerce2\webadmin\language\turkish\sale\special\_promotions.php_

* **View template** dizinindeki _.tpl_ uzantılı dosya üzerinde görsel düzenleme yapılır.

  > Front-end kısmıdır.
  >
  > * `tr` satırı kopyalanıp, `name` değerleri `entry_[name]` yapısı ile alınır
  > * _Örn: ecommerce2\webadmin\view\template\sale\special\_promotions\_form.tpl_

### Form için entry ekleme <a id="form-icin-entry-ekleme"></a>

```text
$this->data['entry_[name]'] = $this->language->get('entry_[name]');
```

### Form verisi oluşturma <a id="form-verisi-olusturma"></a>

```text
if (isset($this->request->post['[name]'])) {    $this->data['[name]'] = $this->request->post['[name]'];} elseif (!empty($special_promotion)) {    $this->data['[name]'] = $[değişken]['[name]'];} else {    $this->data['[name]'] = 0; }
```

* `[değişken]` Model ile alınan mySQL verilerini tutan değişken

  > Tablo değişkeni için `$special_promotion` veya `$order_info` örnek olabilir.

* `[name]` MySQL sütun ismi

  > Sütun ismi için `$product_info` örnek olabilir.

> Veri oluşturulmazsa `TLP` \(front-end\) kısmında görmez.

## Filtreleme <a id="filtreleme"></a>

```text
$results = $this->model_sale_order->getOrders($data);
```

* **Model** dizinindeki gerekli veri tabanı metodlarını güncelleme

  > MySQL üzerindeki verileri sorgular yardımıyla projeye ekleyen yapıdır.
  >
  > * `get*s`, `getTotal*s` metodlarındaki mySQL sorguları güncellenir. Kaynak kodu için [buraya]() tıklayabilirsin.
  >
  >   `$data` değişkeninin kullanıldığı alanlar güncellenir.
  >
  > * _Örnek Yol: webadmin\model_
  > * _Örn: C:\xampp\htdocs\ecommerce2\webadmin\model\sale\order.php_

* **Controller** dizinindeki Uygun dosyanın `getList` metodunda filtreleme değişkenlerini \(filters\) ve verileri oluşturma

  > Veriler $data değişkeni ile _.tpl_ uzantılı dosyaya aktarılır.
  >
  > * Filtreleme değişkeni \(filter\) eklenir. Kaynak kodu için [buraya]() tıklayabilirsin.
  > * Veri \(data\) oluşturma. Kaynak kod için [buraya]() tıklayabilirsin.
  > * _Örnek Yol: webadmin\controller_
  > * _Örn: C:\xampp\htdocs\ecommerce2\webadmin\controller\sale\order.php_

* **View** kısmında filtre ekleme alanı oluştulur. Kaynak kod için [buraya]() tıklayabilirsin.
  * Filtreleme butonunun js kısmındaki `filter()` metodunda güncelleme yapılır. Kaynak kod için [buraya]() tıklayabilirsin.

### Filtre Alanı Ekleme <a id="filtre-alani-ekleme"></a>

```text
<?php<select name="filter_[names]">    <?php foreach ($[names] as $[name]) { ?>        <?php if ($[name]['[name_id]'] == $[name_id]) { ?>        <option value="<?php echo $[name][[name_id]]; ?>" selected="selected"><?php echo $[name]['name']; ?></option>        <?php } else { ?>        <option value="<?php echo $[name][[name_id]]; ?>"><?php echo $[name]['name']; ?></option>        <?php } ?>    <?php } ?></select>
```

### Filtreleme değişkeni oluşturma <a id="filtreleme-degiskeni-olusturma"></a>

```text
if (isset($this->request->get['[filter_name]'])) {    $[filter_[name]] = $this->request->get['filter_name'];} else {    $filter_store_id = null;}
```

* `[name]` MySQL sütununua eş değer değişken ismidir.

### Filtreleme verisini oluşturma <a id="filtreleme-verisini-olusturma"></a>

```text
$data = array(    'filter_[name]' => $filter_[name];);
```

* `[name]` MySQL sütununua eş değer değişken ismidir.

> Data verisinde birden fazla değişken olabilir. Örn:

```text
$data = array(    'filter_store_id'        => $filter_store_id,    'filter_store_name'      => $filter_store_name,    'filter_order_id'        => $filter_order_id,    'filter_customer'        => $filter_customer,    'filter_order_status_id' => $filter_order_status_id,    'filter_total'           => $filter_total,    'filter_date_added'      => $filter_date_added,    'filter_date_modified'   => $filter_date_modified,    'filter_payment_method'  => $filter_payment_method,    'filter_[name]'          => $filter_[name],    'sort'                   => $sort,    'order'                  => $order,    'start'                  => ($page - 1) * $this->config->get('config_admin_limit'),    'limit'                  => $this->config->get('config_admin_limit'));
```

### Filtreleme URL'i oluşturma <a id="filtreleme-urli-olusturma"></a>

```text
if (isset($this->request->get['filter_[name]'])) {    $url .= '&filter_[name]=' . $this->request->get['filter_[name]'];}
```

> Her `$url = '';` aşaması için üstteki yapılır.

```text
$this->data['filter_[name]'] = $filter_[name];
```

* `[name]` MySQL sütununua eş değer değişken ismidir.

### Filtreleme Sorgusu <a id="filtreleme-sorgusu"></a>

```text
if (!empty($data['filter_[name]'])) {    $sql .= " AND [tablo].[name] = '" . $this->db->escape($data['filter_[name]']) . "'";}
```

### Filtreleme filter\(\) metodu <a id="filtreleme-filter-metodu"></a>

```text
var filter_[name] = $('select[name=\'filter_[name]\']').val();​if (filter_[name]) {    url += '&filter_[name]=' + encodeURIComponent(filter_[name]);}
```

* `[name]` MySQL sütununua eş değer değişken ismidir.

## Karma Kodlar <a id="karma-kodlar"></a>

### MySQL Kodları <a id="mysql-kodlari"></a>

```text
SELECT [ID], [Sütun] FROM [Tablo] WHERE [ID] = [Sayı];UPDATE [Tablo] SET [Sütun] = [Değişken Tipine Uygun Değer] WHERE [ID] = [Sayı];INSERT INTO [Tablo] VALUES ([Sütun1 Değeri], [Sütun2 Değeri]);​CREATE TABLE IF NOT EXISTS [Tablo] (    [ID Sütunu] [Değişken Tipi] DEFAULT [Varsayılan Değer] PRIMARY KEY,    [Sütun] [Değişken Tipi]);​ALTER TABLE [Tablo] ADD COLUMN [Sütun] [Değişken Tipi] DEFAULT [Varsayılan Değeri] AFTER [Önceki Sütun];ALTER TABLE [Tablo] DROP COLUMN [Sütun];ALTER TABLE `cookplus_order` ADD COLUMN `cancel_status_id` int(1) DEFAULT '0';
```

### Checkbox kodu <a id="checkbox-kodu"></a>

OpenCard form verisine checkbox ekleme yapısı

```text
<tr>    <td><?php echo $entry_[name]; ?></td>    <td>        <input type="checkbox" name="[name]" value="1" <?php if($[name]) echo 'checked="checked"'; ?> />    </td></tr>
```

> `name` Değişken ismi

### Controller'da view için değişken oluşturma kodu <a id="controllerda-view-icin-degisken-olusturma-kodu"></a>

```text
$[veri ismi] = $this->model_catalog_manufacturer->getManufacturers();​foreach ($[veri ismi] as $[veri parçası]) {    $this->data['[veri ismi]'][$[veri parçası]['[özellik1]']] = array(        '[özellik2]' => $[veri parçası]['[özellik]'],        '[özellik3]' => $[veri parçası]['[özellik]']    );}
```

### Selection box kodu <a id="selection-box-kodu"></a>

```text
<?php<select name="filter_[names]">    <?php foreach ($[names] as $[name]) { ?>        <?php if ($[name]['[name_id]'] == $[name_id]) { ?>        <option value="<?php echo $[name][[name_id]]; ?>" selected="selected"><?php echo $[name]['name']; ?></option>        <?php } else { ?>        <option value="<?php echo $[name][[name_id]]; ?>"><?php echo $[name]['name']; ?></option>        <?php } ?>    <?php } ?></select>
```


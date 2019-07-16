---
id: dashboardOverview
title: Dashboard Genel Bakış ve Çalışma Ortamı
sidebar_label: Dashboard
---

Logsign SIEM, kaynaklardan elde ettiği verilerin(logs/events) bir kopyasını imzalı/şifreli olarak saklarken aynı anda bu ham olay verileri, eyleme dönüştürülebilir bilgi elde etmek için log ayrıştırma(parsing) ve zenginleştirme(enrichment) süreçlerine dahil edilirler.

Logsign SIEM; bu olay verileri üzerinde, farklı türde grafik çizimleri ile istediğiniz data objelerine odaklanmanızı ve etkili olay incelemesi yapmanızı sağlayan bir Dashboard modülüne sahiptir.

Logsign'a login olunduğunda ön tanımlı Welcome Dashboard'u karşılama sayfası olarak açılır.

<div>
<img src="/img/dashboard/dashoverview/dashboard-1.png" >
<p class="figure">Figure 1. Welcome dashboard çalışma alanı üzerindeki farklı grafikleri içeren ön tanımlı Widget’lar</p>
</div>


<b>Logsign dashboard modülü aşağıda gösterilen kısımlardan oluşur.</b>

<div>
<img src="/img/dashboard/dashoverview/dashboard-2.png">
<p class="figure">Figure 2. Dashboard menü bileşenleri</p>
</div>


**1.** Menü çubuğunda yer alan Dashboard simgesi üzerine gelindiğinde Dashboard menüsü açılır; simge tıklandığında ise doğrudan (ön tanımlı)Welcome Dashboard'una ulaşım sağlanır.

**2.** Dashboard menüsünde yer alan Dashboards menü öğesine tıklayarak da yine Welcome Dashboard'una ulaşabilirsiniz. Ayrıca dashboard yapılandırmalarını yapabileceğiniz dashboard alt menüsü yine bu sayfa üzerinde yer alır. (ilerleyen bölümde anlatılacak)

**3.** Install Dashboards menü öğesine tıklayarak farklı grafik tiplerinde hazır Widgetlar’ı içeren yerleşik/ön tanımlı Dashboard'ları yükleyebilirsiniz. Dashboard’lar, dashboard kategorilerine dahildirler ve bir kategori altindaki herhangi bir Dashboard'u tek olarak yükleyebileceğiniz gibi yalnızca kategoriyi yükleyerek, bu kategoriye dahil olan tüm Dashboardlar’ın yüklenmesini sağlayabilirsiniz.

<br/>
**Menu çubuğundan Dashboard simgesine tıklayarak ulaşabileceğiniz dashboard alt menüsü ve bileşenleri aşagıda gösterildiği gibidir.**
<div>
<img src="/img/dashboard/dashoverview/dashboard-3.png" >
<p class="figure">Figure 3. Dashboard alt menü bileşenleri</p>
</div>

**1-** Dashboard kategorileri ve Dashboard’ların listelenmesi/düzenlenmesi amacıyla kullanılan menüdür.

**2-** **New Dashboard** butonuna tıklayarak (yerleşik dashboard kategorilerinden olan Custom Dashboards yada kullanıcı tanımlı herhangi bir kategori altında) yeni bir dashboard oluşturabilirsiniz.

**3-** Dashboard kategorileri ve bu kategorilere dahil Dashboard listesi... Yerleşik/ön tanımlı iki dashboard kategorisi bulunur; **Custom Dashboards** ve **Welcome Dashboard.**

**4-** Yerleşik Welcome Dashboard kategorisi ve buna dahil olan yerleşik Welcome dashboardu.

**5-** **Add Category** butonuna tıklayarak yeni bir dashboard kategorisi oluşturabilirsiniz

**6-** **Edit Menu** butonu, yerleşik kategoriler(Custom Dashboards ve Wellcome Dashboard) dışında yeni bir kategori oluşturulduğunda etkinleşerek dashboard kategorileri ve dashboardlar ile ilgili (menu sıra düzeni gibi) düzenleme işlemlerini yapmanızı sağlar.

<blockquote class="orangeblock"> <b>Not:</b> Ön tanımlı dashboard kategorileri silinemezler.</blockquote>

<p class="baslik">Dashboard Kategorisi Oluşturmak</p>


- Yeni bir dashboard kategorisi oluşturmak için dashboard alt menüsü üzerinde **Add Category** butonuna tıklayın ve Kategori ismini girdikten sonra **Save** butonuna basın.

<div>
<img src="/img/dashboard/dashoverview/dashboard-4.png">
<p class="figure">Figure 4. Yeni dashboard kategorisi oluşturma</p>
</div>


<div>
<img src="/img/dashboard/dashoverview/dashboard-5.png" >
<p class="figure">Figure 5. Dashboard ve dashboard kategorilerine menü üzerinden erişim</p>
</div>

<p class="baslik">Dashboard Oluşturmak</p>

Yeni bir dashboard olusturmak icin asagidaki adimlari izleyin.

<div>
<img src="/img/dashboard/dashoverview/dashboard-6.png" >
<p class="figure">Figure 6. Dashboard kategorisi altında yeni dashboard oluşturulması</p>
</div>

- Dashboard alt menüsü üzerinde **New Dashboard** butonuna tıklayın.

- Dashboard Name alanına dashboard ismini girin.

- Category açılır listesinden dashboardun dahil olacağı dashboard kategorisini seçin.

- Profiles açılır listesinden <i>(isteğe bağlı)</i> bir dashboard profili* seçerek **Save** butonuna tıklayın.

<blockquote class="orangeblock"> * Dashboard Profiles / Interface Profiles yapılandırmaları ile Logsign uzerinde tanımlı Admin olmayan kullanicilarin dashboard kategorileri ve dashboardlar uzerinde (okuma/düzenleme/silme) yetkilerini belirleyebilirsiniz.</blockquote>
<br/>

Otomatik yönlendirme sonrasında SOC-1 kategorisi altındaki SOC Analyst-1 dashboard calışma alanı ekranda boş olarak görüntülenecektir.
<div>
<img src="/img/dashboard/dashoverview/dashboard-7.png">
<p class="figure">Figure 7. Dashboard çalışma alanı</p>
</div>

<p></p>

Bu aşamada hızlıca sayfa üzerinde yer alan **Add Widget** butonu ile dashboard çalışma alanı uzerine farklı tiplerde grafikler eklemeye hazırsınız. Oluşturduğunuz dashboard çalışma alanlarına **Widget ekleme ve grafik tipleri** ile ilgili detaylara ilgili bölümden ulaşabilirsiniz.

Oluşturulan dashboard kategorileri ve dashboard'ların menu uzerindeki görünümü Figure-8 de görülebilir.

<div>
<img src="/img/dashboard/dashoverview/dashboard-8.png">
<p class="figure">Figure 8. Dashboard oluşturma sonrası menü görünümü</p>
</div>


<p class="baslik">Dashboard ve Dashboard Kategorilerini Düzenleme</p>

Dashboard alt menüsü üzerinde listelenen dashboardların üzerine gelindiginde beliren butonları kullanarak kullanıcı tanımlı dashboardlar üzerinde hızlıca isim/kategori/profile değişikliği ve silme işlemlerini gerçekleştirebilirsiniz.

<div>
<img src="/img/dashboard/dashoverview/dashboard-9.png" >
<p class="figure">Figure 9. Hızlı dashboard düzenleme</p>
</div>

<p class="baslik">Edit Menu ile Dashboard Düzenlemeleri</p>

En az bir adet kullanıcı tanımlı dashboard kategorisi eklendiğinde etkinleşen Edit Menu'yu kullanarak;

1. Dashboard ve Dashboard kategorilerini birbiri içinde sürukle bırak yöntemi ile hızlıca düzenleyebilir,
2. Dashboard kategorilerini yeniden isimlendirebilir,
3. Dashboard kategorisini icerdigi tum dashboardlar ile birlikte silebilirsiniz.

<div>
<img src="/img/dashboard/dashoverview/dashboard-10.png">
<p class="figure">Figure 10. Edit Menu</p>
</div>

- Dashboard kategori isminin hemen yanında yer alan butonlar ile ilgili dashboard kategorisinin ismini değiştirebilir yada ilgili kategoriyi içerdigi tüm dashboardlar ile birlikte silebilirsiniz.

<div>
<img src="/img/dashboard/dashoverview/dashboard-11.png" >
<p class="figure">Figure 11. Edit Menu - dashboard kategori işlemleri</p>
</div>

- Yeni bir dashboard kategorisi oluşturmak için **New Category** butonuna tıklayın. Category Name alanına dashboard kategori ismini yazarak **Save** butonuna tıklayın.

<div>
<img src="/img/dashboard/dashoverview/dashboard-12.png" >
<p class="figure">Figure 12. Edit Menu- yeni dashboard kategorisi oluşturma</p>
</div>

<div>
<img src="/img/dashboard/dashoverview/dashboard-13.png" >
<p class="figure">Figure 13. Kategori oluşturma sonrası</p>
</div>

**Bu kısımda Sürükle & Bırak yöntemini kullanarak;**

- Dashboard’ları, aynı yada farklı dashboard kategorileri içinde çapraz yönlü taşıyarak menü üzerindeki sıra düzeni ve kategorisini,
- Dashboard kategorilerinin menü üzerindeki sıra düzenini değiştirebilirsiniz.

<div class="main-div">
<img class="main-image" src="/img/dashboard/dashoverview/dashboard-14.png" >
<p class="figure">Figure 14. Sol resim değişiklik öncesi, sağ resim değişiklik sonrası sıra düzeni</p>
</div>

<blockquote class="orangeblock"><b>NOT:</b> Düzenleme sonrasında değişiklikleri kalıcı olarak saklamak icin <b>Save Changes</b> butonuna tıklayın.</blockquote>
<br/>

Düzenleme sonrasında Dashboard ve Dashboard kategorilerinin menu uzerindeki görünümü Figure-15 de görülebilir.

<div>
<img src="/img/dashboard/dashoverview/dashboard-15.png" >
<p class="figure">Figure 15. Dashboard ve dashboard kategorilerinin menü üzerindeki görünümü</p>
</div>

<!--- ===========C H A R T S & W I D G E T S============= -->

<h1>Dashboard Widgets/Charts</h1>

Bir dashboard calisma alani icerisine farkli tiplerde Widget'lar ekleyebilirsiniz. Eklediginiz Widget'ları calisma alani icerisinde dilediginiz sekilde boyutlandirabilir ve konumlandirabilirsiniz. Asağıda bir dashboard calisma alani uzerinde ekleyebileceginiz widget tipleri ile ilgili bilgilere ulasabilirsiniz.

<p class="baslik">Histogram with Bar Chart</p>

Histogram, belirli bir veri yığınının işlenmesi sonucu elde edilen veri gruplarinin zamansal bazda grafik cizimi ile gosterimidir.
Dashboard'unuzda ilgili veri gruplarinin zamansal bazda 'bar/çubuk' grafiği ile gösterilmesini istiyorsaniz Histogram with Bar Chart grafigini kullanabilirsiniz.

- Menu cubugundan Dashboard simgesine tıklayın.
- Dashboard alt menusunu kullanarak soz konusu grafigi iceren Widget’i eklemek istediginiz Dashboard’u tıklayın.

<div>
<img src="/img/dashboard/widgets-charts/histogram-1.png" >
<p class="figure">Figure 1. CIR isimli dashboard kategorisi altindaki Security Analyst dashboardu uzerinde Histogram with Bar Chart grafiginin eklenmesi</p>
</div>

- Dashboard calisma alani uzerindeki <b>Add Widget</b> butonuna tıklayın
- <b>Select Widget</b> sekmesinde <b>Histogram with Bar Chart</b> secerek Next butonuna tiklayin.

<div>
<img src="/img/dashboard/widgets-charts/histogram-2.png" >
<p class="figure">Figure 2. Widget Selection</p>
</div>

- <b>Content Settings</b> sekmesinde asagida detaylari aciklanan yapilandirmalari tamamlayarak <b>Next</b> butonuna tıklayın.

<div>
<img src="/img/dashboard/widgets-charts/histogram-3.png" >
<p class="figure">Figure 3. Content Settings</p>
</div>


+ <b>`Title:`</b> İlgili dashboard calisma alani icerisinde eklenecek olan widget başlığı
+ <b>`Information Source:`</b> Grafigi olusturulacak veriler icin 3 farkli bilgi kaynagi mevcuttur.
  * <b>`Reports:`</b> SIEM uzerinde ekli olan log kaynaklarindan alinan log /event verileri
  * <b>`Captive Portal:`</b> Hotspot modülü etkin olan sistemlerde, verileri hotspot uzerinden aktarilan kullanicilar ile ilgili bandwidth kullanimi, baglanti sureleri gibi Hotspot verileri
  * <b>`Logsign Events:`</b> SIEM sistem disk, redis-server, kaynak health-check, signed-archive klasorleri ve Elasticsearch kontrollerine ait sonuc verileri
+ <b>`Time Column: !!!!`</b>   Yazilacak fakat sorun oldugunu dusunuyorum!!!! Ne yazilacak ?
+ <b>`Grouped Column:`</b> Gruplanarak grafigi olusturulacak kolonu belirtir.
+ <b>`Grouped Column Order Type:`</b> Gruplanan kolonun sıralama bicimini belirtir. Gruplanan kolonun icerdigi farkli her bir degerin "oluşum sayısı bazında" artan/azalan <b>(count/reverse count)</b> yada yine gruplanan kolonun icerdigi degerlerin "isim bazında" artan/azalan <b>(Term/Reverse Term)</b> sıralanmasını sağlar.
+ <b>`Refresh Time:`</b> Dashboard uzerindeki grafigin kac sn/dk bir yenilenecegini belirtir.
+ <b>`Query:`</b> Olusturulacak grafigin baz alinacagi veri setini döndüren sorguyu belirtir.
+ <b>`Rows Per Page:`</b> Grafikte bir sayfada yer alacak en fazla satir/kayit sayisini belirtir.
+ <b>`Index Time:`</b> Grafigin olusturulmasinda kullanilan veri setini döndürecek sorgunun kac saatlik indexlenmis log verisi uzerinde calistirilacagini belirtir.

<blockquote class="blueblock"><b>Figure-3</b> de son 12 saatlik log indeksi baz alınarak meydana gelen alarmların Alarm ismine göre gruplandirilmasi ve en cok olusum sirasina gore siralanmis biçimde Histogram with Bar Chart grafik tipinde dashboard uzerine eklenmesi gosteriliyor.</blockquote>

<br/>
- View Settings sekmesinde aşağıdaki açıklamalar dogrultusunda <b>1.Column Size</b> ve <b>2.Column Size</b> secimlerini yaparak <b>Save</b> butonuna tıklayın.

<div>
<img src="/img/dashboard/widgets-charts/histogram-4.png" >
<p class="figure">Figure 4. View Settings</p>
</div>

+ <b>`1.Column Size:`</b> Eklenecek Widget'da yer alacak 1.kolonun, widget toplam genisliginin 12 esit parcaya oranidir. (4/12 = 12 de 4 oraninda genisliktir)
+ <b>`2.Column Size:`</b> Eklenecek Widget'da yer alacak 2.kolonun, widget toplam genisliginin 12 esit parcaya oranidir. (8/12 = 12 de 8 oraninda genisliktir)

<br/>
Security Analyst isimli dashboard calisma alani uzerinde olusturdugumuz 'Alerts - SIEM' isimli Histogram with Bar Charts tipindeki Widget Figure-5 de gorulebilir.


<div>
<img src="/img/dashboard/widgets-charts/histogram-5.png" >
<p class="figure">Figure 5. Histogram with Bar Chart</p>
</div>


<p class="baslik">Dashboard Çalışma Alanı Üzerinde Widget Yerleşimi <small>&</small> Düzeni</p>

- Widget'ları sayfa icinde sürükle & bırak yontemi ile dilediginiz yere konumlandirabilirsiniz.
- Grafik uzerindeki(Grafigin olusturulmasinda kullanilan ilgili olaylar baz alinarak uretilmis olan) oğelerin üzerine gelerek grafigin olusturulmasinda rol alan veriler ile ilgili bilgi alabilirsiniz.(Ilgili zaman dilimi icerisindeki olusum sayısı)
- Widget'ları sayfa icerisinde yeniden ölçeklendirebilirsiniz. 

<div>
<img src="/img/dashboard/widgets-charts/histogram-6.png" >
<p class="figure">Figure 6. Widget yerleşim düzeni</p>
</div>

<blockquote class="blueblock"><b>1.</b> Widget'ları sayfa icinde sürükle & bırak yontemi ile dilediginiz yere konumlandirabilirsiniz. <br/> <b>2.</b> Grafik uzerindeki(Grafigin olusturulmasinda kullanilan ilgili olaylar baz alinarak uretilmis olan) oğelerin üzerine gelerek grafigin olusturulmasinda rol alan veriler ile ilgili bilgi alabilirsiniz.(Ilgili zaman dilimi icerisindeki olusum sayısı)<br/><b>3.</b> Widget'ları sayfa icerisinde yeniden ölçeklendirebilirsiniz.  </blockquote>

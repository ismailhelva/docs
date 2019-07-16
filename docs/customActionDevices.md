---
id: customActionDevices
title: Custom Action Devices
---

Logsign Custom Action Devices ile Firewall, UTM* gibi guvenlik urunleri uzerinde yapilandirilmis Policy'lerin tetiklenmesini sağlayabilirsiniz. Sistem üzerindeki EPS miktarı önemli olmaksızın sürekli log akışı içerisinde analiz edilmesi ve aksiyon alınması zaman gerektiren işlemler, Custom Action Device kullanılarak ilgili güvenlik ürünlerinde tanımlı Policy'lerin tetiklenmesi sağlanarak daha hızlı tamamlanabilir.

<blockquote class="orangeblock"> * Logsign custom action devices şu an için Check Point, FortiGate ve Palo Alto markalarina ait programlanabilir XML API destegi olan guvenlik urunlerini desteklemektedir.</blockquote>


**Açıklama:** Bu döküman Logsign custom action devices özelliğini PaloAlto FW ürününü baz alarak üretim ortamına uygun bir senaryo kapsamında örnek bir yapılandırma ile açıklamaktadır.

<p class="baslik">Palo Alto Firewall Custom Action Device Ekleme</p>

- **Settings -> General Settings** yolunu izleyerek menü üzerinden **Custom Action Devices** tıklayın.

<div>
<img alt="Custom Action Devices" src=" /img/custom_action_devices/CAD-1.png">
<p class="figure">Figure 1. Custom Action Device Ekleme</p>
</div>

- **New Device** butonuna tiklayarak ilgili alanlari aciklamalar dogrultusunda doldurun.

<div>
<img alt="Custom Action Devices" src=" /img/custom_action_devices/CAD-2.png">
<p class="figure">Figure 2. Firewall API iletisimi icin parametrelerin girilmesi</p>
</div>


- <b>`Vendor:`</b> Şu an icin 3 farkli vendor destegi bulunmaktadir; Check Point, FortiGate ve Palo Alto. Listeden PaloAlto seçin.
- <b>`Host:`</b> API çağrılarının gönderileceği Palo Alto firewall IP adresini girin.
- <b>`Key:`</b> Firewall kendisine gelen API cagrilarini dogrulamak icin bir <b>API key</b> kullanir. API key, Figure-3 de gosterilen yonergeler dogrultusunda olusturulabilir.
- <b>`Virtual System:`</b> Virtual system, fiziksel bir firewall icinde ayri olarak yonetilebilecek sanal bir firewall ornegidir. Her bir vsys, kendi Security Policy'leri, Interface'leri ve bunları yöneten Admin'leri olan bagimsiz bir firewall olabilir. Bir vsys, güvenlik duvarının sağladığı tüm politikaların, raporlama ve görünürlük işlevlerinin yönetimini bölümlere ayırmanızı sağlar. Vsys ile ilgili özel bir yapilandirmaya sahip degil iseniz ön tanımlı seçeneği kullanabilirsiniz. (Detaylı bilgiye PaloAlto dökümanlarından ulaşabilirsiniz.)
- <b>`Protocol:`</b> Firewall'a gonderilecek API cagrilarinin hangi protokol uzerinden (HTTP/HTTPS) gerceklesecegini tanimlar. Firewall yapilandirmaniza uygun olan secenegi seçmelisiniz.*

<blockquote class="orangeblock"> * PaloAlto Firewall üzerinde Network -Network Profiles - Interface Mgmt kısmında ilgili (HTTP/HTTPS) servislerin secilerek izin verildigi (mevcut yada yeni olusturulan) bir profil, Network - Interfaces bölümünde listelenen interfacelerden API isteklerininin geleceği ilgili Interface'e atanmis durumda olmalidir. Boylece soz konusu Interface'e gelecek API cagrilari, izin verilen (HTTP/HTTPS) servis/protokol uzerinden karsilanabilecektir. (PaloAlto FW versiyon farklılıkları olabilir)</blockquote>


<p class="baslik">Palo Alto Firewall uzerinde API Key Olusturmak</p>
<p>Asagida gosterilen URL'i yapilandirmaniza uygun bicimde degistirerek internet tarayicinizda calistirin.</p>


    http[s]://firewall[:port]/api/?type=keygen&user=username&password=password


<blockquote class="orangeblock"> URL icerisinde, son kısımda kimlik bilgileri kullanilacak kullanici PaloAlto FW uzerinde Admin Roles'de ilgili "XML API" izinlerine sahip olmalidir.</blockquote>

<br/>

<div>
<img alt="Custom Action Devices" src=" /img/custom_action_devices/CAD-3.png">
<p class="figure">Figure 3. API key oluşturmak</p>
</div>


Key'i elde ettikten ve diğer alanları açıkalamalar doğrultusunda doldurduktan sonra New Action Device penceresi uzerinde Key alanına yapistirip Test Connection butonuna tıklayın; Connection Success mesajı sonrasında Save butonuna basarak yapilandirmayi kaydedin.

<div>
<img alt="Custom Action Devices" src=" /img/custom_action_devices/CAD-4.png">
<p class="figure">Figure 4. Bağlantı testi ve yapılandırmayı kaydetmek</p>
</div>

İşlem sonrasında Figure-5 de gosterilen Add Rule butonuna tikladiginizda gelen pencere uzerinde **Group Name** açılır listesinde FW uzerindeki mevcut dinamik adres gruplar listelenir. FW uzerinde dynamic address group, policy tanımı ve diger detaylar ilerleyen bolumde anlatilacagindan simdilik New Action Rule penceresini Cancel butonuna tiklayarak kapatabilirsiniz.

<div>
<img alt="Custom Action Devices" src=" /img/custom_action_devices/CAD-5.png">
<p class="figure">Figure 5. New Action Rule - Group Name (dynamic address group) seçimi</p>
</div>

<blockquote class="blueblock">Custom Action Device yapilandirmasini sırası ile asagidaki islemler dogrultusunda tamamlayacagiz</blockquote>

**1-** Logsign uzerinde tetiklenen alertler sonucunda elde edilen kosullara uygun IP adreslerinin FW uzerinde depolanacağı bir **dinamik adres grup** ve soz konusu adres grubu referans alarak gerekli **(allow/block vb.)** eylemi  meydana getirecek  bir **security policy** tanımı

**2-** Yukarıda Figure-5 de gosterilen **New Action Rule** penceresinde **Group Name** acilir listesinden 1. madde de tanimi gerceklestirilen ilgili **dinamik adres grubun**'un secilerek kaydedilmesi

**3-** Logsign tarafında "hangi verinin, hangi koşullarda" FW'a iletilecegini belirleyen bir **Alert** tanımı...


<p class="baslik">PaloAlto Firewall üzerinde Address Group ve Policy Oluşturmak</p>


Yapılandırmalar kapsamında PaloAlto FW ile ilgili bilinmesi gereken bazı kavramlar ve açıklamaları şöyledir:

**XML API:**  3.parti bir uygulama/servis/script uzerinden PaloAlto FW'a erişim ve yönetme imkanı verir. *(Logsign, PaloAlto FW ile bu yapı uzerinden iletisim kurar)*

**Dynamic Address Group:** Manual müdahale olmadan network adreslerini saklayabilen ve guncelleyebilen adres grup tipidir. *(Logsign, ilgili kosullar gerceklestiginde(ilerleyen bolumde anlatildigi uzere)tetiklenen Alert'ler doğrultusunda ilgili verileri(IP adreslerini) ilgili adres grupta tutulmak uzere XML API baglantisini kullanarak FW'a gonderir... Böylece Logsign tarafindan gonderilen IP adresleri FW uzerindeki ilgili adres grup tarafindan dinamik olarak tutulur.)*

- **Match(criteria):** FW uzerinde bir dinamik adres grup en az bir match criteria olmadan tanımlanamaz.(aşağıda detaylı olarak anlatılacak)

**Security Policy:** Security Policy Rule'ları, trafik özelliklerine gore bir oturuma izin verir yada engeller. Bir dinamik adres grup tarafindan tutulan IP adresleri ile ilgili bir eylem gerceklestirilebilmesi icin soz konusu adres grupun bir Security Policy icinde referans edilerek kullanilmasi gerekir. *(FW uzerinde tanimlanan dinamik adres grup Logsign tarafindan beslenir ve ilgili adres grupun uyeleri(IP adresleri) uzerinde ilgili policy tarafindan (allow/block vb.) bir eylem gerceklestirilir...)* (daha detaylı bilgiye PaloAlto dökümantasyonundan ulaşabilirsiniz)

**Öncelikle firewall üzerinde bir dynamic address group ve bir security policy aşağıdaki adımlar izlenerek tanımlanabilir:**

- FW web arayuzunden yetkili bir kullanıcı hesabı ile login olun.
- Üst menü bar uzerinden **Objects** ve sol menü bar dan **Address Groups** tıklayın.
- **Add** butonuna tıklayın ve ilgili alanlari Figure-5 ve asagidaki aciklamalar dogrultusunda doldurduktan sonra OK butonuna tiklayin.

<div>
<img alt="Custom Action Devices" src=" /img/custom_action_devices/CAD-6.png">
<p class="figure">Figure 6. PaloAlto FW üzerinde dynamic address group oluşturmak</p>
</div>

- <b>`Name:`</b> Address Group icin ayırt edici bir isim girin.
- <b>`Type:`</b> Soz konusu adress grup Logsign tarafindan beslenecegi icin **Dynamic** secenegini secin.
- <b>`Match:`</b> Diğer address grouplarinin etkilenmemesi amaciyla ayırd edici/diğer adres gruplarinda kullanilmayan bir match criteria girin.*

<blockquote class="orangeblock">*<b>Önemli Not:</b> Match alanı PaloAlto FW uzerinde dynamic address group tanimi yapilabilmesi icin deger girisi zorunlu alanlardan biridir. PaloAlto XML API iletisiminde dinamik adres grubun üyeleri match criteria kullanilarak elde edilir/güncellenir.(Detaylı bilgiye PaloAlto dokumantasyonundan ulaşabilirsiniz.) Bir başka ifade ile arka planda gerceklesen Logsign <-> PaloAlto FW XML API iletisiminde dynamic address group IP register/unregister islemlerinde adres grubun ismi yerine ilgili adres grupta girilen match criteria degeri kullanilir. Bundan dolayi tetiklenen alertler sonucunda FW'a gonderilecek verilerin bu amacla tanimlanan ilgili dinamik adres grup disinda diger dinamik adres gruplara iletilmesini onlemek icin soz konusu match criteria degerini, FW uzerindeki diger hic bir dinamik adres grubun icermemesi gerekir! Aksi durumda API baglantisi ile FW'da register/unregister edilecek IP adreslerinin yalnizca ilgili adres grupta degil -FW uzerindeki soz konusu aynı match degerinin kullanildigi- diger adres gruplarda da register/unregister olmasina sebep olur. Bunun anlamı ilgili IP adreslerinin istenmeyen adres gruplarında register/unregister islemi dolayisiyla FW uzerinde istenmeyen policy eylemlerinin gerceklestirilmesine yol açabilecek olmasıdır.</blockquote>

İkinci adim olarak, tanimladiginiz dinamik adres grubun aksiyon alinabilir duruma gelmesi icin bir policy icinde kullanilmasi gerekir.

- FW web arayuzunden **Policies -> Security** yolunu izleyerek gelen sayfa üzerinde **Add** butonuna tıklayın.
- Aşağıda gösterilen adımları izleyerek yeni bir Security Policy Rule tanımlayın.

**Aşağıda, yeni bir policy tanımının bir address group'u referans alarak nasıl yapılandırıldığı görülebilir.**


<div>
<img alt="Custom Action Devices" src=" /img/custom_action_devices/CAD-7.png">
<p class="figure">Figure 7. PaloAlto FW üzerinde Security Policy oluşturmak</p>
</div>

<div>
<img alt="Custom Action Devices" src=" /img/custom_action_devices/CAD-8.png">
<p class="figure">Figure 8. Security Policy Rule - General Sekmesi</p>
</div>

<div>
<img alt="Custom Action Devices" src=" /img/custom_action_devices/CAD-9.png">
<p class="figure">Figure 9. Security Policy Rule - Source Sekmesi</p>
</div>


<div>
<img alt="Custom Action Devices" src=" /img/custom_action_devices/CAD-10.png">
<p class="figure">Figure 10. Security Policy Rule - Destination Sekmesi</p>
</div>

<div>
<img alt="Custom Action Devices" src=" /img/custom_action_devices/CAD-11.png">
<p class="figure">Figure 11. Security Policy Rule - Service/URL Category Sekmesi</p>
</div>


<div>
<img alt="Custom Action Devices" src=" /img/custom_action_devices/CAD-12.png">
<p class="figure">Figure 12. Security Policy Rule - Actions Sekmesi</p>
</div>

**Log Forwarding:** *(opsiyonel)* Söz konusu policy kapsamında gerceklesen eylemlere ilişkin olayların / log kayıtlarının syslog ile (Logsign yada istenilen bir adrese) gonderilmesini saglayabilirsiniz. Soz konusu islem konumuz dışında olduğundan log yonlendirmesi ile ilgili detaylı bilgiye PaloAlto dokumantasyonundan ulasabilirsiniz.


<div>
<img alt="Custom Action Devices" src=" /img/custom_action_devices/CAD-13.png">
<p class="figure">Figure 13. Security Policy Rule - Commit</p>
</div>

<blockquote class="orangeblock"><b>Commit:</b> Policy yapılandırmasını tamamladıktan sonra değişikliklerin etkili olması için Commit butonu ile değişiklikleri onaylamalısınız.</blockquote>

Logsign Auto Action ismi ile olusturdugumuz adres grubu Source sekmesinden Source Address kısmından ekledik... ve son olarak Actions sekmesinden Action:Deny secimi ile policy yapilandirmasini tamamladik; boylece FW dan gecen paketler icerisinde soz konusu adres gruba dahil herhangi bir IP adresin source oldugu trafikler FW tarafından engellenecektir. Benzer yada cok daha farkli senaryolar dogrultusunda FW uzerinde policy yapilandirmalari gerceklestirebilirsiniz.

<blockquote class="orangeblock"><b>NOT:</b> Firewall uzerinden gecen tum trafik bir oturuma karsilik gelir ve her bir oturum bir security policy tarafindan degerlendirilir. PaloAlto FW uzerinde security rule'lari soldan saga ve yukaridan asagiya dogru degerlendirilirler. Bir paket, tanımlanan kriterleri karşılayan ilk rule ile eşleşir; yani bir eşleşme tetiklendikten sonra, bu paket için sonraki rule'lar değerlendirilmez. Bu nedenle, en iyi eşleşme ölçütlerini uygulamak için daha spesifik kuralların daha genel olanlardan önce gelmesi gerekir. (Ayrıntılı bilgiye PaloAlto dökümanlarından ulaşabilirsiniz)</blockquote>



<p class="baslik">Custom Action Device - New Action Rule oluşturmak</p>
Yukarıda Figure-5 de gösterilen Group Name bu aşamada seçilerek rule ekleme islemi tamamlanabilir...

- **Settings -> General Settings -> Custom Action Devices** yolunu izleyerek sayfa üzerinde yer alan **Add Rule** butonuna tıklayın...
- Aşağıdaki açıklamalar doğrultusunda **Group Name** ve **Expire Time** seçerek Save butonuna tıklayın.

<div>
<img alt="Custom Action Devices" src=" /img/custom_action_devices/CAD-14.png">
<p class="figure">Figure 14. New Action Rule - Group Name (dynamic address group) seçimi</p>
</div>

- <b>`Group Name:`</b> FW'daki mevcut dinamik adres grupların listesidir. FW uzerinde olusturdugunuz dinamik adres grubu secin.
- <b>`Expire Time:`</b> Logsign uzerinde tetiklenen alertler sonucunda FW'a gonderilen IP adreslerinin FW'da ilgili adres grup icinde ne kadar süre ile tutulacagini belirtir. FW'a ilgili adres grup icinde tutulmak uzere iletilen her bir IP adresi icin bu expire suresi belirli araliklarla ilgili Logsign servisi tarafindan kontrol edilir ve suresi dolan IP adreslerinin ilgili adres gruptan çıkarılmaları(unregister) işlemi için FW'a API çağrısı gönderilir. Listeden tercihiniz doğrultusunda  bir expire time suresi seçin.

<br/>
Figure-15 de ilgili Group Name ve Expire Time seçilerek Action Rule yapılandırması tamamlanan PaloAlto custom action device görülüyor.

<div>
<img alt="Custom Action Devices" src=" /img/custom_action_devices/CAD-15.png">
<p class="figure">Figure 15. Custom Action Device</p>
</div>





<!--- LOGSIGN UZERINDE ALERT TANIMLAMAK -->
<p class="baslik">Logsign üzerinde Alert tanımlamak</p>

<blockquote class="blueblock"><b>Özet:</b> Custom Action Devices sayfasinda PaloAlto FW API baglantisini olusturdunuz. FW uzerinde once bir dinamik adres grup, ardindan soz konusu dinamik adres grubu referans alarak Block eylemini gerceklestirecek bir policy yapilandirdiniz. Custom Action Devices sayfasina geri dönerek eklediginiz baglanti uzerinde FW'da tanimladiginiz adres grubu secerek bir action rule olusturdunuz.</blockquote>

Yapılandirmanin son aşamasi olarak, tetiklendiginde security automation kapsaminda FW'a ilgili verilerin gonderilmesini saglayacak bir alert tanimlayacağız. Soz konusu alert tanimi kapsaminda Logsign'a ulaşan logların Source.IP kolon değerleri, **Threat Intellegence IPs\*** isimli listenin tuttuğu IP ler ile karşılaştırılarak eşleşme olması durumunda alert tetiklenecek ve bunun sonucunda kosulu saglayan IP adresleri FW da ilgili adres gruba iletilecek...

<blockquote class="orangeblock"><b>*Enable Reputation Service:</b> Logsign, Threat Intelligence Database'lerinden belirli aralıklar ile zararlı aktivitelere sahip IP adreslerini çeker ve söz konusu IP adresleri <b>Threat Intellegence IPs</b> listesinde güncel olarak tutulur.(Threat Intelligence IPs yerleşik ve kullanıcı tarafından duzenlenemez bir listedir.) Reputation hizmetinin kullanilabilmesi icin <b>Settings -> License -> License Management</b> bolumunden <b>Reputation</b> hizmetinin lisansiniza dahil oldugundan ve <b>Settings -> Data Management -> Data Management</b> bölümünde Service Policy başlığı altından <b>Enable Reputation Service</b> onay kutusunun seçili olduğundan emin olun.</blockquote>

- Logsign web arayuzunden **Alerts -> Alert Rules** yolunu izleyerek **New Alert Rule** butonuna tıklayın.
- Formu asagidaki aciklamalar dogrultusunda doldurarak **Save** butonuna tıklayarak yapılandırmayı kaydedin.

<div>
<img alt="Custom Action Devices" src=" /img/custom_action_devices/CAD-16.png">
<p class="figure">Figure 16. New Alert with Security Automation</p>
</div>

- <b>`Description:`</b> Alert ismini girin.
- <b>`Category:`</b> Her bir alert tanımı bir alert kategorisine dahildir. Yerleşik alert kategorilerinden birini seçebilir yada hızlıca formdan ayrilmadan yeni bir alert kategori olusturmak icin listeden Add New Category seçerek görünür duruma gelen New Category alanina yeni kategori ismini girebilirsiniz.
- <b>`Severity:`</b> Alert'lerde Log'lar gibi farklı severity'lere sahiptirler. Boylece oluşan Alert'leri severity'lerine gore gruplayarak filtreleme yapabilirsiniz. Ilgili alert icin tercih ettiginiz bir severity secimi yapin.
- <b>`Rule:`</b> Açılır listeler sırası ile şunları listeler: Kullanilabilir geçerli kolonlar - Koşullar - Listeler. Figure-16 da gosterilen senaryo kapsaminda Logsign tarafından işlenen loglardan herhangi birinin Source.IP değeri, "Threat Intelligence IPs" listesindeki IP'lerden herhangi biri eşleşirse alert tetiklenir. Bu doğrultuda kolon olarak 'Source.IP', koşul olarak 'Behavior', liste olarak 'Threat Intellegence IPs' seçimlerini yapın ve 'Add' butonuna basarak rule olarak eklenmesini sağlayın.
- <b>`Action Column:`</b> Alert tetiklenmesine sebep olan log/loglar baz alınarak notification ve security automation kapsamında değerlendirilen kolondur... Logsign veritabaninizda 10.000 adet log oldugunu ve bu loglardan yalnizca 10 tanesinin yapilandirdiginiz alert rule(lar) ile esleserek ilgili alarmı tetikledigini varsayın...İlgili alert tanimi icerisinde Action Column olarak ornegin Source.IP sectiginiz varsayarak alertin tetiklenmesini saglayan bu 10 adet logun Source.IP degerleri ilgili adres grupta depolanmak uzere PaloAlto FW'a gonderilecektir. (Aşağıda açıklanan ayrıca Figure-16 gösterilen Security Automation etkinleştirilerek tetikleme sonucunda verilerin gönderileceğı vendor (PaloAlto) ve ilgili adres grup seçilmelidir.)
- <b>`Email:`</b> Ilgili kosul/kosullari saglayan alert meydana geldiginde E-mail ile bilgilendirme alabilirsiniz.
- <b>`SMS:`</b> Ilgili kosul/kosullari saglayan alert meydana geldiginde SMS ile bilgilendirme alabilirsiniz.
- <b>`Security Automation:`</b> Tetiklenen Alert'ler sonucunda, alert tetiklenmesini saglayan ilgili her bir logun icerdigi Action Column da seçtiğiniz ilgili kolon degerini PaloAlto FW'a gondermek icin onay kutusunu tiklayarak Security Automation'ı etkinlestirin.
- <b>`Vendor:`</b> PaloAlto seçin
- <b>`Group Name:`</b> Custom Action Devices sayfasında eklenen her bir Action Rule tanımında kullanılan dinamik adres gruplar listelenir. Figure-14'de gosterilen New Action Rule tanımında sectiğiniz adres grubu bu listeden seçin. (Figure-5 de goruldugu uzere Add Rule butonu kullanilarak bir custom action device icin birden fazla Action Rule eklenebilir dolayisiyla farkli alert tanimlari icerisinde farkli adres grupları secilerek FW uzerinde tanimli istenilen adres gruba veri gonderilmesi saglanabilir.)


<blockquote class="greenblock">Tebrikler !</blockquote>

**1-** PaloAlto FW uzerinde bir dinamik adres grup ve bu adres grubu baz alarak (block) aksiyon alan bir policy tanimladiniz.

**2-** Logsign uzerinde PaloAlto FW'u custom action device olarak eklediniz ve ilgili adres grubu referans alan bir action rule eklediniz.

**3-** Tetiklendiğinde koşulları sağlayan IP adreslerinin FW'a iletilmesini saglayan bir alert tanımı olusturdunuz.

 <blockquote class="orangeblock"><b>NOT:</b> Rule Set basligi altinda yer alan rule'lar AND mantiginda degerlendirilir bunun anlamı girilen rule'lardaki tum kosullarin saglanmasi durumunda alert'in tetiklenmesidir... Bundan dolayı Source.IP kontrolune ek olarak Destination.IP karsilastirmasi da yapmak istemeniz durumunda (Figure-16 da gosterildigi gibi yeni bir alert tanımlayıp, bu defa rule icinde Source.IP yerine Destination.IP secerek) yeni bir alert tanımlamalısınız.</blockquote>


Alerts - Alert Rules yolunu izleyerek olusturdugumuz alert tanımına göz atalım...

Figure-17 'de PaloAlto-AutoAction alert category'si altında tanımlanan AutoAction isimli Alert tanımı görülebilir

<div>
<img alt="Custom Action Devices" src=" /img/custom_action_devices/CAD-17.png">
<p class="figure">Figure 17. Alert Rules Pages</p>
</div>

Soz konusu alert tanımı kapsaminda Source.IP degeri, Threat Intelligence IPs listesi icinde yer alan zararlı aktiviteye sahip IP adresleri ile eşleşen her bir farklı log/event için bir alert meydana gelecektir.**\*** Bir alert tanimi kapsaminda tetiklenen alert olup olmadigini Figure-17 de gösterilen ilgili alert tanımınının yanında yer alan search butonuna tıklayarak görebilirsiniz.

 <blockquote class="orangeblock"><b>*</b> Log icerisinde yer alarak bir alertin tetiklenmesinde rol alan ilgili kolon/kolonlardaki degerler, log akışı icerisinde izleyen loglarda da bulundugunda yada bir kosula bagli olmaksizin soz konusu alertin 'belli bir sure boyunca' yeniden tetiklenerek birden fazla sayida olusmasini önlemek amaciyla Silence ve Mute ozellikleri kullanilir. Alert tanimi icerisinde Advanced Mode'a gecis yapilarak soz konusu ozellikler yapilandirilabilir. Tum alertler icin varsayilan olarak Silence ozelligi etkindir ve Silence Time suresi varsayilan olarak 600 saniyedir. Silence ve Mute ozellikleri ile ilgili detayli bilgiye Logsign SIEM Alerts dokumantasyonundan ulasabilirsiniz.</blockquote>
<br/>


<div>
<img alt="Custom Action Devices" src=" /img/custom_action_devices/CAD-18.png">
<p class="figure">Figure 18. Alert filtreleme</p>
</div>

Action.Object ve Source.IP kolonlarındaki IP adreslerinin aynı olduğunu farketmiş olmalısınız. Bunun sebebi Alert tanımında Action Column olarak Source.IP kolonunun seçilmiş olmasıdır. Oluşan her bir alert için Action.Object kolonundaki IP adresi, ilgili dynamic address group'ta depolanmak uzere PaloAlto FW'a gönderilir.


<div>
<img alt="Custom Action Devices" src=" /img/custom_action_devices/CAD-19.png">
<p class="figure">Figure 19. Tetiklenen Alert'ler tarafından FW'da ilgili address groupda register edilen IP adresleri</p>
</div>

**Settings -> General Settings -> Custom Action Devices** sayfasında daha once eklediginiz PaloAlto custom action device'a ait action rule uzerinde yer alan **Show** butonuna tiklayarak FW'a gönderilen IP adreslerini gorebilir ve uzerinde islem yapabilirsiniz. Ilgili adres grupdaki ilk 500 IP adresini **Search** alanını kullanarak filtreleyebilirsiniz. Arama sonucuna uygun IP adresleri search arama kutusunun hemen altında listelenir ve listedeki IP adreslerinden dilediğinizi **Unregister** butonuna tıklayarak ilgili adres gruptan çıkarabilirsiniz. **Unregister All** butonuna tiklayarak 'tüm IP adreslerinin' FW üzerindeki ilgili adres gruptan çıkarılmalarını saglayabilirsiniz. (Unregister edilen IP adresleri bu sebep ile ilgili adres grubu referans alan ilgili Policy'nin eyleminden -yeniden register edilene kadar- etkilenmezler.)



 <blockquote class="orangeblock">PaloAlto FW uzerinde bir dinamik adres gruba register edilebilecek IP sayısı (PaloAlto FW platform/seri'ye gore farklilik gosterir) 500'ün üzerindedir fakat <b>Panos XML API, adres gruptaki (en fazla) ilk 500 IP kaydını response olarak döner.</b> Panos XML API'nin bu kısıtlamasından dolayı Search field'inda yalnizca ilk 500 IP dahilinde arama yapabilirsiniz... Buna rağmen söz konusu limit sebebi ile Search'de bulamadığınız fakat ilgili address group icinde oldugundan emin oldugunuz herhangi bir IP adresini <b>Manual Request</b> ile unregister edebilirsiniz(Figure-19). Bu sayede FW uzerindeki ilgili address group'taki tum IP adreslerine erisebilir ve unregister islemi yapabilirsiniz.</blockquote>

# Örnek Bir Paket Oluşturulması

## Amaç

Bu bölüm altında paketin ilk oluşturulması aşamasından başlanarak, yayınlanma aşamasına kadar geçen süreçler adım adım örneklenecektir.

Örneğimizde kullanacağımız paketin amacı, temel Türkçe dil bilgisi kurallarını verilen metin üzerinde uygulanmasıdır. Örneğin;

***"bu bir örnek başlıktır"*** 

olarak verilen mesajı aşağıdaki başlık formatına uygulayan bir metotdumuz olacaktır;

***"Bu Bir Örnek Başlıktır"***

I> ## Bilgi
I>
I> Bu özelliği belirlemek tamamen bizim elimizde. Amacımız iş yapan bir paket geliştirmek yerine paket geliştirmeyi anlatmak olduğundan, örneğimizde kullancağımız paketin çok az bir işi yapıyor olması işimize gelmektedir.

## Temel Yapılandırma 

Temel olarak paketimizin hangi işi yapacağına karar verdikten sonra, paket ile ilgili genel ayarlamaları yapmamız gerekmektedir. Bu adımlar şöyledir;

* Paket Adının Belirlenmesi
* Paketin Deposunun Oluşturulması
* Paketin Yerele Alınması
* Composer Yapılandırması
* İlk Commit

### Paket Adının Belirlenmesi

Paket adı belirlenirken dikkat edilecek bazı önemli noktalar bulunmaktadır;

* Basit ve anlaşılır olması
* Mümkün olduğunca tekil (unique) olması
* Özel bağımlılıkların paket adında geçmesi
* Yöresel bir paket değilse, İngilizce bir isme sahip olması

Bu maddeler kural değil, temennidir. Basit bir isim her zaman daha kalıcı olacaktır. Aynı isme sahip yüzlerce paket ile karışmamak için eğer mümkünse olmayan bir ismi kullanmak yerinde olabilir. 

Eğer sadece bir framework'de çalışmak üzere bir paket geliştiriyorsanız, ilgili framework adının paket adında geçmesi(laravel-paket-adi) paketinizi çok daha iyi açıklayacaktır. 

Tüm bunlara ek olarak; sadece Türkiye'ye özgü bir paket geliştiriyorsanız, adının İngilizce olması gereksiz olacaktır. Buna en güzel örneklerden bir tanesi [Türk Medeni Kanunu](https://github.com/anonrig/turk-medeni-kanunu-json) deposudur. 

I> ## Bilgi 
I> 
I> Biz paketimizin adını "Example" olarak belirledik ve bundan sonraki işlemlerde bu isim üzerinden anlatım gerçekleştirilecektir. 

### Paketin Deposunun Oluşturulması

Bir sonraki adımımız paketimizi nerede muhafaza edeceğimizin belirlenmesidir. Biz herkese açık, [MIT Lisansı](http://opensource.org/licenses/MIT)'na sahip bir paket geliştirmek istiyoruz. Bu nedenlerden ötürü GitHub hesabımda **example** isimli bir depo (repo) oluşturacağım. 

Siz de kendi hesabınız üzerinden adımları birebir uygulayabilirsiniz.

Bunun için öncelikle ***GitHub*** üzerinde oturum açmanız gerekmektedir. Daha sonra sağ üstteki kullanıcı adınızın hemen yanında bulunan **+** butonuna tıklayarak, **"New Repository"** menüsü ile yeni depo oluşturma sayfasına gidebilirsiniz. 

Açılan form üzerinde **Repository Name** alanına deponuzun adını yazdıktan sonra **Create Repository** butonuna tıklayarak reponuzu oluşturabilirsiniz. 

I> ## Bilgi
I> 
I> Benim örneğimde kullancağım repoya [link](https://github.com/ozziest/example) aracılığı ulaşabilirsiniz.

### Paketin Yerele Alınması

Paketimizi ***GitHub*** üzerinde oluşturduktan sonra, çalışmalarımızı yapmak için kendi bilgisayarımıza almamız gerekmektedir. Bunun için paket oluşturulduktan sonra GitHub bize yardımcı olmak amacıyla örnek kodlar göstermektedir. Bu kodlar versiyon kontrol sistemi ***(Git)*** komutlarından oluşmaktadır. Git için hazırlanan kullanıcı arayüzleri olsa da, biz işlemlerimizi ***konsol (terminal)*** üzerinden gerçekleştireceğiz. 

Aşağıdaki komutu kendi paketinize göre düzenleyerek konsol üzerinde çalıştırınız;

```
$ https://github.com/kullanici-adi/paket-adi.git
```

Yukarıdaki komutta **kullanici-adi** yazan bölüme sizin kullanıcı adınız, **paket-adi** yazan bölüme ise sizin paket adınız gelmelidir. 

Komut çalıştırıldıktan sonra ilgili depo kendi çalışma ortamınıza indirilecektir. Aşağıdaki komut ile deponuz için ayrı bir klasör oluşturulduğunu görebilirsiniz;

```
$ ls -all
```

### Composer Yapılandırması

Depomuzu kendi bilgisayarımıza aldıktan sonra, depomuzun klasörünün içerisine girip aşağıdaki komutu çalıştırıyoruz ve ***composer*** yapılandırma dosyasını oluşturuyoruz;

```
$ composer init
```

Bu komut çalıştırıldıktan sonra ***composer*** bize çeşitli sorular soracaktır. Bunlar paket adı (yayıncı/paket adı), paket açıklaması vb. gibi sorulardır. Bu sorulara uygun cevapları yazarak yapılandırmayı tanımlayabilirsiniz.

### İlk Commit

Composer yapılandırması oluşturulduktan sonra ana dizinde bir composer.json dosyası oluşacaktır. Bu işlemden sonra var olan yapılandırmamızı ***GitHub*** üzerindeki depomuza gönderilerek ilk commit işlemimiz gerçekleştirilmiş olacaktır. Bunun için aşağıdaki komutlar sırasıyla çalştırılır;

```
$ git add .
$ git commit -m "Initial Commit Message"
$ git push origin master
```

Bu işlemden sonra yaptığımız değişiklikler depomuza gönderilmiş olacaktır.

## Döküman Oluşturulması

Bu başlığa özellikler yer vermek istiyorum. Çünkü bizim unuttuğumuz en önemli husustan biridir döküman hazırlanması. Çok harika işler yapıldığında dahi bunların belgelenmediğine şahit oluyoruz. Bu nedenle bir paket oluştururken, önce dökümanın hazırlanması oldukça önemlidir. ***"Ön işi yapalım, sonra açıklarız."*** demek yerine; ***"Ön nasıl çalışacağını belgeleyelim, sonra bu belgeye uygulayacak kodları yazarız."*** demek uzun vadede daha kârlı bir iş olacaktır.

Geliştireceğimiz paket için hazırlayacağımız döküman aşağıdaki temel bölümlerden oluşacaktır;

* Açıklama
* Kurulum
* Kullanım
* Lisans

I> ## Bilgi
I> 
I> Dökümanımızı [Markdown](https://help.github.com/articles/markdown-basics) formatında **Readme.md** dosyası içerisine yazacağız. GitHub, BitBucket gibi servisler otomatik olarak ***Readme.md*** dosyalarını biçimlendirmektedir.

Bu temel başlıkların yerine siz de hazırlayacağınız paketin durumuna göre ek başlıklar oluşturabilirsiniz. Bizim oluşturduğumuz paketin dökümanı [link](https://github.com/ozziest/example/blob/master/README.md) üzerinden incelenebilir.

## Test Yazılması

Test yazımı ne yazık ki bir çoğumuzun uymadığı bir husustur. Yazmak gibi bir zorunluluğumuz yoktur ancak daha profesyonel bir paket için gereklidir. Bu, paketinizin güvenilirliğini de önemli ölçüde etkilemektedir. 

PHP ile test yazmak için bir çok araç bulunmaktadır. Bunlardan en önemlileri [PHPUnit](https://phpunit.de), [PHPSpec](http://www.phpspec.net) ve [CodeCeption](http://codeception.com) araçlarıdır. Siz hepsini inceleyip, ihtiyaçlarınıza göre ([Birim Test](http://tr.wikipedia.org/wiki/Birim_testi), [Entegreasyon Testi](http://en.wikipedia.org/wiki/Integration_testing), [Fonksiyonel Test](http://en.wikipedia.org/wiki/Functional_testing)) en idealini projeniz için kullanabilirsiniz. Biz örneğimiz için PHPUnit'i kullanacağız.   

### PHPUnit'in Projeye Dahil Edilmesi

PHPUnit kurulumu iki aşamadan oluşmaktadır. Öncelikle PHPUnit'i genel olarak sistemimize kurmamız gerekmektedir;

```
$ wget https://phar.phpunit.de/phpunit.phar
$ chmod +x phpunit.phar
$ sudo mv phpunit.phar /usr/local/bin/phpunit
$ phpunit --version
```

Bu işlemlerden sonra konsol üzerinde aşağıdaki çıktıyı görebilmeniz gerekmektedir;

```
PHPUnit 4.4.1 by Sebastian Bergmann.
```

Artık PHPUnit sistemimizde kullanılabilir haldedir. PHPUnit ile test geliştirmek için, yazdığımız testlerin PHPUnit içerisinde bulunan sınıflardan genişletilmesi gerekmektedir. Bu nedenle PHPUnit'i projemize de dahil etmek zorundayız. Bu işlemi ***composer.json*** dosyasını aşağıdaki gibi düzenleyerek gerçekleştirebiliriz;

```json
{
    "require-dev": {
        "phpunit/phpunit": "4.4.*"
    }
}
```

Bu düzenleme işleminden sonra aşağıdaki komutu çalıştırarak PHPUnit'in proje dizinimize kurulmasını sağlayacağız;

```
$ composer update
```
Bu işlemler PHPUnit'i projemizde kullanılabilir hale getirmiştir. 

W> ## Uyarı
W>
W> Eğer PHPUnit kurulumunda sorun yaşıyorsanız, [kendi dökümanından](https://phpunit.de/manual/current/en/installation.html) yararlanabilirsiniz. 

### PHPUnit Yapılandırması

`phpunit` komutuna yazdığımız testleri yolunu belirterek testleri çalıştırabiliriz. Ancak öncelikle bu işlemi her defasında tekrar etmemek amacıyla, paketimizin kök dizinine `phpunit.xml` adında bir yapılandırma dosyası oluşturacağız ve içerisini aşağıdaki gibi düzenleyerek kaydedeceğiz;

```xml
<?xml version="1.0" encoding="UTF-8"?>
<phpunit bootstrap="vendor/autoload.php"
         colors="true">
    <testsuites>
        <testsuite name="Package Test Suite">
            <directory suffix=".php">./tests/</directory>
        </testsuite>
    </testsuites>
</phpunit>
```

Bu ***XML*** dosyasında öncelikle her test çalıştırıldığında otomatik olarak yüklemelerin yapılacağı dosyayı belirtiyoruz. Bu dosya `vendor/autoload.php` dosyasıdır. 

I> ## Bilgi
I>
I> Bu dosya aslında ***composer***'ın kendi kullandığı otomatik yükleme dosyasıdır. Bu dosya aracılığı ile **autoload** bölümünde belirtilen namespace ya da dizin/dosyalar otomatik olarak yüklenecektir. 

İkinci olarak, testlerimizin barındırıldığı dizinin `tests` dizini olduğunu PHPUnit'e söylemekteyiz. Bundan sonra kök dizinimizde her `phpunit` komutu çalıştırıldığında, testlerimiz ***tests*** klasörü altında aranacaktır. Bu işlemlerden sonra `phpunit` komutunun çıktısı aşağıdaki gibi olmalıdır;

```
Time: 38 ms, Memory: 2.00Mb

No tests executed!
```

### Test Sınıfının Oluşturulması

Öncelikle ***tests*** dizini altında `SampleTest.php` ismiyle bir dosya oluşturarak, dosyayı aşağıdaki gibi düzenleyelim;

```php
class SampleTest extends PHPUnit_Framework_TestCase {
    
    public function testSample()
    {
        $this->assertTrue(true);
    }

}
```

Bu kodlar ile basit bir test sınıfı oluşturmuş oluyoruz. Test sınıfımızın adı **SampleTest** ve bu sınıf PHPUnit'in bize sağladığı **PHPUnit_Framework_TestCase** sınıfından genişletiliyor.

Test sınıfımızın içerisinde bir **testSample** metodu bulunuyor. Bu metot testimizi yazacağımız bölümü barındıracaktır. Şimdilik ***PHPUnit***'in çalışmasını kontrol açısından, **true** değerinin **true** olup olmadığını kontrol eden bir test hazırladım. Dosyayı kaydettikten sonra `phpunit` komutunu çalıştırarak aşağıdaki sonucu yeşil renkte görebilirsiniz;

```
OK (1 test, 1 assertion)
```

Bu demek oluyor ki testimiz sorunsuz bir şekilde çalışıyor.

### Testimizin Yazılması

Daha önce bir dökümantasyon oluşturduğumuz için testimizi yazmak çok daha kolay olacaktır. Test işlemini gerçekleştireceğimiz metodumuzu, dökümanımızdaki gibi düzenliyoruz;

```php
public function testSample()
{
    $example = new Ozziest\Example\Example;
    $title = $example->title('bu örnek bir başlıktır');
    $this->assertEquals($title, 'Bu Örnek Bir Başlıktır');
}
```

Burada yaptığımız; sınıfımızı kullanarak, beklediğimiz sonucu sınıfın bizi gönderdiği sonuçlar karşılaştırmaktır. Ancak testimizi çalıştırdığınız an bir hata ile karşılaşacaksınız. Çünkü testimiz hazır olmasına rağmen, henüz ortada böyle bir sınıf bulunmamaktadır. 

Bundan sonra yapmamız gereken; testimizin tekrar **yeşil** renge dönmesini sağlayan kodları yazmaktır.

## Paketin Geliştirilmesi

Bu bölüm altında paket geliştirilecektir.

### Bağımlılık Tanımlaması

Bu bölüm altında test araçlarının paket bağımlılıklarına eklenmesi anlatılacaktır.

## Versiyon Numarası

Bu bölüm altında versiyon numarası verme işlemi gerçekleştirilecektir.

## Packagist İle Yayınlama

Bu bölüm altına paketimizin nasıl yayınlanacağı anlatılacaktır.

## Kurulum Denemesi

Bu bölüm altında paketimizin kurulum ve kullanımı test edilecektir.


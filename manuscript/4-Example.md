# Örnek Bir Paket Oluşturulması

## 1. Amaç

Bu bölüm altında paketin ilk oluşturulması aşamasından başlanarak, yayınlanma aşamasına kadar geçen süreçler adım adım örneklenecektir.

Örneğimizde kullanacağımız paketin amacı, temel Türkçe dil bilgisi kurallarını verilen metin üzerinde uygulanmasıdır. Örneğin;

***"bu bir örnek başlıktır"*** 

olarak verilen mesajı aşağıdaki başlık formatına uygulayan bir metotdumuz olacaktır;

***"Bu Bir Örnek Başlıktır"***

I> ## Bilgi
I>
I> Bu özelliği belirlemek tamamen bizim elimizde. Amacımız iş yapan bir paket geliştirmek yerine paket geliştirmeyi anlatmak olduğundan, örneğimizde kullancağımız paketin çok az bir işi yapıyor olması işimize gelmektedir.

## 2. Temel Yapılandırma 

Temel olarak paketimizin hangi işi yapacağına karar verdikten sonra, paket ile ilgili genel ayarlamaları yapmamız gerekmektedir. Bu adımlar şöyledir;

* Paket Adının Belirlenmesi
* Paketin Deposunun Oluşturulması
* Paketin Yerele Alınması
* Composer Yapılandırması
* İlk Commit

### 2.1. Paket Adının Belirlenmesi

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

### 2.2. Paketin Deposunun Oluşturulması

Bir sonraki adımımız paketimizi nerede muhafaza edeceğimizin belirlenmesidir. Biz herkese açık, [MIT Lisansı](http://opensource.org/licenses/MIT)'na sahip bir paket geliştirmek istiyoruz. Bu nedenlerden ötürü GitHub hesabımda **example** isimli bir depo (repo) oluşturacağım. 

Siz de kendi hesabınız üzerinden adımları birebir uygulayabilirsiniz.

Bunun için öncelikle ***GitHub*** üzerinde oturum açmanız gerekmektedir. Daha sonra sağ üstteki kullanıcı adınızın hemen yanında bulunan **+** butonuna tıklayarak, **"New Repository"** menüsü ile yeni depo oluşturma sayfasına gidebilirsiniz. 

Açılan form üzerinde **Repository Name** alanına deponuzun adını yazdıktan sonra **Create Repository** butonuna tıklayarak reponuzu oluşturabilirsiniz. 

I> ## Bilgi
I> 
I> Benim örneğimde kullancağım repoya [link](https://github.com/ozziest/example) aracılığı ulaşabilirsiniz.

### 2.3. Paketin Yerele Alınması

Paketimizi ***GitHub*** üzerinde oluşturduktan sonra, çalışmalarımızı yapmak için kendi bilgisayarımıza almamız gerekmektedir. Bunun için paket oluşturulduktan sonra GitHub bize yardımcı olmak amacıyla örnek kodlar göstermektedir. Bu kodlar versiyon kontrol sistemi ***(Git)*** komutlarından oluşmaktadır. Git için hazırlanan kullanıcı arayüzleri olsa da, biz işlemlerimizi ***konsol (terminal)*** üzerinden gerçekleştireceğiz. 

Aşağıdaki komutu kendi paketinize göre düzenleyerek konsol üzerinde çalıştırınız;

```
$ git clone https://github.com/kullanici-adi/paket-adi.git
```

Yukarıdaki komutta **kullanici-adi** yazan bölüme sizin kullanıcı adınız, **paket-adi** yazan bölüme ise sizin paket adınız gelmelidir. 

Komut çalıştırıldıktan sonra ilgili depo kendi çalışma ortamınıza indirilecektir. Aşağıdaki komut ile deponuz için ayrı bir klasör oluşturulduğunu görebilirsiniz;

```
$ ls -all
```

### 2.4. Composer Yapılandırması

Depomuzu kendi bilgisayarımıza aldıktan sonra, depomuzun klasörünün içerisine girip aşağıdaki komutu çalıştırıyoruz ve ***composer*** yapılandırma dosyasını oluşturuyoruz;

```
$ composer init
```

Bu komut çalıştırıldıktan sonra ***composer*** bize çeşitli sorular soracaktır. Bunlar paket adı (yayıncı/paket adı), paket açıklaması vb. gibi sorulardır. Bu sorulara uygun cevapları yazarak yapılandırmayı tanımlayabilirsiniz.

### 2.5. İlk Commit

Composer yapılandırması oluşturulduktan sonra ana dizinde bir composer.json dosyası oluşacaktır. Bu işlemden sonra var olan yapılandırmamızı ***GitHub*** üzerindeki depomuza gönderilerek ilk commit işlemimiz gerçekleştirilmiş olacaktır. Bunun için aşağıdaki komutlar sırasıyla çalştırılır;

```
$ git add .
$ git commit -m "Initial Commit Message"
$ git push origin master
```

Bu işlemden sonra yaptığımız değişiklikler depomuza gönderilmiş olacaktır.

## 3. Döküman Oluşturulması

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

## 4. Test Yazılması

Test yazımı ne yazık ki bir çoğumuzun uymadığı bir husustur. Yazmak gibi bir zorunluluğumuz yoktur ancak daha profesyonel bir paket için gereklidir. Bu, paketinizin güvenilirliğini de önemli ölçüde etkilemektedir. 

PHP ile test yazmak için bir çok araç bulunmaktadır. Bunlardan en önemlileri [PHPUnit](https://phpunit.de), [PHPSpec](http://www.phpspec.net) ve [CodeCeption](http://codeception.com) araçlarıdır. Siz hepsini inceleyip, ihtiyaçlarınıza göre ([Birim Test](http://tr.wikipedia.org/wiki/Birim_testi), [Entegreasyon Testi](http://en.wikipedia.org/wiki/Integration_testing), [Fonksiyonel Test](http://en.wikipedia.org/wiki/Functional_testing)) en idealini projeniz için kullanabilirsiniz. Biz örneğimiz için PHPUnit'i kullanacağız.   

### 4.1. PHPUnit'in Projeye Dahil Edilmesi

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

### 4.2. PHPUnit Yapılandırması

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

### 4.3. Test Sınıfının Oluşturulması

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

### 4.4. Testimizin Yazılması

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

## 5. Paketin Geliştirilmesi

Bu bölümde daha önce yazdığımız testi geçen paketimizin kodlarını geliştireceğiz. 

Öncelikle `src` dizinimizin altında `Ozziest\Example` klasörleri oluşturuyoruz.

```
├── src/
│   ├── Ozzziest
│   │   ├── Example
```

Daha sorna `Example` klasörü içerisine `Example.php` dosyası oluşturarak, içerisini aşağıdaki gibi dolduruyoruz.

```php
namespace Ozziest\Example;

class Example {

    public function title($text)
    {
        
    }

}
```

Bu işlemden sonra, işi gerçekleştirecek asıl sınıfımızı ve metodumuzu oluşturmuş olduk. Ancak bu adımda testimizi çalıştırdığımızda yine sınıfımızın bulunamadığını göreceksiniz;

```
$ phpunit

PHP Fatal error:  Class 'Ozziest\Example\Example' not found in ...
```

Bunun nedeni otomatik yükleme ayarlarını henüz yapmamış olmamızdır. Diğer bir deyişle; henüz ***Example.php*** dosyamız testimiz için include edilmemiştir.

Otomatik yükleme işlemi için ***composer.json*** dosyamızı açarak içerisini aşağıdaki eklemeyi yapıyoruz;

```json
"autoload": {
    "psr-4": {
        "Ozziest\\Example\\": "src/Ozziest/Example"
    }
}
```

Bu eklemeyle birlikte ***composer***'a ilgili namespace'in hangi dizin altında aranması gerektiğini söylemiş oluyoruz. Bu işlemden sonra komut satırında aşağıdaki komutu çalıştırarak, otomatik yüklemelerin yeniden ayarlanması gerektiğini ***composer***'a söylemiş oluyoruz;

```
$ composer dump-autoload
```

I> ## Bilgi
I>
I> Composer'ın çalışma mantığını daha iyi anlamak için `vendor/composer` dizini altındaki dosyaları inceleyebilirsiniz.

Bu işlemden sonra `phpunit` komutunu çalıştırdığınız takdirde; kırmızı renklerle ilgili metodun beklenilen sonucu vermediğini görebilirsiniz. 

Bu noktadan sonra tek yapmanız gereken, artık işi yapan komutları geliştirmektedir. Bizim amacımız gerçekten iş yapan bir paket geliştirmekten ziyade, paket geliştirmek olduğundan, sadece testi geçmemizi sağlayacak olan kodları metodumuza dahil ediyoruz;

```php
public function title($text)
{
    return trim(
        mb_convert_case(
            str_replace(
                [' I',' ı', ' İ', ' i'],
                [' I',' I',' İ',' İ'],
                $text
            ),
            MB_CASE_TITLE, 
            "UTF-8"
        )
    );
}
``` 

Bu işlemden sonra hedeflediğimiz işi yapan basit bir sınıf geliştirdiğimizi varsayabiliriz. 

I> ## Bilgi
I>
I> Yaptığınız tüm değişikliklri ***GitHub*** üzerindeki deponuza gönderdiğinizden lütfen emin olunuz.

## 6. Bağımlılık Tanımlaması

Bizim hazırladığımız paket, yalnızca tek bir işe odaklanmış bir pakettir. Bu nedenle aklınıza "Neden bu kadar basit bir iş için bu kadar uğraştık?" sorusu gelmesi son derece mantıklıdır. Ancak bizim paketimizdeki iş örnek oluşturulması amacıyla seçilmiştir. Daha çok iş yapan çok gelişmiş bir paket oluşturabilirsiniz. Örneğin [Sentry](https://github.com/cartalyst/sentry) gibi yetkilendirme ve oturum yönetimi işlemini gerçekleştiren çok büyük paketler vardır. Fakat her paketin de bu kadar kapsamlı olmasına da gerek yoktur. Küçük bir işe odaklanan, basit paketlerin olması da mümkündür. 

Bazı durumlarda paketler büyükçe bağımlı olduğu başka paketler de olabilmektedir. Bunun için ilgili bağımlılığının ***composer.json*** üzerinde tanımlanması gerekmektedir. Bu tanımlamadan sonra asıl kodlarımız için ilgili bağımlılık kullanılabilir.

## 7. Semantik Versiyonlama

Yazılım dünyasında önemli bir sorun versiyonlamadır. Bu, bazı insanlar için ticari bir kavram olabilir ama bizim için teknik bir tabirdir. Paket geliştirme ve sürdürme süresince ise kritik bir rol oynar. 

Geliştirilen birçok paket, yazılımın doğası gereği geliştirildiği gibi kalmaz. Hatalar giderilir, yeni özellikler eklenir ya da çekirdekte çok önemli değişikliker yapılabilir. 

Örneğin; bir paket geliştirirken, başka bir **A** paketini kullandığınızı varsayalım ve kendi paketinizin bir yerinde **A** paketinde bulunan ***getAttr()*** metodunu çağırıyorsunuz. Ancak zamanla **A** paketinin içeriği değişti ve bu metot kullanımdan kaldırıldı. Bu durumda sizin paketiniz çalışmaz. Paketler ***Composer*** ile otomatik olarak güncellenebildiğinden, paketinizin çalışması siz daha farkına varamadan bozulabilirdi. 

Peki bu değişime nasıl ayak uyduracağız ve paketlerin birbirleri ile uyumla çalışmasını sağlayacağız? Bu sorun uzun zaman önce çözülmüş ve **Semantik Versiyonlama** ortaya atılmıştır.

### 7.1. Değişiklik Kategorileri

Semantik Versiyonlama'da her değişiklik bir kategoriye aittir. Bu kategoriler aşağıdaki gibidir;

* Patch Güncellemeleri 
* Minor Güncellemeler
* Major Güncellemeler 

Bir paketin versiyon numaraları sırasıyla şu şekilde sıralanmaktadır;

```
major.minor.patch
// Örnek; 1.0.0
```

Yapılan güncelleme hangi kategoriye aitse, ilgili numara 1 arttırılır. 

#### 7.2. Patch Güncellemeleri

Paketimizdeki çeşitli hatalar düzeltildiğinde ilgili işlem bu kategoride değerlendirilir. Tespit edilen bir hata giderilmiş ve paketin çalışma mantığında hiçbir değişiklik olmamıştır. 

#### 7.3. Minor Güncellemeler

Paketimize yeni bir özellik eklediğimizde bu kategoride değerlendirilir. Örneğin **Cache** işlemi yapan bir paket tasarladığımızı varsayalım. Bu paket daha önce **MemCache** teknolojisi ile çalışabiliyorken daha sonradan **Redis** teknolojisi de eklenirse bu bir **minor** güncelleme olacaktır. 

W> ## Uyarı
W>
W> Anahtar kuralımız, minor değişiklikten sonra geçmişe yönelik desteğin devam etmesidir. Eğer destek devam etmiyorsa, yani paketin eski halini kullanan kodlar bundan etkilenebilirse bu bir major değişikliktir. 

#### 7.4. Major Güncellemeler

Paketimizde yapılan ve sonrasında paketin çalışmasını doğrudan etkileyen değişikliklere verilen isimdir. Örneğin var olan bir metodun kaldırılması ya da yeni bir zorunlu parametre eklenmesi gibi değişiklikler **major** güncelleme olarak adlandırılır.

Major güncellemeler pek sevilmez. Çünkü o ana kadar paketi kullanan başka projeler bundan etkilenecektir. Eğer bir major güncelleme olursa, muhtalaka bir **Upgrade Guide (Yükseltme Rehberi)** hazırlanarak, ilgili değişikliğe nasıl adapte olunacağı belgelendirilmelidir.

I> ## Bilgi 
I> 
I> Bazı durumlarda major değişiklikler o kadar büyük olur ki; eski sürümden yeni major sürüme geçmek olanaksız olur. 

### 7.5. Paketimizin Versiyonunu Belirleme

Paketimize ilk defa versiyon verirken dikkat etmemiz gereken; paketimizin kararlılığıdır. Eğer paketinizin hazır olduğunu düşünüyorsanız, doğrudan **1.0.0** versiyon numarasıyla başlatabilirsiniz. Ancak bu pek önerilen bir yöntem değildir. Paketler genellikle **0.1.0** numarasından başlarlar ve yukarıda belirtilen kurallara göre versiyon numarası güncellenir. Paket çeşitli geliştirciler tarafından test edildikten sonra artık **1.0.0** kararlı sürümüne ulaşabilir.

Biz de paketimizi başlangıç için **0.1.0** versiyon numarasıyla başlatmak istiyoruz. Bunu belirtmek için ***Git*** komutlarından yarlanacağız;

```
$ git tag 0.1.0
$ git push --tags
```

Bu komutlar çalıştırıldıktan sonra aşağıdaki çıktı size gösterilecektir;

```
To https://github.com/ozziest/example.git
 * [new tag]         0.1.0 -> 0.1.0
```

[GitHub deposu](https://github.com/ozziest/example/releases) üzerinden paketimizi incelerseniz, paketin tüm versiyon numaları burada gösterilecektir.

I> ## Bilgi
I> 
I> Yeni eklemelerden sonra versiyon numaralarının değiştirilmeleri önemlidir. Dilerseniz eski versiyon numaralarını da silebilirsiniz ancak major ve minor versiyon numaralarının silinmesi pek önerilmez. Genelde **patch** bölümünde birden fazla değişik versiyon varsa (1.0.1, 1.0.2, 1.0.3) sadece en son versiyon numarasının saklanması daha yerinde olacaktır. 

### 7.6. Composer'da Versiyon Seçimi

Composer ile bir başka paketi projenize dahil ederken aşağıdaki kullanım şeklinden yararlanabilirsiniz;

```json
{
    "require": {
        "ozziest/example": "1.*"
    }
}
```

Bu tanımlamada görüldüğü üzere; ilgili paketin **"1.*"**  sürümünün kullanılması istenmektedir. Eğer pakette major bir değişiklik olursa, **composer update** komutu çalıştırılsa bile o değişiklik alınmaz ve böylece paketi kullanan projeler major değişikliklerden etkilenmez. 

W> ## Uyarı
W> 
W> Eğer tanımlama yaparken **"1.*"** yerine  **"dev-master"** yazılırsa, ilgili paketin sürüm numarasına dikkat edilmeden son hali kullanılacaktır. Bu kullanımı yukarıdaki sebeplerden ötürü önerilmemektedir.

Eğer yeni özellikleri de istemiyor ve sadece var olan hataların güncellemelerini almak istiyorsak; aşağıdaki gibi bir kullanım uygun olacaktır;

```json
{
    "require": {
        "ozziest/example": "1.5.*"
    }
}
```

## 8. Packagist İle Yayınlama

Şuana kadar yaptığımız işlemler çalışan bir paketin kodlarını yayınlamaktan ibarettir. Paketimizin ***composer*** ile kurulabilmesi için [Packagist](https://packagist.org) üzerinden paketimizi duyurmamız gerekecektir.

I> ## Bilgi
I>
I> Packagist, ***composer*** için oluşturulmuş bir paket deposu ya da diğer bir değişle paket arşividir. 

### 8.1 Packagist Hesabı Oluşturma

Bunun için öncelikle ***Packagist*** üzerinden bir hesap oluşturmanız gerekmektedir. 

I> ## Uyarı
I>
I> ***Packagist*** hesabınızında kullanacağınız kullanıcı adının, ***GitHub*** hesabınızda kullandığınız kullanıcı adıyla aynı olması daha şık duracaktır. 

### 8.2 Paket Gönderme

***Packagist*** üzerinde paketinizi yanıtmak için yeşil renkli **"Submit Package"** butonuna tıklayarak paket gönderme formuna ulaşmanız gerekmektedir.

Açılan form üzerinde paketinizin yer aldığı deponun linki sizden istenilecektir. Paketinizin GitHub üzerinde muhafaza edildiği deponun linkini bu bölüme yazarak **"Check"** butonuna tıklayabilirsiniz. 

I> ## Uyarı
I>
I> Eğer paketinizin adına benzer başka paketler varsa, ***Packagist*** sizi uyaracaktır. Bu uyarıyı dikkate almayabilirsiniz. 

Kontrol işleminden sonra form üzerinde **"Submit"** butonu görünecektir. Butona tıklayarak paket tanıtma işlemini sonlandırabilirsiniz. Paket tanıtım işlemi sonlandırıldıktan sonra paketiniz için oluşturulan sayfaya yönlendirileceksiniz. Bu bölümde paketinizin detaylarını (Versiyonlar, lisans bilgisi, yazarlar, bağımlılıklar vs.) görebilirsiniz.

### 8.3 Otomatik Paket Güncelleme

Varsayalım paketinize yeni güncellemeler gönderdiniz ve bu güncellemelerden sonra paketinizin yeni bir versiyon numarası oldu. Bu bilgi otomatik olarak ***Packagist***'e ulaşmaz. Bu durumda ya her güncellemeden sonra paket sayfasına gelerek **"Force Update"** butonu aracılığı ile paketin son halinin kontrol edilmesini isteyeceksiniz ya da bu işlemi otomatikleştireceksiniz. 

Otomatikleştirme işlemi için her güncellemeden sonra ***GitHub***'dan ***Packagist***'in tetiklenmesini sağlayacağız. Bu tetikleme işlemine **Services** adı verilmektedir. 

I> ## Bilgi
I>
I> Sadece ***Packagist*** için değil bir çok farklı servis için tetikleme işlemi tanımlayabilir, dilerseniz kendinize özet tetiklemeler yazabilirsiniz. (Örneğin her yeni versiyondan sonra otomatik tweet gönderilmesi gibi.) Tüm bu işlemler deponuzun ayarlar bölümünde ***Webhooks&Services*** sekmesi altında yer almaktadır. 

Tetikleme işlemlerinde kullanılmak üzere ***Packagist*** size bir **API Token (API Anahtarı)**vermektedir. Bu anahtarı görüntülemek için [bu linkteki](https://packagist.org/profile) profil sayfanızı ziyaret edebilirsiniz. Profil sayfanızda **Show API Token** linkine tıklayarak mevcut size özel olarak oluşturulan anahtarı öğrenebilirsiniz.

Anahtarımızı öğrendikten sonra ***GitHub*** üzerindeki depomuza giderek, **Settings** linkine tıklayalım. Açılan ayarlar bölümünden **Webhooks&Services** sekmesine ulaşabiliriz. 

Açılan bölümde **Services** kutucuğunda yer alan **Add Service** butonuna tıklayarak, listelenen servisler arasından ***Packagist*** servisini seçelim. Bu işlemden sonra ***Packagist*** servisine özel tanımlama ekranına yönlendirileceksiniz. 

Bu ekranda sizden 3 temel bilgi istenilecektir;

* ***Packagist*** kullanıcı adınız
* API Token
* Domain

Gerekli bilgileri ilgili alanlara yazınız ve **Add Service** butonuna tıklayarak servis oluşturma işleminin tamamlanacaktır. Bundan sonra yapılacak güncellemelerden sonra otomatik olarak ***Packagist*** haberdar edilecektir. 

I> ## Bilgi
I>
I> Domain alanına ***https://packagist.org*** değerini yazabilirsiniz.

## 9. Kurulum Denemesi

Artık yayınlanan ve ***composer*** ile kurulabilen bir pakete sahibiz. Bunu denememiz bizim için çok kolay. 

Öncelikl bilgisayarımızda boş bir dizin oluşturarak, dizin içerisine aşağıdaki gibi bir `composer.json` dosyası oluşturabiliriz;

```json
{
    "require": {
        "ozziest/example": "dev-master"
    }    
}
```

Dosya kaydedildikten sonra aynı dizinde aşağıdaki komutu çalıştırarak ***composer***'dan bağımlılıkları kurmasını isteyebiliriz;

```
$ composer install
```

Eğer daha önceki tüm adımlar sorunsuz bir şekilde tamamlandıysa aşağıdaki çıktıyı göreceksiniz;

```
Loading composer repositories with package information
Installing dependencies (including require-dev)
  - Installing ozziest/example (dev-master 4fe5a33)
    Cloning 4fe5a333c591d6de91552789b3afa1997d66d1cc

Writing lock file
Generating autoload files
```


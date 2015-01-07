# Genel Bakış

PHP için hazırlanan bir paket genel olarak bir PHP yazılımından farksızdır. Buna rağmen paketlerin genel amacı; hızlı bir şekilde ve koda girmeksizin başka projelerde kullanılabilmesidir. Bu bölümde genel kabul görmüş paket oluşturma kurallarına değinilecektir.

## Dizin Yapısı

Aşağıda temel bir paketin dizin yapısı görülmektedir;

```
├── src/
│   ├── Ozzziest
│   │   ├── Example
├── tests/
├── composer.json
├── README.md
```

* `composer.json`: Bu dosya bağımlılık yöneticisine (Composer) paketimizi tanıtan dosyadır.
* `src/`: Asıl dosyalarımızın bulunacağı dizindir. 
* `tests`: Paketimizin çalışmasını test eden kodlarımız da bu bölüm altında yer almaktadır.
* `README.md`: Paket hakkında genel bilgiler veren, Markdown fomatında hazırlanmış bir ön dökümandır. Paket hakkında oluşturulacak döküman ufaksa sadece bu dosyaya yazılır. Eğer daha geniş bir döküman varsa ayrı bir klasör altında dökümanlar toparlanabilir.

I> ## Bilgi
I> 
I> Genelde kabul edilen kullanım şekli bu olmasına rağmen kesin bir kural değildir. Dolayısıyla kendi paketinizde dilediğiniz dizin yapısını kullanabilirsiniz. Ancak sizin paketinize katkı yapmak isteyecek bir geliştiricinin kafasını karıştırmaktan öteye gitmiş olmazsınız. Bu nedenle genel kabullere uymak yararlıdır.

## Kod Yapısı

Bugüne kadar hiç fonksiyonlardan oluşan bir paket kullanmadım. Daha çok tüm paketler bir sınıf yapısına sahip olmaktadır ve muhakkar bir namespace kullanmaktadır. Global Scope üzerinde herhangi bir sınıf tanımlamak pek hoş karşılanan bir durum değildir. Yukarıdaki klasör yapısında aşağıdaki gibi bir namespace kullanılmış olması muhtemeldir;

```php
namespace Ozziest\Example;
```

## Autoload

Composer'ın en güzel yanlarından biri de autoload (Otomatik Yükleme) özelliğidir. ***composer.json*** içerisinde tanımlayacağınızı dizinleri otomatik olarak yükletebilirsiniz. Böylelikle paketinizi kullanan kullanıcılar `include` komutu ile uğraşmayacaklardır. 

`composer.json` içerisinde 4 farklı türde autoload tanımlaması desteklenmektedir;

* PSR-0
* PSR-4
* classmap
* files

### PSR-0 

PSR-0 standartları kullanılarak aşağıdaki gibi bir otomatik yükleme kaydı tanımlanabilir;

```json
{
    "autoload": {
        "psr-0": {
            "Ozziest\\Example\\": "src/"
        }
    }
}
```

Bu tanımlama ile `Ozziest\Example` namespace'imizin nerede aranması gerektiğini Composer'a söylemiş olmaktayız.

I> ## Uyarı
I> 
I> [PSR-0](http://www.php-fig.org/psr/psr-0/) **PHP Otomatik Yükleme Standardı**'dır. Ancak bu standart artık önerilmemekte ve bunun yerine PSR-4 standardı önerilmektedir. 

### PSR-4

PSR-4 standartları kullanılarak aşağıdaki gibi bir otomatik yükleme kaydı tanımlanabilir;

```json
{
    "autoload": {
        "psr-4": {
            "Ozziest\\Example\\": "src/"
        }
    }
}
```

Bu tanımlama ile `Ozziest\Example` namespace'imizin nerede aranması gerektiğini Composer'a söylemiş olmaktayız.

### Classmap

Classmap, sadece sınıf barındıran ve herhangi bir namespace'e sahip olmayan klasörlerin otomatik olarak yüklenmesi için daha uygundur.

```json
{
    "autoload": {
        "classmap": ["src/", "lib/", "Something.php"]
    }
}
``` 

### Files

Files, sadece sınıf barındıran ve herhangi bir namespace'e sahip olmayan tek bir dosyanın otomatik olarak yüklenmesi istenildiğinde daha uygundur.

```json
{
    "autoload": {
        "files": ["src/MyLibrary/functions.php"]
    }
}
``` 

## Bağımlılık Yönetimi

Geliştirdiğimiz paketin hiçbir başka pakete bağımlı olmadan, kendi başına çalışabilmesi en idealidir. Ancak bu çoğu zaman mümkün değildir ve paketler başka paketlerle birlikte çalışma ihtiyacı hissedebilirler. Örneğin [Symfony/Yaml](https://github.com/symfony/Yaml) kendi başına çalışabilen bir paketken, [PHPUnit](https://github.com/sebastianbergmann/phpunit) çalışmak için başka paketlere bağımlıdır. Tüm bu bağımlılıkların hepsi `composer.json` dosyası içerisinde tanımlanmalıdır. Aşağıda PHPUnit paketinin bağımlılıklarının yazıldığı bölüm görülmektedir;

```json
{
    "require": {
        "php": ">=5.3.3",
        "phpunit/php-file-iterator": "~1.3",
        "phpunit/php-text-template": "~1.2",
        "phpunit/php-code-coverage": "~2.0",
        "phpunit/php-timer": "~1.0",
        "phpunit/phpunit-mock-objects": "~2.3",
        "phpspec/prophecy": "~1.3.1",
        "symfony/yaml": "~2.1|~3.0",
        "sebastian/comparator": "~1.1",
        "sebastian/diff": "~1.2",
        "sebastian/environment": "~1.2",
        "sebastian/exporter": "~1.0",
        "sebastian/global-state": "~1.0",
        "sebastian/version": "~1.0",
        "ext-dom": "*",
        "ext-json": "*",
        "ext-pcre": "*",
        "ext-reflection": "*",
        "ext-spl": "*"
    }
}
```

W> ## Uyarı
W> 
W> Eğer bir paketten herhangi bir özelliği kendi paketimizde kullandıysak ve bunu ***composer.json*** dosyasında tanımlamadıysak ne olur? Paketimiz yüklendiğinde bağımlı olunan paket yüklenmez ve çalışma anında bağımlı olunan paket bulunamadığı için bir hata ile karşılaşılır.

## Versiyon Kontrol Sistemi

Versiyon kontrol sistemleri geliştirdiğimiz projelerin takibinin kolaylaştırılmasını sağlayan araçlardır. Aynı anda birden fazla özellik geliştirme, hangi özelliğin hangi sürümlerde olduğunu takip edebilme, ekip halinde çalışma vb. gibi çok sayıda fayda sağlamaktadır. 

W> ## Uyarı
W> 
W> Versiyon kontrol sistemleri bilinen aksin sadece ekip çalışmasının olduğu yerde değil, tek kişi tarafından geliştirilen projeler için de bir zorunluluktur. 

Paket geliştirme sürecinde ise versiyon kontrol sistemleri kullanılmak zorundadır. Geliştirdiğiniz paketin anlık sürümü, yeni özelliklerin hangi sürümlerle çıkacağı vb. gibi nedenlerden ötürü bu bir zorunluluk halini almıştır.

Şuanda bir çok versiyon kontrol sistemi olsa da ağırlıklı olarak **[Git](http://git-scm.com)** ve **[SVN](http://tortoisesvn.net)** tercih edilmektedir. Yine bir çok geliştirici de kullanım kolaylığı açısından ***Git*** önermektedir. Bu nedenlerden ötürü ben de geliştirdiğiniz paketlerde ***Git*** kullanmanızı tavsiye etmekteyim.

I> ## Bilgi
I>
I> İlerleyen bölümlerde versiyon kontrol sisteminin paketlerde kullanılmasıyla ilgili ipuçları verilecektir.

## GitHub ve Alternatifleri

Paket geliştirme sürecinde versiyon kontrol sistemi kullanarak kodlarınızı bir yerde muhafaza etmek zorundasınızdır. Bu genellikle kendi bilgisayarınız olmaz. Çünkü amacımız dileyen herkesin dilediği anda paketimize ulaşabilmesidir. Bu nedenle bu iş için tasarlanmış servislerden yararlanırız. Dünya genelinde bu iş için geliştirilmiş iki büyük site vardır: **GitHub** ve **BitBucket**.

I> ## Bilgi
I>
I> Eğer gerekli olduğunu düşünürseniz kendi sunucularınızı da versiyon kontrol sistemi sunucusu olarak yapılandırabilir ve kodlarınızı kendi sunucularınızda muhafaza edebilirsiniz. Ancak bu konu e-kitap kapsamı dışında olduğundan, e-kitap boyunca değinilmeyecektir.

Her iki siteyi kullanarak, kodlarınızı versiyon kontrol sistmei aracılığı ile muhafaza edebilirsiniz. Ancak ***GitHub*** çok fazla sebepten ötürü daha çok tercih edilmektedir. ***BitBucket***'ın en büyük avantajı ise ücretsiz **Gizli Depo (Private Repository)** oluşturulmasına izin vermesidir. ***GitHub***'da bunu yapmak istediğinizde ücret ödemek zorunda kalırsınız.

Biz e-kitap içerisinde örnekleyeceğimiz uygulamaları ***GitHub*** üzerinde **Açık Depo (Public Repository)** olarak muhafaza edeceğiz.

I> ## Bilgi
I> 
I> Eğer geliştirdiğiniz paketi dileyen herkesin kullanımına sunacaksanız; paketinizi açık kaynak lisansları ile lisanslamanız gerekmektedir. Bu lisansların gerekliliği de; kaynak kodlarınızın herkesin ulaşılabileceği bir şekilde yayınlanmasıdır. Bu nedenle gizli depolar sadece kendiniz için hazırladığınız paketler için kullanılabilir.



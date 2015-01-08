# Paket/Bağımlılık Yönetimi

Daha sürdürülebilir projeler geliştirebilmek için uygulamamızın iskeletini parçalamak ve bu parçaları kullanmak akıllıca bir yoldur. Ancak bu parçaları ayrı ayrı versiyonlamak ve birbirleri ile uyumlu bir şekilde kullanabilmek için mutlaka bir paket yöneticisine ve versiyon kontrol sistemine ihtiyaç duyacaksaınız.

Bana modern PHP dünyasında hangi teknolojinin zaruri olması gerektiğini sorsanız; yukarıdaki paragraftaki nedenten ötürü cevabım **Composer** olacaktır. Composer; PHP ile geliştirilen paketlerin yönetimini, hızlıca projenize paket eklemeyi ve kaldırmayı sağlayan bir ***bağımlılık yöneticisidir***. Özellikle projenizde kullandığınız paketlerin güncellemesinde size sağlayacağı kolaylık ve zaman tasarrufu, kendisini proje geliştirme süreçlerinde çok önemli bir araç haline getirmektedir.

## 1. Kurulum

Composer'ı mevcut projenizde ya da yeni bir paket geliştirirken kullanmanız için öncelikle bilgisayarınızda Composer'ın kurulu olması gerekmektedir. Aşağıdaki satırları konsol üzerinde çalıştırarak Composer kurulumunu gerçekleştirebilirsiniz;

```
$ curl -sS https://getcomposer.org/installer | php
$ mv composer.phar /usr/local/bin/composer
```

Yukarıdaki komutun ilk satırı Composer'ı bilgisayarınıza indirmek, ikinci satırı da her yerden ulaşılabilir hale getirmek için kullanılmaktadır. Bu aşamalardan herhangi bir dizinde aşağıdaki komutla Composer kurulumunu test edebilirsiniz;

```
$ composer -v
```

## 2. Yapılandırma Dosyası (composer.json)

Composer ile paket/bağımlılık  yönetimi gerçekleştirmek için proje dizininde bir yapılandırma dosyanızın olması gerekmektedir. Bu yapılandırma dosyası ***JSON*** formatında olmalıdır. Bu yapılandırma dosyasının adı genelde `composer.json` olmaktadır ve bu dosyayı  el yordamı ile ya da konsol üzerinden doğrudan composer'ın kendisine hazırlattırabilirsiniz. 

Aşağıdaki örnek bir yapılandırma dosyası gösterilmektedir.

```json
{
    "name": "ozziest/example",
    "description": "Example PHP Package",
    "authors": [
        {
            "name": "Özgür Adem Işıklı",
            "email": "i.ozguradem@gmail.com"
        }
    ],
    "minimum-stability": "stable",
    "autoload": {
        "classmap": [
            "libs"
        ],
        "psr-0": {
            "Ozziest\\Example": "src"
        }
    },    
    "require": {
        "philo/laravel-blade": "2.*"
    },
    "require-dev": {
        "phpunit/phpunit": "4.3.*"
    }    
}
```
Yukarıda temel bir Composer yapılandırma dosyasında en çok karşılaşılan bilgiler görülmektedir. Bu parametrelerin neler olduğunu özetlemeye çalışalım;

* `name`: Composer paketinizin adı bu alanda saklanır. Bu isim **"/"** karakteriyle iki bölüme ayrılmıştır. Dünya üzerinde binlerce paket olabildiğinden, paketlerin birbirine karışmaması için tüm paket isimleri iki bölümden oluşmaktadır. Birinci bölüm dağıtıcı adı, ikinci bölüm paket adıdır. Yukarıdaki örnekte dağıtıcı adı benim GitHub kullanıcı adımdan oluşmaktadır. Paket adını dilediğiniz şekilde verebilirsiniz. Ancak paketiniz için çok önemli bir detayı da paket adında vurgulamanız sıkça kullanılan bir yöntemdir. Örneğin Laravel Framework'ü için bir paket geliştirdiğinizde, paketin daha kolay bulunabilmesi açısından **laravel-paket-adi** gibi bir isimlendirme daha şık duracaktır. 

* `description`: Paketin açıklamasını içermektedir. Bu açıklama ile paketiniz diğer geliştiriciler tarafından aramalarda görülebilir ve çok kısa bir şekilde paketinizin amacını özetlemektedir. Bu nedenle genelde ***İngilizce*** bir açıklama yazılması daha doğru olacaktır.  

* `authors`: Paketin geliştiricilerinin bilgilerini tutmaktadır. Zorunlu bir alan değildir ancak paket geliştiricilerine ulaşılabilmesi açısından önemlidir. 

* `minimum-stability`: Paketin kararlılığını tutan değerdir. Eğer paketiniz henüz bir paketse bu değer `stable` olmalıdır. Fakat paketiniz henüz kararlı bir sürüme ulaşmamış ise `dev`, `alpha`, `beta` vb. değerler verilebilir. Bu, paketinizi kullanacak geliştiriciler açısından oldukça önemlidir. Henüz kararlı bir sürüme ulaşmamış bir paket stabil olarak lanse edilmemelidir. Çünkü paketiniz henüz geliştirilme aşamasındayken bir başkası tarafından herhangi bir uygulamada kullanılabilir ve paketinizin neden olabileceği sorunlar yüzünden başkalarına zarar verebilirsiniz. 

* `autoload `: Otomatik olarak yüklenecek olan dizin ve Namespace tanımlamalarının yapıldığı bölümdür. Otomatik yükleme sistemini anlayabilmek için [PSR-0 Standartları](http://www.php-fig.org/psr/psr-0)'ın anlamak yararlı olacaktır. 

* `require`: Bu bölümde paketimizin/uygulamamızın bağımlı olduğu diğer paketler tanıtılmaktadır. Composer'ın asıl can alıcı noktası bu bölümdür. Hangi paketin hangi sürümünün projemizde kullanılacağı bu bölümde tanımlanmaktadır.  Require bölümünde dilediğiniz kadar paket tanımı yapabilirsiniz. Her paketin kullanılması gereken sürümünü de belirtebilir ve uygulamanızı daha stabil hale getirebilirsiniz. Eğer versiyon numaraları dikkat edilmeden kullanılırsa, paketinizin çalışması zamanla bozulabilir. 

I> ## Bilgi
I> 
I> Versiyonlama oldukça önemli bir konu olduğu için **Semantik Versiyonlama** bölümünde detaylı olarak ele alınacaktır.

* `require-dev`: Bu bölüm development aşamasında kullanılan paketler içindir. Sadece geliştirme ortamında kullanacağınız paketleri bu anahtar altında tutabilirsiniz. Böylelikle yayında olan projenizde gereksiz paketleri boşu boşuna diskte tutmak zorunda kalmazsınız. Genelde debug araçları gibi araçlar bu bölüm altında belirtilmektedir. 

### 3. Otomatik Yapılandırma

Konsol üzerinden bir yapılandırma dosyası oluşturmak için çalışacağınız dizin içerisinde aşağıdaki komutu vermeniz yeterli olacaktır. 

```bash
$ composer init 
```

Bu komuttan sonra konsol üzerinden sizden paket ile ilgili çeşitli bilgiler istenilecek ve sonrasında yapılandırma dosyası otomatik olarak oluşturulacaktır.

## 4. Bağımlılıkların Kurulması

Yukarıdaki gibi **composer.json** dosyası oluşturduktan sonra uygulamanızda kullanacağınız paketleri kurmak için dosya ile aynı dizinde aşağıdaki komutu kullanabilirsiniz;

```bash
$ composer install
```

Composer sizin için yapılandırma dosyasını okuyarak tanımladığınız paketleri bulacak ve `vendor` dizini altına yerleştirecektir. Yerleştirme yaparken **yayıncı/paket** klasör yapısını kullanacaktır. 

## 5. Bağımlılıkların Güncellenmesi 

Composer'ın asıl gücü ise paket güncellemelerinde ortaya çıkmaktadır. Projenizi geliştirmeye devam ettiğiniz herhangi bir anda, kullandığınız paketlerin son güncel hallerini kullanmak için aşağıdaki komutu yapılandırma dosyanızın olduğu dizinde çalıştırabilirsiniz; 

```bash
$ composer update
```

Composer, yapılandırma dosyasında belirttiğiniz versiyon bilgilerini dikkate alarak yeni güncellemeleri otomatik olarak yükleyecektir. 

I> ## Uyarı
I> 
I> Paket yapılandırmalarında versiyon numaları oldukça önemlidir. Eğer major sürüm numaralarına dikkat edilmezse, update işleminden sonra paketinizin çalışmasını bozacak güncellemeler gelebilir. Bu konuyu daha iyi anlamak için **Semantik Versiyonlama** bölümünü incelenmelidir.

## 6. Paket Bulma

Composer ile yayınlanan birçok paket  [Packagist](https://packagist.org) üzerinde listelenmektedir. Packagist, Composer paketlerinin listelenmesi için ana Composer ambarıdır. Packagist üzerinden arama yaparak, kullancağınız paketleri bulabilirsiniz.

I> ## Bilgi
I> 
I> Bunun yanında bazı paketler doğrudan depolandıkları yer üzerinden de kurulabilir. Bu yer genelde **GitHub** olmakla birlikte, bazen **BitBucket** da olabilmektedir. Bu nedenle GitHub üzerinde de bir arama yapmanız yararlı olabilir. 

W> ## Uyarı
W>
W> Eğer bir GitHub hesabınız yoksa, en kısa sürede kendinize bir GitHub hesabı edinmenizi öneririz. GitHub geliştiricilerin özgeçmişleridir.

Packagist üzerinde bir paketin detayı gittiğinizde, paket ile ilgili bilgiler yardımıyla paket kurulum ve kullanımını öğrenebilirsiniz.

I> ## Bilgi
I>
I> İlerleyen bölümler de Packagist üzerinden nasıl paket yayınlanacağı detaylı bir şekilde anlatılacaktır.

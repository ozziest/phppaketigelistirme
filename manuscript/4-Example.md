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

Bu komut çalıştırıldıktan sonra ***composer*** bize çeşitli sorular soracaktır. Bunlar paket adı (yayıncı/paket adı), paket açıklaması vb. gibi sorulardır.

### İlk Commit

Composer yapılandırması oluşturulduktan sonra ana dizinde bir composer.json dosyası oluşacaktır. Bu işlemden sonra var olan yapılandırmamızı ***GitHub*** üzerindeki depomuza gönderilerek ilk commit işlemimiz gerçekleştirilmiş olacaktır. Bunun için aşağıdaki komutlar sırasıyla çalştırılır;

```
$ git add .
$ git commit -m "Initial Commit Message"
$ git push origin master
```

Bu işlemden sonra yaptığımız değişikliker depomuza gönderilmiş olacaktır.

## Döküman Oluşturulması

Bu bölüm altında temel bir döküman nasıl oluşturulur anlatılacaktır.

## Test Yazılması

Bu bölüm altında test yazımı anlatılacaktır.

### Bağımlılık Tanımlaması

Bu bölüm altında test araçlarının paket bağımlılıklarına eklenmesi anlatılacaktır.

### Örnek Test Yazımı

Bu bölüm altında örnek bir test yazılacaktır.

## Paketin Geliştirilmesi

Bu bölüm altında paket geliştirilecektir.

## Repository Oluşturulması

Bu bölüm altında GitHub üzerinde boş bir repository oluşturulacaktır.

## GitHub'a Yükleme

Bu bölüm altında dosyalar repoya yüklenecektir.

## Versiyon Numarası

Bu bölüm altında versiyon numarası verme işlemi gerçekleştirilecektir.

## Packagist İle Yayınlama

Bu bölüm altına paketimizin nasıl yayınlanacağı anlatılacaktır.

## Kurulum Denemesi

Bu bölüm altında paketimizin kurulum ve kullanımı test edilecektir.


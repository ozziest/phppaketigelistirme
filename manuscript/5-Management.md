# Yönetim

Bir paket oluşturduktan ve yayınladıktan sonra, zaman içerisinde paketinizi kullanan kullanıcılardan size geri bildirimler gelecektir. Bu geri bildirimlere göre paketinize eklemeler yaparak, geliştirme safhasına devam edebilirsiniz. Biz bu bölümde, kullanıcılardan gelen bildirimleri irdeleyeceğiz.


## 1. Issues (Sorular)

**Issue** kelime manasıyla genellikle ***"Sorun"*** olarak kullanılsa da, biz bu kelimeyi anlam bakımından ***"Konu"*** olarak da ele alabiliriz. ***GitHub*** üzerinde oluşturduğunuz paket için bir ***Issue*** bölümü otomatik olarak oluşacaktır. Paketinizin ana sayfasına girdiğinizde, sağ tarafta yer alan bölüm altında ***Issues*** menüsünü görebilirsiniz. 

***Issues*** bölümü; kullanıcıların paketinizde gördüğü hataları size bildirdiği bölümdür. Ancak bunlar asla hatalarla sınırlı kalmaz. Kullanıcılar paketinizde olmayan bir özelliği de talep edebilir ya da dökümanda bulamadıkları bir kullanımı da sorabilirler. ***Issues*** bölümünün genel geçer bir kuralı yoktur. Bu bölümü paketiniz için oluşturulan bir forum gibi düşünebilirsiniz.

Siz de paketiniz için size soru soran ya da hata bildiren kullanıcılara cevap vermelisiniz. Elbette bu bir zorunluluk değildir. Ancak ben bir paketi incelerken ilk yaptığım işlerden biri; ***Issues*** bölümünü değerlendirmektir. Eğer aylar geçmesine rağmen cevap verilmeyen başlıklar görürsem, o pakete çok fazla güvenmem. Çünkü bu; paketin mevcut halinde bir sorun yaşadığımda paket geliştiricilerinin bana destek vermekte yetersiz olacağı manasına gelir ve kimse kendisini kör bir kuyuya atmak istemez. 

I> ## Bilgi 
I>
I> ***Issues*** bölümünde kullanılan ve benim önereceğim dil İngilizce'dir. Ancak duruma göre Türkçe kullanılmasının da bir sakıncası olmayabilir. Bu tamamen sizin paketinizin hedef kitlesiyle alakalıdır. Bu duruma en iyi örnek [arguman.org](http://arguman.org)'un deposunun [Issues](https://github.com/arguman/arguman.org/issues) bölümü olabilir;


### 1.1. Etiketleme (Labels)

Yeni bir ***issue*** geldiğinde ilk yapılması gereken, ilgili başlığın etiketlenmesidir. Bunun aşağdaki gibi yararları bulunmaktadır;

* Issues yönetiminin daha anlaşılır olması
* Geliştirme planlarınız için yardımcı olması 
* Paketinizi inceleyen kullanıcılara hata oranları hakkında bilgi vermesi

Etiketlere göre başlıkları süzmek için **Labels** filtresini kullanabilirsiniz. **Labels** filtresi varsayılan olarak bazı değerleri içerse de, siz bunların yanına başka etiketler de ekleyebilirsiniz. Biz bu bölümde, standart etiketleri açıklayacağız;

* Bug: Açılan başlık bir hatayı belirtiyorsa bu etiket seçilir. 
* Duplicate (Kopya): Başlık, bir başka başlığın kopyasıysa bu etiket seçilir ve ilgili başlığa, kopyası olan başlığın linki verilir. 
* Enhancement (Yeni Özellik): Açılan başlık olmayan bir özellik tavsiye ediyorsa bu etiket kullanılır.
* Help Wanted (Yardım Çağrısı): Başlık bir konuda yardım talep ediyorsa bu etiket kullanılır.
* Invalid (Geçersiz): Başlık paketle alakasızsa bu etiket kullanılabilir. Ancak neden geçersiz sayıldığı da başlığın altına yorumlanmalıdır. 
* Question (Soru): Paket hakkında bir soru soruluyorsa bu etiket seçilir.

### 1.2. Cevaplama 

Açılan her ***issue*** cevaplanmalıdır ve bu cevaplar oldukça kısa bir süre içerisinde verilmeye çalışılmalıdır. Çünkü genellikle her yolu deneyen ama çözüm bulamayan geliştiriciler son çare olarak paket geliştiricilerine danışırlar ve bizim de paketimizi kullanan geliştiricileri bekletmemiz etik olmayacaktır. Ayrıca verilen cevaplar basit ve anlaşılır olmalı, duruma göre harici linklerle de desteklenmelidir. 

#### 1.3. Başlığı Kapatma

Cevap verilen başlıklarda eğer kullanıcının aradığı cevabın bulunduğunu düşünüyorsanız başlığı cevap verdiğiniz anda kapatabilirsiniz. Kullanıcılar eğer tatmim olmamışlarsa başlığı yeniden açabilirler ve yeni sorularını sizlere yönetebilirler. 

Hata ile ilgili başlıklar diğerlerinden biraz farklıdır ve hata çözülmeden kapatılmamalıdır. Çünkü bir hata başlığının kapatılması, hatanın çözüldüğünü cevap olarak olarak başlığı açana iletmek demektir. Bu hususa özen gösterilmelidir ve hata ile ilgili düzeltme yapıldıktan sonra başlık kapatılmalıdır.

Hata ile ilgili düzeltme yapıldığında, commit anında başlığı kapatmak mümkündür. Bunun için aşağıdaki gibi bir commit mesajı yazılmalıdır;

```
$ git commit -m "Bug fix: #13"
```

Bu komit mesajında `#` karekterinden sonra gelen ilgili başlığın numarasıdır (issue no) ve bu commit gönderildikten sonra ilgili başlık otomatik olarak kapatılacaktır. Bu örneği daha detaylı anlamak için ***arguman.org*** deposuna gönderilen [bu commit](https://github.com/arguman/arguman.org/commit/848c4dcc8e3850e2cd925caa281079956aa9361e)'i inceleyebilirsiniz.


## 2. Milestones (Kilometre Taşları)

Bu kavram bir miktar **Issues** bölümüyle ilgilidir. ***Milestones***; en genel tabiriyle planladığınız yeni versiyonları belirtmektedir. Dilediğiniz kadar yeni versiyon planı tanımlayabilirsiniz. 

I> ## Bilgi 
I> 
I> Yeni ***Milestones*** tanımlaması için **Issues** bölümü altında bulunan **Milestones** sekmesini kullanabilirsiniz.

***Issues*** bölümünde, ***Yeni Özellik (Enhancement)*** taleplerinden bahsetmiştik. Milestones daha çok bu tür issue bildirimleri için kullanılmaktadır. Kullanıcının istediği yeni özelliğin hangi sürümde kullanılabilir olduğunu planlar ve ilgili talebi bir versiyonla ilişkilendirebilirsiniz.

I> ## Bilgi 
I> 
I> İlişkilendirme işlemi için; ilgili başlık altındayken sağ tarafta bulunan **Milestones** bölümünden yararlanabilirsiniz. 

Planlanan bir versiyon altında ilişkilendirilen ***issue*** listesini görebilir, ilgili versiyonun ne kadarının tamamlandığını görebilirsiniz. Yine arguman.org'un çok iyi kullandığı [Milestones](https://github.com/arguman/arguman.org/milestones) sayfasını inceleyerek daha detaylı bilgi sahibi olabilirsiniz.


## 3. Branch (Dal) Yönetimi

Branch (dal) kavramı, versiyon kontrol sistemleri için önemli bir kavram olmasına rağmen birçok geliştirici tarafından ihmal edilmektedir. 

Varsayılan olarak Git ile bir depo oluşturduğunuzda ana dalımız **master** ismini almaktadır. Dilerseniz ana dal adını değiştirebilirsiniz. 

Paket geliştirirken her zaman için çalışan kararlı sürümünüzü **master** üzerinde tutmanız ve en az 2 farklı dalınızın olması önerilmektedir. Bunun neden zorunlu olduğunu bir örnekle birlikte irdelemek istiyorum. Örneğin; bir paket hazırladığımızı ve bunu yayınladığımızı varsayalım. Bu işlemden sonra başka bir özellik ile ilgili çalışmaya başladık. Bu arada hemen düzeltilmesi gereken bir hata bildirimi geldi. Eğer biz aynı dal üzerinde çalışırsak, üzerinde çalıştığımız yeni özellikleri ve hatayı düzelttiğimiz kodu birbirinden ayıramayız. Bu durumda ya hatanın düzeltilmiş halinin yayınlanması için yeni özelliklerin bitmesini bekleyeceksiniz ya da henüz bitmemiş özellikleri de yayınlayacaksınız. Bu durum bizi çaresiz bırakacaktır. 

Yukarıda anlatılan nedenden ötürü ben 3 farklı dal oluşturmanızı öneriyorum; **master, dev, bug**. Bu dallardan **master**, her zaman için kararlı sürümü barındırmalı ve kesinlikle doğrudan bu dal üzerinde geliştirme yapılmamalıdır. Yeni bir özellikle geliştirirken kullanacağımız dal **dev** olmalıdır. Bir hata durumunda ise **bug** dalı üzerinde çalışmalı ve değişikler ***master** ile birleştirilmelidir. 

I> ## Bilgi 
I> 
I> En az 3 dal zorunlu değildir. Aynı anda birden fazla özellik geliştirdiğiniz durumlarda, daha fazla dal oluşturabilirsiniz. Ancak çok fazla dalın proje yönetimini de zorlaştırabileceği unutulmamalıdır. 

Tüm bunlara rağmen projeniz için en iyi kararı kendiniz vermelisiniz. ***GitHub*** üzerinde bulunan başka depoların da dal yapısını inceleyerek, daha fazla fikir sahibi olabilirsiniz.


## 4. Pull Request (Kullanıcıların Katkı İstekleri)

Siz paketinizi geliştirirken, bir yandan da başka bir kullanıcı sizin paketinizi katkıda bulunmak isteyebilir. Bu durumda ya ilgili kullanıcıya doğrudan paket üzerinde yetki vermeniz ya da ilgili kullanıcının **Pull Request** olarak tabir ettiğimiz işlemi gerçekleştirmesi gerekir. Güvenlik nedenlerinden ötürü ikinci yöntem daha sağlıklıdır. 

I> ## Uyarı 
I>
I> Tanımadığınız bir kullanıcıya paketiniz üzerinde yetki vermek, ilgili kullanıcının paketinizi bozmasına yol açabilir ve paketinizi kullanan kullanıcıları mağdur edebilir. Bu nedenle tanımadığınız kullanıcılardan kod kabul ederken, bunları incelemeniz gerekmektedir. Bu nedenle ***Pull Request*** daha güvenlidir. 

***Pull Request*** işlemi için ilgili kullanıcı sizin deponuzu **fork** ederek, gerekli değişiklikleri yapar ve **Rull Request** göndererek, geliştirdiği kodları deponuza eklemek istediğini belirtir. Bu işlemden sonra deponuzun **Pull Requests** bölümü altında ilgili istek görülecektir. Siz bu isteğin içerdiği değişiklikleri inceleyerek, isteği kabul edebilir ya da reddedebilirsiniz.

I> ## Bilgi 
I> 
I> Konumuz dışında olduğu için başkasının paketine katkıda bulunma aşamalarına değinilmemiştir. Ancak bu konu hakkında fikir sahibi değilseniz Can Geliş'in [Git ile Açık Kaynaklı Projelere Katkıda Bulunmak](http://www.cangelis.com/git-ile-acik-kaynakli-projelere-katkida-bulunmak) başlıklı makelesini inceleyerek detaylı bilgi sahibi olabilirsiniz.

Aksini belirtmediğiniz sürece kullanıcılar doğrudan sizin **master** dalınıza ***Pull Request*** isteği gönderebilir. Ancak bunu çeşitli sebeplerden ötürü tavsiye etmiyorum. Öncelikle her zaman aklınızda olması gereken; tanımadığımız kullanıcılara güvenmemektir. Bir ***Pull Request*** geldiğinde kodları inceleyebilirsiniz, ancak ilgili değişikleri doğrudan **master** dalına göndermeden önce, testlerinizi çalıştırarak genel yapıyı bozmadığından emin olmak daha mantıklı bir seçenek olacaktır. Bu nedenle katkıda bulunmak isteyenler için ayrı bir dal açarak, isteklerini o dala göndermelerini isteyebilirsiniz. 

I> ## Bilgi 
I> 
I> Projenize katkı sağlayacak kişilerin hangi şartları göz önünde bulundurarak katkı sağlayacağıyla ilgili bir döküman yazmanız yerinde olacaktır. İlgili dökümanın adı genel kabulden ötürü `CONTRIBUTING` olmalıdır ve mümkünse deponuzda kolay ulaşılabilir bir dizinde konumlandırılmalıdır.  



















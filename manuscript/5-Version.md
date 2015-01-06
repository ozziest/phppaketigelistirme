# Semantik Versiyonlama

Yazılım dünyasında önemli bir sorun versiyonlamadır. Bu bazı insanlar için ticari bir kavram olabilir ama bizim için teknik bir tabirdir. Paket geliştirme ve sürdürme süresince ise kritik bir rol oynar. 

Geliştirilen birçok paket, yazılımın doğası gereği geliştirildiği gibi kalmaz. Hatalar giderilir, yeni özellikler eklenir ya da çekirdekte çok önemli değişikliker yapılabilir. 

Örneğin; bir paket geliştirirken, başka bir **A** paketini kullandığınızı varsayalım ve kendi paketinizin bir yerinde **A** paketinde bulunan ***getAttr()*** metodunu çağırıyorsunuz. Ancak zamanla **A** paketinin içeriği değişti ve bu metot kullanımdan kaldırıldı. Bu durumda sizin paketiniz çalışmaz. Paketler ***Composer*** ile otomatik olarak güncellenebildiğinden, paketinizin çalışması siz daha farkına varamadan bozulabilirdi. 

Peki bu değişime nasıl ayak uyduracağız ve paketlerin birbirleri ile uyumla çalışmasını sağlayacağız? Bu sorun uzun zaman önce çözülmüş ve **Semantik Versiyonlama** ortaya atılmıştır.

### Değişiklik Kategorileri

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

#### Patch Güncellemeleri

Paketimizdeki çeşitli hatalar düzeltildiğinde ilgili işlem bu kategoride değerlendirilir. Tespit edilen bir hata giderilmiş ve paketin çalışma mantığında hiçbir değişiklik olmamıştır. 

#### Minor Güncellemeler

Paketimize yeni bir özellik eklediğimizde bu kategoride değerlendirilir. Örneğin **Cache** işlemi yapan bir paket tasarladığımızı varsayalım. Bu paket daha önce **MemCache** teknolojisi ile çalışabiliyorken daha sonradan **Redis** teknolojisi de eklenirse bu bir **minor** güncelleme olacaktır. 

W> ## Uyarı
W>
W> Anahtar kuralımız, minor değişiklikten sonra geçmişe yönelik desteğin devam etmesidir. Eğer destek devam etmiyorsa, yani paketin eski halini kullanan kodlar bundan etkilenebilirse bu bir major değişikliktir. 

#### Major Güncellemeler

Paketimizde yapılan ve sonrasında paketin çalışmasını doğrudan etkileyen değişikliklere verilen isimdir. Örneğin var olan bir metodun kaldırılması ya da yeni bir zorunlu parametre eklenmesi gibi değişiklikler **major** güncelleme olarak adlandırılır.

Major güncellemeler pek sevilmez. Çünkü o ana kadar paketi kullanan başka projeler bundan etkilenecektir. Eğer bir major güncelleme olursa, muhtalaka bir **Upgrade Guide (Yükseltme Rehberi)** hazırlanarak, ilgili değişikliğe nasıl adapte olunacağı belgelendirilmelidir.

I> ## Bilgi 
I> 
I> Bazı durumlarda major değişiklikler o kadar büyük olur ki; eski sürümden yeni major sürüme geçmek olanaksız olur. 

### Composer'da Versiyon Seçimi

Composer ile bir paketi projenize dahil ederken aşağıdaki kullanım şeklinden yararlanabilirsiniz;

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

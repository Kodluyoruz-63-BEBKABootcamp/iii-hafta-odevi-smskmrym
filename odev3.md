- .Net kodu nedir ve nasıl derlenir?

- Roslyn compiler ne işe yarar?
 
 NET Compiler Platform (Roslyn) çözümleyiciler stil, kalite, bakım, tasarım ve diğer sorunlar için C# veya Visual Basic kodunuzu inceler. Bu denetleme veya analiz, tüm açık dosyalardaki tasarım zamanı sırasında yapılır.
Çözümleyiciler aşağıdaki gruplara ayrılabilir:
Kod stili Çözümleyicileri, Visual Studio 'da yerleşik olarak bulunur. Bu çözümleyiciler için tanılama KIMLIĞI veya kodu ıdexxxx biçimindedir, örneğin, IDE0067. Tercihleri, metin düzenleyici seçenekleri sayfasında veya bir editorconfig dosyasındayapılandırabilirsiniz. .NET 5,0 ' den başlayarak, kod stili Çözümleyicileri .NET SDK 'ya dahildir ve derleme uyarıları veya hataları olarak kesinlikle zorlanabilir.
Kod kalitesi Çözümleyicileri artık .NET 5 SDK 'ya dahildir ve varsayılan olarak etkindir. Bu çözümleyiciler için tanılama KIMLIĞI veya kodu CAxxxx biçimindedir, örneğin, CA1822.
Üçüncü taraf Çözümleyicileri, bir NuGet paketi veya bir Visual Studio uzantısı olarak yüklenebilir. StyleCop, roslynator, xUnit Çözümleyicilerive sonar Çözümleyicisigibi üçüncü taraf Çözümleyicileri.

- Restful servisler nasıl çalışır? 

Alternatifleri nelerdir ve nasıl çalışırlar?
REST (Representational State Transfer )istemci-sunucu arasında hızlı ve kolay şekilde iletişim kurulmasını sağlayan bir servis yapısıdır.
REST, servis yönelimli mimari üzerine oluşturulan yazılımlarda kullanılan bir veri transfer yöntemidir. HTTP üzerinde çalışır ve diğer alternatiflere göre daha basittir, minimum içerikle veri alıp gönderdiği için de daha hızlıdır. İstemci ve sunucu arasında XML veya JSON verilerini taşıyarak uygulamaların haberleşmesini sağlar. 
REST stateless‘dır, yani durum bilgisini saklamaz. Yani standartlarında istemci-sunucu arasında taşınan verilerde ekstra başlık bilgileri saklanmaz, istemciye ait detaylar bulunmaz, bu bilgiler istemci-sunucu arasında taşınmaz. Dolayısıyla servis yönelimli uygulamalarda REST bize lightweight bir çözüm yapısı sunar.

- Extension method nedir? Nasıl yazılır?

Extension method bize .Net içerisinde bulunan sınıflara yeni metodlar eklememizi sağlamaktadır. Extension metodlar static class içerisinde static olarak tanımlanmaktadır.
Extesion metod yazarken uymamız gereken bir kaç kural vardır. Bunlar;  
   -Extension metodlar static bir class içerisinde static olarak tanımlanmalıdır.  
   -Extend edilecek class ilgili extension metoda metodun ilk parametresi olarak verilip önünde this keyword'ü ile tanımlanmalıdır.  
   -Extension metod da tanımlı parametrelerden sadece 1 tanesi this keyword'ü ile tanımlanır.  

- MVC'nin alternatifleri nelerdir?
  - ADR (Action-Domain-Responder)
ADR, HTTP üzerinden haberleşen web uygulamalarını tanımlamak üzere geliştirilmiş bir tanımlama. Net bir implementasyonu yok. Vurguladığı önemli noktalardan biri,  bir uygulama mimarisi olmaması ve sadece web uygulamaları için bir kullanıcı etkileşimi pattern’i olması.
ADR elemanları olan action, domain ve responder’ı MVC’deki elemanlara benzetebiliriz bir noktada.
- Architectural pattern nedir? Neden ihtiyaç duyuyoruz?
Architectural pattern, belirli bir bağlamda yazılım mimarisinde yaygın olarak ortaya çıkan bir soruna genel, yeniden kullanılabilir bir çözümdür. Architectural pattern  yazılım tasarım desenine benzer, ancak daha geniş bir alana sahiptir.
  - Model-view-controller deseni
MVC pattern olarak da bilinen bu desen, etkileşimli uygulamayı aşağıdaki gibi 3 bölüme ayırır:,
model:  temel işlevselliği ve verileri içerir
view:  bilgileri kullanıcıya görüntüler (birden fazla görünüm tanımlanabilir)
controller:  kullanıcıdan gelen girişi işler
Bu, bilginin iç temsillerini, bilginin kullanıcıya sunulma ve kabul edilme biçimlerinden ayırmak için yapılır. Bileşenler tamamen bağımsız hale getirilir ve verimli kodu yeniden kullanmayı sağlar.
- ViewData, ViewBag, TempData farkları nelerdir? Çalıştığımız proje üzerinde başka bir branch açarak bunları deneyiniz?
ViewBag, ViewData ve TempData tüm nesneleri ASP.NET MVC ve bunlar verileri çeşitli senaryolarda iletmek için kullanılır. Aşağıda, bu nesneleri kullanabileceğimiz senaryolar bulunmaktadır.

  -Verileri Denetleyiciden görüntülemek üzere iletin.  
  -Verileri aynı Denetleyicideki bir eylemden başka bir eyleme iletin.  
  -Verileri Denetleyiciler arasında iletin.  
  -Verileri ardışık istekler arasında iletin.  
  
    - ViewBag
 ViewBag, verileri Denetleyiciden görünüme geçirmek için dinamik bir nesnedir. Ve bu, verileri object ViewBag özelliği olarak geçirir. Ve verileri okumak veya boş kontrol etmek için typecast'e gerek yok. ViewBag kapsamı geçerli istek için izin verilir ve ViewBag değeri yeniden yönlendirme sırasında null olur.

  - ViewData
  ViewData, verilerin anahtar-değer çifti olarak iletildiği yeri görüntülemek için Denetleyiciden veri aktarmak için kullanılan bir sözlük nesnesidir. Ve veriler karmaşıksa ve boş istisnalardan kaçınmak için boş bir kontrol sağlamamız gerekiyorsa, verileri görüntülemek için yazım denetimi gereklidir. ViewData kapsamı ViewBag benzer ve geçerli istek ile sınırlıdır ve viewdata değeri yeniden yönlendirme sırasında null olur.

  - TempData
TempData, verileri bir eylemden aynı Denetleyicide veya farklı Denetleyicilerde başka bir eyleme geçirmek için bir sözlük nesnesidir. Genellikle, TempData nesnesi bir oturum nesnesinde saklanır. Tempdata ayrıca typecast ve ondan veri okumadan önce null denetimi için gereklidir. TempData kapsamı bir sonraki istekle sınırlıdır ve Tempdata'nın daha da erişilebilir olmasını istiyorsak, Keep ve peek kullanmalıyız.

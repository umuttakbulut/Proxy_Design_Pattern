# Proxy_Design_Pattern

Proxy tasarım deseni structural tasarım desenlerinden biridir. 
Bir nesneye erişimi kontrol etmek için, proxy nesne kullanır.
Bu nesne erişilecek nesneyi kontrol eder. Erişilecek nesne remote, yaratılması pahalı olan veya erişim için yetki 
istiyen gibi türlere sahip olabilir.

Ne zaman Kullanılır?

1. Remote nesne kullanmak istediğimizde kullanılır.(Remote proxy, farklı adres uzayında bulunan bir nesneye lokal temsilci sağlar)
2. Masraflı nesnelerin ihtiyaç duyulduğunda yaratılmasını sağlamak için(Örneğin resim yüklenmeden önce yükleniyor yazısı göstermek için. Bazı resimlerin boyutu büyük olduğu için yüklenmesi geç olabilmektedir. Burada belirtilen masraflı ifadesi büyük resim nesnesini temsil eder) kullanılır. Bu tarz proxy'lere virtual proxy denir.
3. Client'ın yetkisine göre işlem yapılıp yapılmamasını belirlemek için kullanılır. (Protection proxy)

Nasıl Kullanılır?

Öncelikle türü interface veya abstract olan bir Subject sınıfı oluşturulur. Bu sınıftan türeyecek veya sınıfı(interface olarak tanımlanırsa) implement edecek Proxy ve RealSubject sınıfları yaratılır. Bu sınıflar aynı sınıftan türediği için, ortak metod(lar)a sahip olurlar. Proxy sınıfına, Subject türüne sahip değişken eklenir. Proxy ve RealSubject aynı sınıftan türediği için türleri aynı olur. Bu sayede Proxy sınıfı içerisindeki bir metod içerisinden RealSubject sınıfındaki metod çağrılır. Proxy sınıfında bulunan metoda ise Client sınıfı tarafından erişilir. Client sınıfı RealSubject sınıfına direkt erişmez, bunun yerine Proxy sınıfı aracılığı ile erişir. Proxy sınıfı bu özelliği 
ile erişimi kontrol eden sınıf olarak adlandırılır.Ayrıca RealSubject sınıfından nesne yaratılma işlemi Proxy sınıfında yapılır.

Gerekenler

Proxy sınıfı. RealSubject sınıfına erişimi kontrol eder ve düzenler. Client sınıfı tarafından erişilir.
Türü interface veya abstract olan Subject sınıfı. Proxy ve RealSubject sınıfları bu interface'den implement olurlar.
Real Subject: Somut Subject sınıfı.
Client sınıfı. Proxy sınıfı aracılığı ile RealSubject nesnesine erişir. Direkt erişmez.

Örnek Kullanım Alanları

1. java.lang.reflect.Proxy sınıfı
2. java.rmi paketinin tamamı kullanır.


Örnek Uygulama

Proxy ile kullanıcıya göre yetkilendirme işlemi yapılması uygulamasıdır.

Not: Bu uygulamamızda protection proxy kullanılmıştır.

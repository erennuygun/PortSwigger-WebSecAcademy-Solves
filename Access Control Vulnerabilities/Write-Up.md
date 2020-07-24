# Access Control Vulnerabilities

Bu seride Port Swigger web sitesinde bulunan Web Security Academy başlığındaki challengelerdan Access Control Vuln. adlı challengeları çözüyoruz.

## Lab 1 : [Unprotected admin functionality](https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality) :

Bir web testine başlarken her zaman yaptığımız gibi /robots.txt&#39;ye bakıyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab1.png)

Bir admin panelinin adresi mevcut.Bu adrese gittiğimiz zaman panele erişim sağlıyoruz.Böylelikle **carlos**&#39;u siliyoruz.

## Lab 2 : [Unprotected admin functionality with unpredictable URL](https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality-with-unpredictable-url)

Sayfanın kaynak koduna girdiğimiz zaman admin panelinin adresini görüyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab2.png)

Bu adrese gittiğimiz zaman başarılı bir şekilde **carlos** kullanıcısını silebiliyoruz.

## Lab 3 : [User role controlled by request parameter](https://portswigger.net/web-security/access-control/lab-user-role-controlled-by-request-parameter) :

**wiener:peter** kullanıcı bilgileri ile giriş yaptığımız zaman cookie de **Admin** adında bir değer tutulmakta ve bu değer **false** durumda.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab3-1.png)

Bu değeri **true** yapıp admin paneline giriş yapıyoruz ve carlos kullanıcısını siliyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab3-2.png)

## Lab 4 - [User role can be modified in user profile](https://portswigger.net/web-security/access-control/lab-user-role-can-be-modified-in-user-profile) :

**wiener:peter** kullanıcı bilgileri ile giriş yaptığımız zaman, kullanıcı sayfasına email değiştirme yerine rastgele bir email girerek giden isteği inceliyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab4-1.png)

İsteği &quot;Repeater&quot;&#39;a atıp dönen response&#39;a baktığımız zaman, **roleid** adında bir değişkenin bulunduğunu ve değerinin de 1 olduğunu görüyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab4-2.png)

Bu değeri 2 yapıp isteğimiz üzerinde değiştirerek tekrar yolladığımızda admin haklarına erişim sağlıyoruz.Böylelikle **carlos** kullanıcısını silebiliyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab4-3.png)

## Lab 5 - [URL-based access control can be circumvented](https://portswigger.net/web-security/access-control/lab-url-based-access-control-can-be-circumvented) :

Admin paneline gitmek istediğimiz zaman sunucu bize &quot;Access Denied&quot; hatası döndürdü.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab5-1.png)

Bunun önüne geçmek için gideceğimiz adrese rastgele bir değer giriyoruz fakat **X-Original-URL** başlığını kullanarak asıl gitmek istediğimiz yeri yazıyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab5-2.png)

Böylelikle admin paneline erişim sağlayabiliyoruz.Daha sonradan **carlos** kullanıcısını silme işlemini yapıyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab5-3.png)

## Lab 6 - [Method-based access control can be circumvented](https://portswigger.net/web-security/access-control/lab-method-based-access-control-can-be-circumvented) :

Admin hesabıyla giriş yaptığımız zaman kullanıcıların yetkilerini düzenleyebildiğimizi görebiliyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab6.png)

Amacımız **wiene** kullanıcısının yetkilerini admin haklarına getirmek.Bunun için admin kullanıcısında iken wiene kullanıcısının yetkilerini arttıma butonuna basıyoruz ve giden isteği inceliyoruz.Fakat isteği göndermiyoruz çünkü amacımız wiene kullanıcısında iken yetkimizi yükseltmek.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab6-2.png)

Almış olduğumuz isteği **wiene** kullanıcısının cookie değeri ile gönderdiğimiz zaman başarısız olduk.Fakat kullanmış olduğumuz HTTP Metodu POST idi.Metodumuzu GET Metodu ile değiştirdiğimiz zaman ise başarılı bir şekilde kullanıcımızın yetkisini admin haklarına getirmiş olduk.

## Lab 7 - [User ID controlled by request parameter](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter):

Burada bizden istenilen **wiene** kullanıcısında iken **carlos** kullanıcısının **API keyini** almak.Bunun için wiene kullanıcısına giriş yapıyoruz ve adres çubuğunda bulunana wiene yerine carlos yazıyoruz ve başarılı bir şekilde API keyi elde ediyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab7.png)

## Lab 8 - [User ID controlled by request parameter, with unpredictable user IDs](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-unpredictable-user-ids):

Wiener kullanıcısı ile login olduğumuz zaman, kullanıcımızın sayfasına gitmek için kullandığımız GET isteği aşağıdaki şekilde.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab8-1.png)

Bizim amacımız **carlos** kullanıcısının UID değerini bulmak ve bu kısıma yazmak.Böylelikle **carlos** kullanıcısının API keyini elde edebilmekteyiz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab8-2.png)

Bir tane yazıya giriş yaptığımız da yazıyı carlos kullanıcısının oluşturduğunu farkediyoruz.Kullanıcının üzerine tıkladığımızda ise adres çubuğunda carlos kullanıcısının UID değerini bulabiliyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab8-3.png)

Böylelikle isteğimizde bulunan UID değeri ile bu değeri değiştirdiğimiz zaman başarılı bir şekilde **carlos** kullanıcısının **API Keyini** elde ediyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab8-4.png)

##


## Lab 9 - [User ID controlled by request parameter with data leakage in redirect](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-data-leakage-in-redirect):

Wiener kullanıcısı ile login olduğumuz zaman, kullanıcımızın sayfasına gitmek için kullandığımız GET isteği aşağıdaki şekilde.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab9-1.png)

Burada bulunan **id** değerine tarayıcı üzerinden carlos yazdığımız zaman ana sayfaya redirect ediyor.Ama bu işlem şöyle oluyor;

1- carlos tarafına istek yapılıyor.

2- sunucudan response dönüyor.

3- ana sayfaya redirect ediiliyor.

Bu durumda browser üzerinden biz bu response u göremiyoruz.Fakat Burp ile araya girdiğimiz zaman başarılı bir şekilde **carlos** kullanıcısının **API Key** değerini elde ediyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab9-2.png)

## Lab 10 - [User ID controlled by request parameter with password disclosure](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-password-disclosure) :

Wiener kullanıcısı ile giriş yaptık.Kullanıcı sayfasını açtığımız zaman parola değiştirme formunun bulunduğunu gördük.Bu durumda parola masked bir şekilde olduğu için bunu öğe inceleme kısmında clear text bir şekilde görebildik.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab10-1.png)

Daha sonradan adres çubuğuna administrator kullanıcısını girdiğimiz zaman, administrator kullanıcısının da parola bilgisini masked bir şekilde gördük.Bunu da öğe incele ile clear text bir hale getirdik ve bu kullanıcı ile giriş yaptık.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab10-2.png)

Sonuç olarak carlos kullanıcısını silebildik.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab10-3.png)

## Lab 11 - [Insecure direct object references](https://portswigger.net/web-security/access-control/lab-insecure-direct-object-references) :

Bu lab üzerine bir live chat uygulaması çalışmakta.Chatta konuşulduktan sonra view transcript butonuna basıp isteği inceliyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab11-1.png)

İstek üzerinde 3.txt bulunmakta.Başka konuşmalar olmuş mu diye kontrol etmek için 1.txt yazıp isteği yolladığımız zaman başarılı bir şekilde carlosun parolasını ele geçirmiş oluyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab11-2.png)

## Lab 12 - [Multi-step process with no access control on one step](https://portswigger.net/web-security/access-control/lab-multi-step-process-with-no-access-control-on-one-step)

Administrator kullanıcısı olarak giriş yapıyoruz.Panel üzerinde wiener kullanıcısını upgrade et diyerek giden isteği inceliyoruz.İstek iki aşamalı upgrade edilsin mi diye bir soru daha soruluyor o istek üzerinde tüm değerler giriliyor.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab12.png)

Bu durumda Cookie değerini wiener kullanıcısına girip wiener kullanıcısının cookie değeri ile bu isteği gönderdiğimiz zaman başarılı bir şekilde wiener kullanıcısı ile kullanıcımızın yetkilerini admin haklarına yükseltmiş oluyoruz.

##


## Lab 13 - [Referer-based access control](https://portswigger.net/web-security/access-control/lab-referer-based-access-control):

Bu durumda Lab 12 ile aynı fakat buradaki farklılık Referrer headerı.Referrer Headerı doğru olmazsa başarılı olamıyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab13-1.png)

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Access%20Control%20Vulnerabilities/images/lab13-2.png)

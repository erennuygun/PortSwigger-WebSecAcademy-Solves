# HTTP Host Header Attacks

## LAB :1 [Basic password reset poisoning](https://portswigger.net/web-security/host-header/exploiting/password-reset-poisoning/lab-host-header-basic-password-reset-poisoning)

Lab açıklamasında carlos kullanıcısının mailine gelen tüm linklere tıkladığı belirtilmiştir. Böylelikle &quot;Forgot Password&quot; kısmından carlos kullanıcı adını giriyoruz ve carlos kullanıcısına mail gitmesini sağlayan isteği yakalıyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab1-1.png)

Carlos kullanıcısı mailde gelen linke tıkladığında bizim o isteği yakalayıp tokeni elde etmemiz gerekmektedir. Bu yüzden exploit serverın adresini Host Header bilgisine giriyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab1-2.png)

Vee başarılı bir şekilde isteği gönderebildik. Görüldüğü gibi exploit serverın access.logları içerisinde carlosun isteği exploit serverımıza geldi ve link üzerinde token bulunmaktadır.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab1-3.png)

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab1-4.png)

Bu token ile parola değiştirme sayfasına gidip carlos adlı kullanıcısının parolasını değiştiriyoruz.

## LAB: 2 [Password reset poisoning via dangling markup](https://portswigger.net/web-security/host-header/exploiting/password-reset-poisoning/lab-host-header-password-reset-poisoning-via-dangling-markup)

Bu labta ise yine aynı şekilde carlos&#39;un mail adresine parola unuttum isteği gönderilmektedir.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab2-1.png)

Fakat bu sefer aşağıdaki resimde görüldüğü gibi parola sıfırlama linki bulunmamaktadır. Uygulama direkt olarak kullanıcıya yeni bir parola vermektedir. Bu yüzden kullanıcı linke tıklasa bile birinci labta çözdüğümüz gibi parolayı elde edememekteyiz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab2-2.png)

Fakat bu yazacağımız host bilgisi ile mail üzerinde host kısmının tırnağını ve \&lt;a\&gt; tagini kapatıp daha sonra \&lt;img src taginin içerisine exploit serverın adresini verip src bilgisinin tırnak işaretini kapatmazsak eğer src bilgisi mailin sonuna kadar okunacak ve load exploit server adresiymiş gibi istek atacaktır.

Fakat bir diğer sorun ise Host bilgisinde &quot; , \&gt;, \&lt; karakterlerinin kullanılamaması durumu. Bu durumda url parseların çalışma mantığı bilinmeli. Çünkü URL parselar sayesinde gireceğimiz port bilgisi ile bu durumu bypasslayabilmekteyiz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab2-3.png)

Aşağıdaki resimde bu işlemleri yaptıktan sonra başarılı bir şekilde access.log üzerinde carlos kullanıcısının yeni parolası alınmaktadır.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab2-4.png)

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab2-5.png)

## LAB: 3 [Web cache poisoning via ambiguous requests](https://portswigger.net/web-security/host-header/exploiting/lab-host-header-web-cache-poisoning-via-ambiguous-requests)

	Lab&#39;a giriş yaptığımızda gelen istekleri incelediğimizde Response&#39;da **&quot;X-Cache: miss&quot;** başlığını görmekteyiz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab3-1.png)

Öncelikle Host Header Injection klasiği olan host kısmına farklı bir domain giriyoruz. Fakat görüldüğü gibi 504 hatası almaktayız.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab3-2.png)

Böylelikle **&quot; ?c=aa&quot;** gibi bir istek attığımız zaman, ikinci isteğimizde bu başlık sayesinde isteğimizin cachelendiğini tespit ediyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab3-3.png)

Yeni bir host bilgisi girdiğimiz zaman ise başarılı bir şekilde sistemin kabul ettiğini görmekteyiz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab3-4.png)

Böylelikle exploit server&#39;a gidip gerekli ayarlamaları yapıyoruz. Lab&#39;ın bizden istemiş olduğu XSS payloadını exploit server&#39;ımıza giriyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab3-5.png)

Daha sonra isteği gönderdiğimizde başarılı bir şekilde istediğimiz domaine gitmesini sağlıyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab3-6.png)

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab3-7.png)

## LAB: 4 [Host header authentication bypass](https://portswigger.net/web-security/host-header/exploiting/lab-host-header-authentication-bypass)

	Burada bizden admin sayfasına gidip carlos kullanıcısının silinmes istenilmektedir. Fakat /admin sayfasına gitme yetkimiz aşağıdaki ekran görüntüsünde görüldüğü gibi bulunmamaktadır.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab4-1.png)

Konumuz Host-Header Injection olduğuna göre Host başlık bilgimizi localhost olarak değiştirmeyi denediğimizde başarılı bir şekilde giriş yaptığımızı görüyoruz.

Ve dönen cevap üzerinde carlos kullanıcısının delete?username=carlos şeklinde silindiğini tespit ediyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab4-2.png)

## LAB: 5 [Routing-based SSRF](https://portswigger.net/web-security/host-header/exploiting/lab-host-header-routing-based-ssrf)

Labın açıklamasında bize admin sayfasına erişimin internal bir ip aralığında olduğundan bahsetmiş. Bizde bu yüzden host başlığına 192.168.0.0/24 aralığı için brute force yapıyoruz. Gelen 200 status code &#39;una göre isteğimizin başarılı olduğunu anlayacağız.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab5-1.png)

Gördüğümüz gibi başarılı bir şekilde internal ipnin 192.168.0.97 olduğunu anladık.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab5-2.png)

Böylelik bu tespit ettiğimiz internal ip adresi ile carlos kullanıcısını başarılı bir şekilde silebildik.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab5-3.png)

## LAB: 6 [SSRF via flawed request parsing](https://portswigger.net/web-security/host-header/exploiting/lab-host-header-ssrf-via-flawed-request-parsing)

Bu labtada bizden lab5 istenildiği gibi internal bir ip adresi tespit etmemiz ve carlos kullanıcısını silmemiz bekleniyor.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab6-1.png)

Aynı şekilde admin sayfasına istek attığımızda 403 isteği almaktayız. Bunun önüne geçebilmek için admin sayfasına isteğimizi aşağıdaki ekran görüntüsünde görüldüğü gibi atıyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab6-2.png)

Bunun sonucunda 403 hatasından kurtuluyoruz. Böylelik aynı şekilde internal ip aralığına brute force atağı yaparak ip adresini tespit ediyoruz. Daha sonra carlos kullanıcısını siliyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab6-3.png)

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Host%20Header%20Attacks/images/lab6-4.png)

# Information Disclosure

## LAB 1 - [Information disclosure in error messages](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-in-error-messages)

Bizden istenilen error sayfasında bir bilgi ifşa bulmamız ve bunu submit etmemiz.Bu yüzden error verilebilecek yerler bakıldığında, ürünlerin id değerine göre geldiği görülmektedir.Buradaki id değeri yerine rastgele değerler girildiğinde error sayfası karşımıza gelmektedir.Burada da kullanılan Apache Struts&#39;ın versiyon bilgisi ifşa edilmiştir.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Information%20Disclosure/images/lab1.png)

## LAB 2 - [Information disclosure on debug page](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-on-debug-page)

Sayfamızın kaynak koduna girdiğimiz de yorum satırı içerisinde bir dizin belirtilmiş.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Information%20Disclosure/images/lab2-1.png)

Dizine gittiğimiz zaman kullanılan **Secret-Key** değerini görebilmekteyiz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Information%20Disclosure/images/lab2-2.png)

## LAB 3 - [Source code disclosure via backup files](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-via-backup-files)

Web testlerinde her zaman yaptığımız gibi robots.txt dizinine gittiğimiz zaman **/backup** adına bir dizinin olduğu görülmektedir.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Information%20Disclosure/images/lab3-1.png)

Dizini takip ettiğimizde ise bir backup dosyası açılmaktadır ve içerisinde database parolası bulunmaktadır.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Information%20Disclosure/images/lab3-2.png)

##


## LAB 4 - [Authentication bypass via information disclosure](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-authentication-bypass)

Öncelikle admin haklarına erişmemiz gerektiği için authentication bypass yapmamız gerekmektedir.Bunun için /admin dizinine istek yapıp, inceliyoruz.

##


![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Information%20Disclosure/images/lab4-1.png)

İstek sonucunda dönen yanıtta sadece adminlerin veya localhosttan gelenlerin panele erişebileceği söyleniyor.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Information%20Disclosure/images/lab4-2.png)

HTTP Metodumuzu TRACE yaptıktan sonra sunucu X-Custom-IP-Authorization headerı ile IP bilgisini almakta olduğunu görüyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Information%20Disclosure/images/lab4-3.png)

Bizde bu yüzden bu headerı kullanarak /admin dizinine sanki localhosttan geliyormuş gibi istek yapıyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Information%20Disclosure/images/lab4-4.png)

Ve görüldüğü gibi başarılı bir şekilde giriş yaptık.Şimdi zalim carlosu silmenin zamanı :)

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Information%20Disclosure/images/lab4-5.png)

Evet başarılı bir şekilde carlos kullanıcısını sildik.

## LAB 5- [Information disclosure in version control history](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-in-version-control-history)

Sayfa üzerinde yapılan incelemeler sonucunda **.git** dizinin açık olduğunu görülüyor.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Information%20Disclosure/images/lab5-1.png)

Bu dizini hemen lokalimize çekiyoruz ve acaba commitlerdeki bilgilere bakıyoruz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Information%20Disclosure/images/lab5-2.png)

Görüldüğü yapılan son committe administrator kullanıcısının parola bilgisi bulunmakta.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Information%20Disclosure/images/lab5-3.png)

Veee administrator kullanıcısı olarak giriş yaptıktan sonra her zaman olduğu gibi carlos kullanıcısını siliyoruz.

&quot; Garibanın yüzü gülür mü :) &quot; **carlos**

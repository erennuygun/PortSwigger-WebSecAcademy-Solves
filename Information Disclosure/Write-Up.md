# Information Disclosure

## LAB 1 - [Information disclosure in error messages](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-in-error-messages)

Bizden istenilen error sayfasında bir bilgi ifşa bulmamız ve bunu submit etmemiz.Bu yüzden error verilebilecek yerler bakıldığında, ürünlerin id değerine göre geldiği görülmektedir.Buradaki id değeri yerine rastgele değerler girildiğinde error sayfası karşımıza gelmektedir.Burada da kullanılan Apache Struts&#39;ın versiyon bilgisi ifşa edilmiştir.

![](RackMultipart20200723-4-16qt179_html_e4f2ae4b5c2c6949.png)

## LAB 2 - [Information disclosure on debug page](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-on-debug-page)

Sayfamızın kaynak koduna girdiğimiz de yorum satırı içerisinde bir dizin belirtilmiş.

![](RackMultipart20200723-4-16qt179_html_dba5edd5a73b511d.png)

Dizine gittiğimiz zaman kullanılan **Secret-Key** değerini görebilmekteyiz.

![](RackMultipart20200723-4-16qt179_html_f72157e30cf0c4a3.png)

## LAB 3 - [Source code disclosure via backup files](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-via-backup-files)

Web testlerinde her zaman yaptığımız gibi robots.txt dizinine gittiğimiz zaman **/backup** adına bir dizinin olduğu görülmektedir.

![](RackMultipart20200723-4-16qt179_html_f5bccac26b4d5e54.png)

Dizini takip ettiğimizde ise bir backup dosyası açılmaktadır ve içerisinde database parolası bulunmaktadır.

![](RackMultipart20200723-4-16qt179_html_703deb7cff926e1c.png)

##


## LAB 4 - [Authentication bypass via information disclosure](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-authentication-bypass)

Öncelikle admin haklarına erişmemiz gerektiği için authentication bypass yapmamız gerekmektedir.Bunun için /admin dizinine istek yapıp, inceliyoruz.

##


![](RackMultipart20200723-4-16qt179_html_1447c05029ad5c44.png)

İstek sonucunda dönen yanıtta sadece adminlerin veya localhosttan gelenlerin panele erişebileceği söyleniyor.

![](RackMultipart20200723-4-16qt179_html_5e128ce93e2fbba7.png)

HTTP Metodumuzu TRACE yaptıktan sonra sunucu X-Custom-IP-Authorization headerı ile IP bilgisini almakta olduğunu görüyoruz.

![](RackMultipart20200723-4-16qt179_html_fb3e55b66a9942c0.png)

Bizde bu yüzden bu headerı kullanarak /admin dizinine sanki localhosttan geliyormuş gibi istek yapıyoruz.

![](RackMultipart20200723-4-16qt179_html_28097e8491fa762c.png)

Ve görüldüğü gibi başarılı bir şekilde giriş yaptık.Şimdi zalim carlosu silmenin zamanı :)

![](RackMultipart20200723-4-16qt179_html_255a0998b7b223d2.png)

Evet başarılı bir şekilde carlos kullanıcısını sildik.

## LAB 5- [Information disclosure in version control history](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-in-version-control-history)

Sayfa üzerinde yapılan incelemeler sonucunda **.git** dizinin açık olduğunu görülüyor.

![](RackMultipart20200723-4-16qt179_html_c98985f7241aa8ea.png)

Bu dizini hemen lokalimize çekiyoruz ve acaba commitlerdeki bilgilere bakıyoruz.

![](RackMultipart20200723-4-16qt179_html_8dbd747bb104d72e.png)

Görüldüğü yapılan son committe administrator kullanıcısının parola bilgisi bulunmakta.

![](RackMultipart20200723-4-16qt179_html_448350c2fb96759a.png)

Veee administrator kullanıcısı olarak giriş yaptıktan sonra her zaman olduğu gibi carlos kullanıcısını siliyoruz.

&quot; Garibanın yüzü gülür mü :) &quot; **carlos**
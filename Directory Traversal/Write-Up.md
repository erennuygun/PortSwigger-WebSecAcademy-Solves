# Directory traversal

## LAB 1 -[File path traversal, simple case](https://portswigger.net/web-security/file-path-traversal/lab-simple):

Sayfamıza girdiğimiz zaman karşımıza çıkan resimlere tıkladığımız giden GET isteği aşağıdaki gibidir.Biz burada **filename** değerine /etc/passwd dosyamızın ismini verdiğimiz zaman herhangi bir filtreleme işlemi olmadığı için başarılı bir şekilde dosyamıza erişebildik.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Directory%20Traversal/images/lab1.png)

## LAB 2 -[File path traversal, traversal sequences blocked with absolute path bypass](https://portswigger.net/web-security/file-path-traversal/lab-absolute-path-bypass):

/etc/passwd ->; yazarak dosyaya erişebilmekteyiz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Directory%20Traversal/images/lab2.png)

## LAB 3 -[File path traversal, traversal sequences stripped non-recursively](https://portswigger.net/web-security/file-path-traversal/lab-sequences-stripped-non-recursively) :

Burada **..** ve **/** karakterleri filtrelenmiş durumda bizde bypass etmek için **...//** karakterlerini yazarak dosyamıza erişebilmekteyiz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Directory%20Traversal/images/lab3.png)

## LAB 4 -[File path traversal, traversal sequences stripped with superfluous URL-decode](https://portswigger.net/web-security/file-path-traversal/lab-superfluous-url-decode) :

/ karakteri her iki şekilde de filtrelenmiş durumda fakat iki kez url encode ettiğimiz zaman dosyaya erişebilmekteyiz.

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Directory%20Traversal/images/lab4.png)

## LAB 5 -[File path traversal, validation of start of path](https://portswigger.net/web-security/file-path-traversal/lab-validate-start-of-path) :

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Directory%20Traversal/images/lab5.png)

Burada dosyaya erişim sağlarken /var/www/images yolunu kullanmış.Bu yüzden bizde /etc/passwd dosyamıza bu yolu kullanarak erişebildik.

## LAB 6 -[File path traversal, validation of file extension with null byte bypass](https://portswigger.net/web-security/file-path-traversal/lab-validate-file-extension-null-byte-bypass):

![](https://github.com/erennuygun/PortSwigger-WebSecAcademy-Solves/blob/master/Directory%20Traversal/images/lab6.png)

%00 karakteri null byte olarak geçmektedir.Böylelikle resim uzantısının olduğu yerin başına getirdiğimiz zaman sistem bunu dosya yolunun sonu zanneder ve oraya kadar çalıştırır.

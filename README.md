# Практична робота № 1

**Дисципліна:** Основи побудови інформаційних систем та мереж

**Тема:** Спостереження за процесом звернення до вебресурсу. Побудова власної моделі рівнів взаємодії

| | |
|---|---|
| **Прізвище, ім'я** |Курганова Марія |
| **Група** |F2 2.01 |
| **Номер варіанта** |14 |
| **Домен варіанта** |opensuse.org |
| **Середовище виконання** | Windows |
| **Версія curl** | curl 8.21.0 (Windows) libcurl/8.21.0 Schannel zlib/1.3.2 WinIDN WinLDAP |
| **Дата виконання** |17.09.2026 |

---

## Частина A. Збір експериментальних даних

### A.1. Запит із діагностичним виводом

**Команда:**

```
curl.exe -v https://opensuse.org
```

**Вивід:**

```
* Host opensuse.org:443 was resolved.
* IPv6: (none)
* IPv4: 195.135.223.50
*   Trying 195.135.223.50:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* ALPN: server accepted http/1.1
* Established connection to opensuse.org (195.135.223.50 port 443) from 192.168.50.166 port 10564
* using HTTP/1.x
> GET / HTTP/1.1
> Host: opensuse.org
> User-Agent: curl/8.21.0
> Accept: */*
>
* Request completely sent off
* schannel: remote party requests renegotiation
* schannel: renegotiating SSL/TLS connection
* schannel: SSL/TLS connection renegotiated
* schannel: remote party requests renegotiation
* schannel: renegotiating SSL/TLS connection
* schannel: SSL/TLS connection renegotiated
< HTTP/1.1 301 Moved Permanently
< content-length: 0
< location: https://www.opensuse.org/
<
* Connection #0 to host opensuse.org:443 left intact
```

---

### A.2. Запит без захисту з'єднання

**Команда:**

```
curl -v http://neverssl.com
```

**Вивід:**

```
* Host neverssl.com:80 was resolved.
* IPv6: (none)
* IPv4: 34.223.124.45
*   Trying 34.223.124.45:80...
* Established connection to neverssl.com (34.223.124.45 port 80) from 192.168.50.166 port 4788
* using HTTP/1.x
> GET / HTTP/1.1
> Host: neverssl.com
> User-Agent: curl/8.21.0
> Accept: */*
>
* Request completely sent off
< HTTP/1.1 200 OK
< Date: Tue, 15 Sep 2026 14:13:07 GMT
< Server: Apache/2.4.68 ()
< Upgrade: h2,h2c
< Connection: Upgrade
< Last-Modified: Wed, 29 Jun 2022 00:23:33 GMT
< ETag: "f79-5e28b29d38e93"
< Accept-Ranges: bytes
< Content-Length: 3961
< Vary: Accept-Encoding
< Content-Type: text/html; charset=UTF-8
<
<html>
        <head>
                <title>NeverSSL - Connecting ... </title>
                <style>
                body {
                        font-family: Montserrat, helvetica, arial, sans-serif;
                        font-size: 16x;
                        color: #444444;
                        margin: 0;
                }
                h2 {
                        font-weight: 700;
                        font-size: 1.6em;
                        margin-top: 30px;
                }
                p {
                        line-height: 1.6em;
                }
                .container {
                        max-width: 650px;
                        margin: 20px auto 20px auto;
                        padding-left: 15px;
                        padding-right: 15px
                }
                .header {
                        background-color: #42C0FD;
                        color: #FFFFFF;
                        padding: 10px 0 10px 0;
                        font-size: 2.2em;
                }
                .notice {
                        background-color: red;
                        color: white;
                        padding: 10px 0 10px 0;
                        font-size: 1.25em;
                        animation: flash 4s infinite;
                }
                @keyframes flash {
                0% {
                        background-color: red;
                }
                50% {
                        background-color: #AA0000;
                }
                0% {
                        background-color: red;
                }
                }
                <!-- CSS from Mark Webster https://gist.github.com/markcwebster/9bdf30655cdd5279bad13993ac87c85d -->
                </style>

                <script>
                        var adjectives = [ 'cool' , 'calm' , 'relaxed', 'soothing', 'serene', 'slow',
                                                        'beautiful', 'wonderful', 'wonderous', 'fun', 'good',
                                                        'glowing', 'inner', 'grand', 'majestic', 'astounding',
                                                        'fine', 'splendid', 'transcendent', 'sublime', 'whole',
                                                        'unique', 'old', 'young', 'fresh', 'clear', 'shiny',
                                                        'shining', 'lush', 'quiet', 'bright', 'silver' ];

                        var nouns =       [ 'day', 'dawn', 'peace', 'smile', 'love', 'zen', 'laugh',
                                                        'yawn', 'poem', 'song', 'joke', 'verse', 'kiss', 'sunrise',
                                                        'sunset', 'eclipse', 'moon', 'rainbow', 'rain', 'plan',
                                                        'play', 'chart', 'birds', 'stars', 'pathway', 'secret',
                                                        'treasure', 'melody', 'magic', 'spell', 'light', 'morning'];
                        var prefix =
                                        // Choose 3 zen adjectives
                                        adjectives.sort(function(){return 0.5-Math.random()}).slice(-3).join('')
                                        +
                                        // Coupled with a zen noun
                                        nouns.sort(function(){return 0.5-Math.random()}).slice(-1).join('');
                        window.location.href = 'http://' + prefix + '.neverssl.com/online';
                </script>
        </head>
        <body>
        <noscript>
                <div class="notice">
                        <div class="container">
                                ⚠️ JavaScript appears to be disabled. NeverSSL's cache-busting works better if you enable JavaScript for <code>neverssl.com</code>.
                        </div>
                </div>
        </noscript>
        <div class="header">
                <div class="container">
                <h1>NeverSSL</h1>
                </div>
        </div>
        <div class="content">
        <div class="container">

        <h1 id="status"></h1>
        <script>document.querySelector("#status").textContent = "Connecting ...";</script>
        <noscript>

                <h2>What?</h2>
                <p>This website is for when you try to open Facebook, Google, Amazon, etc
                on a wifi network, and nothing happens. Type "http://neverssl.com"
                into your browser's url bar, and you'll be able to log on.</p>

                <h2>How?</h2>
                <p>neverssl.com will never use SSL (also known as TLS). No
                encryption, no strong authentication, no <a
                href="https://en.wikipedia.org/wiki/HTTP_Strict_Transport_Security">HSTS</a>,
                no HTTP/2.0, just plain old unencrypted HTTP and forever stuck in the dark
                ages of internet security.</p>

                <h2>Why?</h2>
                <p>Normally, that's a bad idea. You should always use SSL and secure
                encryption when possible. In fact, it's such a bad idea that most websites
                are now using https by default.</p>

                <p>And that's great, but it also means that if you're relying on
                poorly-behaved wifi networks, it can be hard to get online.  Secure
                browsers and websites using https make it impossible for those wifi
                networks to send you to a login or payment page. Basically, those networks
                can't tap into your connection just like attackers can't. Modern browsers
                are so good that they can remember when a website supports encryption and
                even if you type in the website name, they'll use https.</p>

                <p>And if the network never redirects you to this page, well as you can
                see, you're not missing much.</p>

        <a href="https://twitter.com/neverssl">Follow @neverssl</a>

        </noscript>

        </div>
        </div>

        </body>
</html>
* Connection #0 to host neverssl.com:80 left intact
```

---

### A.3. Запит до служби доменних імен

*Windows: `Resolve-DnsName ВАШ_ДОМЕН`*

**Команда (перше виконання):**

```
Resolve-DnsName opensuse.org
```

**Вивід:**

```
Name                                           Type   TTL   Section    IPAddress
----                                           ----   ---   -------    ---------
opensuse.org                                   AAAA   2091  Answer     2a07:de40:b27e:1204::10
opensuse.org                                   A      2091  Answer     195.135.223.50
```

**Команда (повторне виконання через 5–7 хвилин):**

```
Resolve-DnsName opensuse.org
```

**Вивід:**

```
Name                                           Type   TTL   Section    IPAddress
----                                           ----   ---   -------    ---------
opensuse.org                                   AAAA   1815  Answer     2a07:de40:b27e:1204::10
opensuse.org                                   A      1815  Answer     195.135.223.50
```

**Зафіксовані значення:**

| Параметр | Перше виконання | Повторне виконання |
|---|---|---|
| Час виконання (год:хв) |17:35 |17:40 |
| IP-адреса |195.135.223.50 |195.135.223.50 |
| Значення TTL |2091 |1815 |

> Якщо друге значення TTL виявилося більшим за перше — це нормально: кеш резолвера встиг оновитися. Зафіксуйте як є.

---

### A.4. Контрольний ресурс

**Команда:**

```
curl -v https://google.com
```

**Вивід:**

```
* Host google.com:443 was resolved.
* IPv6: (none)
* IPv4: 142.250.130.102, 142.250.130.138, 142.250.130.113, 142.250.130.100, 142.250.130.101, 142.250.130.139
*   Trying 142.250.130.102:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* ALPN: server accepted http/1.1
* Established connection to google.com (142.250.130.102 port 443) from 192.168.50.166 port 5825
* using HTTP/1.x
> GET / HTTP/1.1
> Host: google.com
> User-Agent: curl/8.21.0
> Accept: */*
>
* Request completely sent off
* schannel: remote party requests renegotiation
* schannel: renegotiating SSL/TLS connection
* schannel: SSL/TLS connection renegotiated
< HTTP/1.1 301 Moved Permanently
< Location: https://www.google.com/
< Content-Type: text/html; charset=UTF-8
< Content-Security-Policy-Report-Only: object-src 'none';base-uri 'self';script-src 'nonce-7S-8WMYy6TacH7tUxNXo5w' 'strict-dynamic' 'report-sample' 'unsafe-eval' 'unsafe-inline' https: http:;report-uri https://csp.withgoogle.com/csp/gws/other-hp
< Date: Tue, 15 Sep 2026 14:42:21 GMT
< Expires: Thu, 15 Oct 2026 14:42:21 GMT
< Cache-Control: public, max-age=2592000
< Server: gws
< Content-Length: 220
< X-XSS-Protection: 0
< X-Frame-Options: SAMEORIGIN
< Alt-Svc: h3=":443"; ma=2592000,h3-29=":443"; ma=2592000
<
<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>301 Moved</TITLE></HEAD><BODY>
<H1>301 Moved</H1>
The document has moved
<A HREF="https://www.google.com/">here</A>.
</BODY></HTML>
* Connection #0 to host google.com:443 left intact
```

---

### A.5. Ресурси з некоректною конфігурацією сертифіката

**Випадок 1**

```
curl -v https://expired.badssl.com
```

```
*   Trying 104.154.89.105:443...
* Host expired.badssl.com:443 was resolved.
* IPv6: (none)
* IPv4: 104.154.89.105
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* schannel: next InitializeSecurityContext failed: SEC_E_CERT_EXPIRED (0x80090328) - Получен сертификат с истекшим сроком действия.
* closing connection #0
curl: (35) schannel: next InitializeSecurityContext failed: SEC_E_CERT_EXPIRED (0x80090328) - Получен сертификат с истекшим сроком действия.
```

**Випадок 2**

```
curl -v https://wrong.host.badssl.com
```

```
* Host wrong.host.badssl.com:443 was resolved.
* IPv6: (none)
* IPv4: 104.154.89.105
*   Trying 104.154.89.105:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* schannel: SNI or certificate check failed: SEC_E_WRONG_PRINCIPAL (0x80090322) - Главное конечное имя неверно.
* closing connection #0
curl: (60) schannel: SNI or certificate check failed: SEC_E_WRONG_PRINCIPAL (0x80090322) - Главное конечное имя неверно.
More details here: https://curl.se/docs/sslcerts.html
```

**Випадок 3**

```
curl -v https://self-signed.badssl.com
```

```
*   Trying 104.154.89.105:443...
* Host self-signed.badssl.com:443 was resolved.
* IPv6: (none)
* IPv4: 104.154.89.105
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* schannel: SEC_E_UNTRUSTED_ROOT (0x80090325) - Цепочка сертификатов выпущена центром сертификации, не имеющим доверия.
* closing connection #0
curl: (60) schannel: SEC_E_UNTRUSTED_ROOT (0x80090325) - Цепочка сертификатов выпущена центром сертификации, не имеющим доверия.
More details here: https://curl.se/docs/sslcerts.html

curl failed to verify the legitimacy of the server and therefore could not
establish a secure connection to it. To learn more about this situation and
how to fix it, please visit the webpage mentioned above.
```

> Якщо використано альтернативний спосіб із параметром `--resolve` — зазначити це та навести фактичну команду.

---

## Частина B. Власна модель рівнів

**Кількість виділених груп:** ___

| № | Назва групи (власне формулювання) | Рядки виводу, віднесені до групи | Обґрунтування |
|---|---|---|---|
| 1 |Прикладний рівень (HTTP-обмін) |> GET / HTTP/1.1 > Host: opensuse.org > User-Agent: curl/8.21.0 < HTTP/1.1 301 Moved Permanently < location: [https://www.opensuse.org/](https://www.opensuse.org/) |Формування та передача HTTP-запиту клієнтом, а також отримання HTTP-заголовків відповіді й тіла ресурсу від вебсервера. |
| 2 |Рівень шифрування та захисту (TLS/SSL) |* ALPN: curl offers http/1.1 * ALPN: server accepted http/1.1 * schannel: renegotiating SSL/TLS connection * schannel: SSL/TLS connection renegotiated Помилки: SEC_E_CERT_EXPIRED SEC_E_WRONG_PRINCIPAL SEC_E_UNTRUSTED_ROOT |Узгодження протоколу прикладного рівня, перевірка цифрового сертифіката сервера та шифрування каналу зв'язку перед передачею HTTP-даних. |
| 3 |Мережево-транспортний рівень (TCP-з'єднання) |* Trying 195.135.223.50:443... * Established connection to opensuse.org (195.135.223.50 port 443) from 192.168.50.166 port 10564 * Connection #0 to host opensuse.org:443 left intact |Встановлення з'єднання за протоколом TCP між локальним IP/портом клієнта та віддаленим IP/портом сервера. |
| 4 |Адресний рівень (DNS-резолвінг) |* Host opensuse.org:443 was resolved. * IPv4: 195.135.223.50 Записи A/AAAA та значення TTL у виводі Resolve-DnsName |Перетворення текстового доменного імені вузла у мережеву IP-адресу для подальшого встановлення мережевого з'єднання. |


*Групи впорядковано від найближчої до користувача (№ 1) до найближчої до апаратного забезпечення. Зайві рядки вилучити, за потреби — додати.*

**Рядки, які не вдалося віднести до жодної групи:**

| Рядок виводу | Причина утруднення |
|---|---|
| | |
| | |
| | |

---

## Контрольні питання

**1. Скільки рядків діагностичного виводу передує отриманню даних сторінки (завдання A.1)?**
> 
У завданні А.1 передує 15 рядків діагностики (включаючи технічні службові рядки *, > та порожній рядок розділювача >) до першого рядка відповіді сервера < HTTP/1.1 301 Moved Permanently

**2. Які рядки наявні у виводі A.1 і відсутні у виводі A.2? Чим це зумовлено?**

> 
У виводі А.2 відсутні рядки узгодження шифрування та перевірки сертифікатів (наприклад, * schannel: disabled automatic use of client certificate, * ALPN: curl offers..., * schannel: renegotiating SSL/TLS connection). Це зумовлено тим, що запит А.2 виконувався за незахищеним протоколом HTTP (порт 80), який не передбачає створення захищеного каналу TLS/SSL.

**3. Звідки у виводі з'явилося значення `443`, якщо його не було вказано в адресі?**

> 
Порт 443 є стандартним мережевим портом за замовчуванням для схеми https://. Утиліта curl автоматично підставляє цей порт при встановленні з'єднання за протоколом HTTPS, якщо він не вказаний явно в URL.

**4. Як змінилося значення TTL між двома запитами (A.3)? Що означає це число?**

> 
Значення TTL зменшилося з 2091 до 1815 (зменшення на 276 секунд за прибилзно 5 хвилин між запитами). Це число показує залишок часу життя (у секундах) запису в локальному кеші DNS-резолвера до моменту, коли знадобиться повторне звернення до авторитетного сервера.

**5. Чим відрізняються між собою три причини помилок із завдання A.5? Сформулювати кожну однією фразою.**

| Випадок | Причина недовіри |
|---|---|
| `expired` |Термін придатності цифрового сертифіката сервера вичерпано. |
| `wrong.host` |Доменне ім'я в URL-адресі не відповідає імені вузла, вказаному у структурі сертифіката. |
| `self-signed` |Сертифікат підписано самостійно або видано центру сертифікації, відсутньому в переліку довірених кореневих центрів (CA). |

**6. Три рядки з власних виводів, про які не йшлося на лекції 1:**

| № | Рядок виводу | Джерело (номер завдання) |
|---|---|---|
| 1 |* schannel: disabled automatic use of client certificate |Завдання А.1 |
| 2 |* ALPN: curl offers http/1.1 |Завдання А.1 |
| 3 |* schannel: remote party requests renegotiation |Завдання А.1 |

*Пояснення до цих рядків не потрібне.*

---

## Висновки

*150–300 слів. Спиратися на власні спостереження, а не на матеріал лекції.*

Під час виконання лабораторної роботи було досліджено послідовність етапів клієнт-серверної взаємодії за допомогою утиліт `curl` та `Resolve-DnsName`. 

**D.1. Що виявилося неочевидним або несподіваним**

Неочікуваним елементом поведінки системи виявилася поява рядка * schannel: remote party requests renegotiation під час HTTPS-запиту до opensuse.org (завдання А.1). Виявилося, що підсистема SChannel у Windows здійснює додатковий етап узгодження безпеки (TLS renegotiation) вже після передачі заголовків запиту, чого не спостерігалося при зверненні до інших HTTPS-ресурсів (наприклад, google.com).

> 

**D.2. Чому саме така кількість груп у частині B**

*На якій підставі ухвалено рішення. Що змусило б його змінити.*

Модель взаємодії було розділено на 4 групи (DNS, TCP, TLS/SSL, HTTP) на основі чіткого функціонального розмежування спостережуваних артефактів: від визначення IP-адреси та встановлення сокета до шифрування каналу та передачі прикладних даних.
> 

**D.3. Питання, яке залишилося без відповіді**

Чому саме вебсервер opensuse.org вимагає повторного узгодження TLS (renegotiation) під час кожного запиту, тоді як інші ресурси (наприклад, google.com) цього не роблять?
> 

---

## Використання штучного інтелекту

*Розділ обов'язковий. Заповнюється незалежно від того, чи використовувався ШІ. Детальні вимоги — у документі «Політика використання технологій штучного інтелекту».*

**Факт використання:** використано / не використано *(потрібне залишити)*

**Установлений рівень для цієї роботи:** Р3 — ШІ як співвиконавець

**Фактичний рівень використання:** Р___

### Використані системи

| Система | Версія або модель | Період використання |
|---|---|---|
|Gemini |3.1 Pro |17:55-18:15 |

### Промпти

*Наводити дослівно, у тому вигляді, у якому запит було надано системі. Переказ не приймається.*

| № | Розділ роботи | Текст промпта |
|---|---|---|
| 1 |Частина В  |поясни мені будь ласка як поділити группи в частині В за якими критеріями |


### Дії з отриманим результатом

| № промпта | Що перевірено | Що змінено | Що відхилено і чому |
|---|---|---|---|
| 1 |Він допоміг мені класифікувати группи за певними критеріями і пояснив чому вони мають бути саме такими |Змінена таблиця частини В в якій вказані пояснення такого вибору | |
### Підтвердження

Підтверджую, що всі наведені в цьому звіті виводи команд отримано мною особисто внаслідок фактичного виконання відповідних дій, а відомості цього розділу є повними та достовірними.

> Виводи `curl`, `dig` та інші артефакти не можуть бути згенеровані. Це стосується будь-якого рівня використання ШІ.

---

## Примітки виконавця

*(необов'язковий розділ: що не спрацювало, які команди довелося змінити, які виникли труднощі)*

> 

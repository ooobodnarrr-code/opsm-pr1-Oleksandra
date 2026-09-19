# Практична робота № 1

**Дисципліна:** Основи побудови інформаційних систем та мереж

**Тема:** Спостереження за процесом звернення до вебресурсу. Побудова власної моделі рівнів взаємодії

| | |
|---|---|
| **Прізвище, ім'я** |Боднар Олександра|
| **Група** |2.02|
| **Номер варіанта** |2|
| **Домен варіанта** |arin.net|
| **Середовище виконання** | *(Window)* |
| **Версія curl** |curl 8.21.0 (Windows) libcurl/8.21.0 Schannel zlib/1.3.2 WinIDN WinLDAP|
| **Дата виконання** |18.09.2026|

---

## Частина A. Збір експериментальних даних

### A.1. Запит із діагностичним виводом

**Команда:**

```
curl -v https://example.org
```

**Вивід:**

```
* Host arin.net:443 was resolved.
* IPv6: (none)
* IPv4: 192.149.252.47, 199.43.0.47
*   Trying 192.149.252.47:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* ALPN: server did not agree on a protocol. Uses default.
* Established connection to arin.net (192.149.252.47 port 443) from 192.168.0.102 port 64217
* using HTTP/1.x
> GET / HTTP/1.1
> Host: arin.net
> User-Agent: curl/8.21.0
> Accept: */*
>
* Request completely sent off
< HTTP/1.1 301 Moved Permanently
< Server: nginx
< Date: Fri, 18 Sep 2026 14:14:04 GMT
< Content-Type: text/html
< Content-Length: 162
< Connection: keep-alive
< Location: https://www.arin.net/
< Strict-Transport-Security: max-age=32140800; includeSubDomains
< X-Frame-Options: SAMEORIGIN
<
<html>
<head><title>301 Moved Permanently</title></head>
<body>
<center><h1>301 Moved Permanently</h1></center>
<hr><center>nginx</center>
</body>
</html>
* Connection #0 to host arin.net:443 left intact
```

---

### A.2. Запит без захисту з'єднання

**Команда:**

```
curl -v http://neverssl.com
```

**Вивід:**

```
* Host arin.net:443 was resolved.
* IPv6: (none)
* IPv4: 199.43.0.47, 192.149.252.47
*   Trying 199.43.0.47:443...
*   Trying 192.149.252.47:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* ALPN: server did not agree on a protocol. Uses default.
* Established connection to arin.net (199.43.0.47 port 443) from 192.168.0.102 port 52901
* using HTTP/1.x
> GET / HTTP/1.1
> Host: arin.net
> User-Agent: curl/8.21.0
> Accept: */*
>
* Request completely sent off
< HTTP/1.1 301 Moved Permanently
< Server: nginx
< Date: Fri, 18 Sep 2026 14:16:31 GMT
< Content-Type: text/html
< Content-Length: 162
< Connection: keep-alive
< Location: https://www.arin.net/
< Strict-Transport-Security: max-age=32140800; includeSubDomains
< X-Frame-Options: SAMEORIGIN
<
<html>
<head><title>301 Moved Permanently</title></head>
<body>
<center><h1>301 Moved Permanently</h1></center>
<hr><center>nginx</center>
</body>
</html>
* Connection #0 to host arin.net:443 left intact
PS C:\Users\Admin> curl.exe -v http://neverssl.com
*   Trying 34.223.124.45:80...
* Host neverssl.com:80 was resolved.
* IPv6: (none)
* IPv4: 34.223.124.45
* Established connection to neverssl.com (34.223.124.45 port 80) from 192.168.0.102 port 52903
* using HTTP/1.x
> GET / HTTP/1.1
> Host: neverssl.com
> User-Agent: curl/8.21.0
> Accept: */*
>
* Request completely sent off
< HTTP/1.1 200 OK
< Date: Fri, 18 Sep 2026 14:17:26 GMT
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
dig ВАШ_ДОМЕН
```

**Вивід:**

```
Name                                           Type   TTL   Section    IPAddress
----                                           ----   ---   -------    ---------
arin.net                                       AAAA   60    Answer     2001:500:4:201::47
arin.net                                       AAAA   60    Answer     2620:d0:6000:502::47
arin.net                                       A      60    Answer     192.149.252.47
arin.net                                       A      60    Answer     199.43.0.47

```

**Команда (повторне виконання через 5–7 хвилин):**

```
dig ВАШ_ДОМЕН
```

**Вивід:**

```
Name                                           Type   TTL   Section    IPAddress
----                                           ----   ---   -------    ---------
arin.net                                       AAAA   60    Answer     2001:500:4:201::47
arin.net                                       AAAA   60    Answer     2620:d0:6000:502::47
arin.net                                       A      0     Answer     192.149.252.47
```

**Зафіксовані значення:**

| Параметр | Перше виконання | Повторне виконання |
|---|---|---|
| Час виконання (год:хв) |17:29|17:35 |
| IP-адреса | 2001:500:4:201::4, 2620:d0:6000:502::47, 192.149.252, 199.43.0.47| 2001:500:4:201::47, 2620:d0:6000:502::47, 192.149.252.47|
| Значення TTL |60 60 60 60|60 60 0 |

> Якщо друге значення TTL виявилося більшим за перше — це нормально: кеш резолвера встиг оновитися. Зафіксуйте як є.

---

### A.4. Контрольний ресурс

**Команда:**

```
curl -v https://google.com
```

**Вивід:**

```
*   Trying 142.250.109.113:443...
* Host google.com:443 was resolved.
* IPv6: (none)
* IPv4: 142.250.109.113
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* ALPN: server accepted http/1.1
* Established connection to google.com (142.250.109.113 port 443) from 192.168.0.102 port 56141
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
< Content-Security-Policy-Report-Only: object-src 'none';base-uri 'self';script-src 'nonce-zslZE9xg4ANb1GbVFK4JfQ' 'strict-dynamic' 'report-sample' 'unsafe-eval' 'unsafe-inline' https: http:;report-uri https://csp.withgoogle.com/csp/gws/other-hp
< Date: Fri, 18 Sep 2026 14:48:49 GMT
< Expires: Sun, 18 Oct 2026 14:48:49 GMT
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
* schannel: next InitializeSecurityContext failed: SEC_E_CERT_EXPIRED (0x80090328) - The received certificate has expired.
* closing connection #0
curl: (35) schannel: next InitializeSecurityContext failed: SEC_E_CERT_EXPIRED (0x80090328) - The received certificate has expired.
```

**Випадок 2**

```
curl -v https://wrong.host.badssl.com
```

```
*   Trying 104.154.89.105:443...
* Host wrong.host.badssl.com:443 was resolved.
* IPv6: (none)
* IPv4: 104.154.89.105
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* schannel: SNI or certificate check failed: SEC_E_WRONG_PRINCIPAL (0x80090322) - The target principal name is incorrect.
* closing connection #0
curl: (60) schannel: SNI or certificate check failed: SEC_E_WRONG_PRINCIPAL (0x80090322) - The target principal name is incorrect.
More details here: https://curl.se/docs/sslcerts.html

curl failed to verify the legitimacy of the server and therefore could not
establish a secure connection to it. To learn more about this situation and
how to fix it, please visit the webpage mentioned above.
```

**Випадок 3**

```
curl -v https://self-signed.badssl.com
```

```
* Host self-signed.badssl.com:443 was resolved.
* IPv6: (none)
* IPv4: 104.154.89.105
*   Trying 104.154.89.105:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* schannel: SEC_E_UNTRUSTED_ROOT (0x80090325) - The certificate chain was issued by an authority that is not trusted.
* closing connection #0
curl: (60) schannel: SEC_E_UNTRUSTED_ROOT (0x80090325) - The certificate chain was issued by an authority that is not trusted.
More details here: https://curl.se/docs/sslcerts.html

curl failed to verify the legitimacy of the server and therefore could not
establish a secure connection to it. To learn more about this situation and
how to fix it, please visit the webpage mentioned above.`
```

> Якщо використано альтернативний спосіб із параметром `--resolve` — зазначити це та навести фактичну команду.

---

## Частина B. Власна модель рівнів

**Кількість виділених груп:** ___

| № | Назва групи (власне формулювання) | Рядки виводу, віднесені до групи | Обґрунтування |
|---|---|---|---|
| 1 |Вміст та HTML-структура|```html``` ```title``` ```body``` ```hr``` ```centre``` nginx|Безпосереднє корисне навантаження (HTML-код сторінки), яке сервер передає клієнту|
| 2 |Службовий HTTP-обмін | ```GET / HTTP/1.1, Host: arin.net, HTTP/1.1 301 Moved Permanently, Location: [https://www.arin.net/](https://www.arin.net/)З```| Заголовки запиту від клієнта та відповіді сервера зі статус-кодом перенаправлення|
| 3 |Налаштування безпеки та TLS|```schannel: disabled automatic..., ALPN: curl offers http/1.1, ALPN: server did not agree...```|Узгодження захищеного з'єднання, вибір протоколу шифрування та перевірка сертифікатів.|
| 4 |Встановлення TCP-сесії |``` Trying 199.43.0.47:443..., * Established connection to arin.net (199.43.0.47 port 443)...```| Процес відкриття та підтвердження мережевого з'єднання (сокета) з конкретним портом 443.|
| 5 | Перетворення домену (DNS-трансляція)|```* Trying 199.43.0.47:443..., * Established connection to arin.net (199.43.0.47 port 443)...``` |Переклад текстового імені сайту ```arin.net``` у список його мережевих IP-адрес|
| 6 |Параметри та деталі DNS-сервера | ```Type: A, TTL: 60, Section: Answer, IPAddress: 192.149.252.47```|Детальна інформація з виводу DNS-запиту: час кешування (TTL), тип запису та IP.|
| 7 |Параметри системного оточення|```User-Agent: curl/8.21.0, Server: nginx, 192.168.0.102 port 52901```|Дані про версію утиліти ```curl```, веб-сервер та локальну IP-адресу клієнтського пристрою.|

*Групи впорядковано від найближчої до користувача (№ 1) до найближчої до апаратного забезпечення. Зайві рядки вилучити, за потреби — додати.*

**Рядки, які не вдалося віднести до жодної групи:**

| Рядок виводу | Причина утруднення |
|---|---|
|```Request completely sent off``` |Внутрішній сповіщувач утиліти curl.exe про завершення надсилання запиту. Повідомлення описує процес роботи самої програми, а не стан мережевого протоколу. | 
|```Connection #0 to host arin.net:443 left intact``` |Зв'язок не розривався. Програма залишила з'єднання відкритим (Keep-Alive), щоб не витрачати час на повторне підключення, якщо знадобиться відправити ще один запит. |
---

## Контрольні питання

**1. Скільки рядків діагностичного виводу передує отриманню даних сторінки (завдання A.1)?**

> У завданні A.1 перед відображенням HTML-коду сторінки виводиться 19 службових рядків, які містять інформацію про встановлення з’єднання, HTTP-запит і відповідь сервера.


**2. Які рядки наявні у виводі A.1 і відсутні у виводі A.2? Чим це зумовлено?**

> У A.1 немає рядка `* Trying 199.43.0.47:443...`, тому що підключення одразу відбулося до IP-адреси `192.149.252.47`. У A.2 спочатку була спроба підключення до `199.43.0.47`, а потім до `192.149.252.47`. Це пов’язано з тим, що сайт має дві IP-адреси, і curl може використовувати їх у різному порядку.


**3. Звідки у виводі з'явилося значення `443`, якщо його не було вказано в адресі?**

> Число ```443``` у виводі з’явилося тому, що під час підключення використовується протокол HTTPS. Для HTTPS стандартним є порт ```443```, тому його не потрібно окремо вказувати в адресі сайту. ```Програма curl автоматично визначає потрібний порт за протоколом і використовує 443 для встановлення з’єднання з сервером.```

**4. Як змінилося значення TTL між двома запитами (A.3)? Що означає це число?**

> TTL змінився з 60 до 0 секунд саме для запису типу `A` з IP-адресою `192.149.252.47`. TTL показує, скільки часу цей DNS-запис може зберігатися в кеші. Під час першого запиту залишалося 60 секунд, а через 5 хвилин значення стало 0, тобто час дії запису закінчився. Після цього DNS-запис потрібно оновити.


**5. Чим відрізняються між собою три причини помилок із завдання A.5? Сформулювати кожну однією фразою.**

| Випадок | Причина недовіри |
|---|---|
| `expired` |Сертифікат сайту прострочений, тобто закінчився термін його дії. (The received certificate has expired)|
| `wrong.host` |Сертифікат виданий для іншого доменного імені, тому ім’я сайту не збігається із сертифікатом.(The target principal name is incorrect)|
| `self-signed` |Сертифікат підписаний самим сервером, а не довіреним центром сертифікаці (The certificate chain was issued by an authority that is not trusted.)|

**6. Три рядки з власних виводів, про які не йшлося на лекції 1:**

| № | Рядок виводу | Джерело (номер завдання) |
|---|---|---|
| 1 | < ETag: "f79-5e28b29d38e93"|А.2 |
| 2 |* schannel: remote party requests renegotiation|А.4 |
| 3 |< Vary: Accept-Encoding|А.2 |

*Пояснення до цих рядків не потрібне.*

---

## Висновки

*150–300 слів. Спиратися на власні спостереження, а не на матеріал лекції.*

**D.1. Що виявилося неочевидним або несподіваним**

*Назвати конкретно, з посиланням на рядок виводу.*

>Найбільш неочевидним під час виконання дослідження виявився обсяг службових операцій, які відбуваються «за лаштунками» до моменту отримання тексту сторінки. У завданні A.1 перед виводом безпосереднього HTML-коду утиліта зафіксувала 19 службових рядків. Зокрема, вразила кількість дій на етапі встановлення з'єднання: від розпізнавання IP-адреси (Host arin.net:443 was resolved) та спроб підключення ```(Trying 192.149.252.47:443...)``` до узгодження параметрів шифрування (ALPN: curl offers http/1.1) і обміну HTTP-заголовками. У повсякденному користуванні мережею цей багаторівневий процес залишається непомітним за миттєвим завантаженням сторінки у браузері.


**D.2. Чому саме така кількість груп у частині B**

*На якій підставі ухвалено рішення. Що змусило б його змінити.*

> Рішення розділити вивід на 7 груп ухвалено на основі чіткого розмежування зон відповідальності учасників мережевого обміну: хто з ким взаємодіє та на якому етапі. Окремо було виділено користувацький вміст (HTML), службовий HTTP-транспорт, шифрування (TLS), системний рівень (TCP-сесія), DNS-трансляцію, специфічні атрибути DNS та параметри оточення. Змінити кількість груп у бік зменшення змусила б потреба в спрощеній моделі — наприклад, об'єднання TLS та TCP в один загальний «рівень захищеного зв'язку». Збільшити кількість груп довелося б у разі появи у виводі додаткових протоколів (securer-посередників, проксі чи розширених параметрів HTTP/2).

**D.3. Питання, яке залишилося без відповіді**

> Я звернула увагу на те, що значення TTL при повторному DNS-запиті зменшилося до 0. Мені цікаво дізнатися детальніше, як саме Windows працює з кешем DN

---

## Використання штучного інтелекту

*Розділ обов'язковий. Заповнюється незалежно від того, чи використовувався ШІ. Детальні вимоги — у документі «Політика використання технологій штучного інтелекту».*

**Факт використання:** використано 

**Установлений рівень для цієї роботи:** Р3 — ШІ як співвиконавець

**Фактичний рівень використання:** Р3 — ШІ як співвиконавець

### Використані системи

| Система | Версія або модель | Період використання |
|---|---|---|
|GPT|5.6 Luna. |18-19.09.2026 |
|Gemini|2.0 |18-19.09.2026 |

### Промпти

*Наводити дослівно, у тому вигляді, у якому запит було надано системі. Переказ не приймається.*

| № | Розділ роботи | Текст промпта |
|---|---|---|
| 1 |Частина В|відштовхуючись від матеріалу поясни як зробити це завдання простими словами |
| 2 |Частина D|сформуй думку |
| 3 |Все|поясни чому тут так |

### Дії з отриманим результатом

| № промпта | Що перевірено | Що змінено | Що відхилено і чому |
|---|---|---|---|
| 1 |Правильність підрахунку та визначення рядків у виводі curl |Уточнено кількість рядків відповідно до наведеного виводу|Неправильний варіант підрахунку, оскільки враховував не всі потрібні рядки |
| 2 |Значення портів, TTL та IP-адрес у результатах команд|Відповідь сформульовано простішими словами|Занадто складні пояснення, оскільки вони були незручними для використання|
| 3 |Три рядки з власних виводів, про які не йшлося на лекції 1|Уточнено, що ці рядки взяті з виводів  |- |

### Підтвердження

Підтверджую, що всі наведені в цьому звіті виводи команд отримано мною особисто внаслідок фактичного виконання відповідних дій, а відомості цього розділу є повними та достовірними.

> Виводи `curl`, `dig` та інші артефакти не можуть бути згенеровані. Це стосується будь-якого рівня використання ШІ.

---

## Примітки виконавця

*(необов'язковий розділ: що не спрацювало, які команди довелося змінити, які виникли труднощі)*

> Цю роботу я виконувала вперше, тому під час виконання мені була потрібна додаткова допомога. Для цього я використовувала ШІ та навчальні відео на YouTube. Я не просто копіювала готові відповіді, а просила пояснити незрозумілі моменти, розбиралася з командами та результатами їх виконання. Намагалася самостійно зрозуміти, що саме я роблю і чому отримую такий результат. Для мене важливо не лише виконати роботу, а й розібратися в матеріалі, щоб надалі мати змогу виконувати подібні завдання самостійно.

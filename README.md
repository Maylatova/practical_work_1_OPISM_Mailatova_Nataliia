# Практична робота № 1

**Дисципліна:** Основи побудови інформаційних систем та мереж

**Тема:** Спостереження за процесом звернення до вебресурсу. Побудова власної моделі рівнів взаємодії

| | |
|---|---|
| **Прізвище, ім'я** | **Майлатова Наталія** |
| **Група** | **ЗПІ-21** |
| **Номер варіанта** | **5** |
| **Домен варіанта** | **rfc-editor.org**  |
| **Середовище виконання** | **Linux** |
| **Версія curl** | **curl 7.81.0** |
| **Дата виконання** | **17.11.2026** |

---

## Частина A. Збір експериментальних даних

### A.1. Запит із діагностичним виводом

**Команда:**

```
curl -v https://rfc-editor.org
```

**Вивід:**

```
*   Trying 104.18.20.81:443...
* Connected to rfc-editor.org (104.18.20.81) port 443 (#0)
* ALPN, offering h2
* ALPN, offering http/1.1
*  CAfile: /etc/ssl/certs/ca-certificates.crt
*  CApath: /etc/ssl/certs
* TLSv1.0 (OUT), TLS header, Certificate Status (22):
* TLSv1.3 (OUT), TLS handshake, Client hello (1):
* TLSv1.2 (IN), TLS header, Certificate Status (22):
* TLSv1.3 (IN), TLS handshake, Server hello (2):
* TLSv1.2 (IN), TLS header, Finished (20):
* TLSv1.2 (IN), TLS header, Supplemental data (23):
* TLSv1.3 (IN), TLS handshake, Encrypted Extensions (8):
* TLSv1.3 (IN), TLS handshake, Certificate (11):
* TLSv1.3 (IN), TLS handshake, CERT verify (15):
* TLSv1.3 (IN), TLS handshake, Finished (20):
* TLSv1.2 (OUT), TLS header, Finished (20):
* TLSv1.3 (OUT), TLS change cipher, Change cipher spec (1):
* TLSv1.2 (OUT), TLS header, Supplemental data (23):
* TLSv1.3 (OUT), TLS handshake, Finished (20):
* SSL connection using TLSv1.3 / TLS_AES_256_GCM_SHA384
* ALPN, server accepted to use h2
* Server certificate:
*  subject: CN=rfc-editor.org
*  start date: Oct 22 10:04:04 2026 GMT
*  expire date: Jan 20 11:04:01 2027 GMT
*  subjectAltName: host "rfc-editor.org" matched cert's "rfc-editor.org"
*  issuer: C=US; O=Google Trust Services; CN=WE1
*  SSL certificate verify ok.
* Using HTTP2, server supports multiplexing
* Connection state changed (HTTP/2 confirmed)
* Copying HTTP/2 data in stream buffer to connection buffer after upgrade: len=0
* TLSv1.2 (OUT), TLS header, Supplemental data (23):
* TLSv1.2 (OUT), TLS header, Supplemental data (23):
* TLSv1.2 (OUT), TLS header, Supplemental data (23):
* Using Stream ID: 1 (easy handle 0x642feb84da90)
* TLSv1.2 (OUT), TLS header, Supplemental data (23):
> GET / HTTP/2
> Host: rfc-editor.org
> user-agent: curl/7.81.0
> accept: */*
> 
* TLSv1.2 (IN), TLS header, Supplemental data (23):
* TLSv1.3 (IN), TLS handshake, Newsession Ticket (4):
* TLSv1.3 (IN), TLS handshake, Newsession Ticket (4):
* old SSL session ID is stale, removing
* TLSv1.2 (IN), TLS header, Supplemental data (23):
* Connection state changed (MAX_CONCURRENT_STREAMS == 256)!
* TLSv1.2 (OUT), TLS header, Supplemental data (23):
* TLSv1.2 (IN), TLS header, Supplemental data (23):
< HTTP/2 301 
< date: Tue, 17 Nov 2026 19:05:47 GMT
< content-type: text/html; charset=UTF-8
< location: https://www.rfc-editor.org/
< server: cloudflare
< cf-ray: a5c1024789155b17-WAW
< alt-svc: h3=":443"; ma=86400
< 
* TLSv1.2 (IN), TLS header, Supplemental data (23):
<html>
<head><title>301 Moved Permanently</title></head>
<body>
<center><h1>301 Moved Permanently</h1></center>
<hr><center>cloudflare</center>
</body>
</html>
* TLSv1.2 (IN), TLS header, Supplemental data (23):
* Connection #0 to host rfc-editor.org left intact

```

---

### A.2. Запит без захисту з'єднання

**Команда:**

```
curl -v http://neverssl.com
```

**Вивід:**

```
*   Trying 34.223.124.45:80...
*   Trying 2600:1f13:37c:1400:ba21:7165:5fc7:736e:80...
* Immediate connect fail for 2600:1f13:37c:1400:ba21:7165:5fc7:736e: Network is unreachable
* Connected to neverssl.com (34.223.124.45) port 80 (#0)
> GET / HTTP/1.1
> Host: neverssl.com
> User-Agent: curl/7.81.0
> Accept: */*
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
< Date: Tue, 17 Nov 2026 19:06:55 GMT
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

			var nouns =	  [ 'day', 'dawn', 'peace', 'smile', 'love', 'zen', 'laugh',
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
* Connection #0 to host neverssl.com left intact

```

---

### A.3. Запит до служби доменних імен

*Windows: `Resolve-DnsName ВАШ_ДОМЕН`*

**Команда (перше виконання):**

```
dig rfc-editor.org
```

**Вивід:**

```
; <<>> DiG 9.18.39-0ubuntu0.22.04.4-Ubuntu <<>> rfc-editor.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 29549
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;rfc-editor.org.			IN	A

;; ANSWER SECTION:
rfc-editor.org.		145	IN	A	104.18.21.81
rfc-editor.org.		145	IN	A	104.18.20.81

;; Query time: 0 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Tue Nov 17 21:08:22 EET 2026
;; MSG SIZE  rcvd: 75

```

**Команда (повторне виконання через 5–7 хвилин):**

```
dig rfc-editor.org
```

**Вивід:**

```
; <<>> DiG 9.18.39-0ubuntu0.22.04.4-Ubuntu <<>> rfc-editor.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 21711
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;rfc-editor.org.			IN	A

;; ANSWER SECTION:
rfc-editor.org.		300	IN	A	104.18.21.81
rfc-editor.org.		300	IN	A	104.18.20.81

;; Query time: 17 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Tue Nov 17 21:16:18 EET 2026
;; MSG SIZE  rcvd: 75

```

**Зафіксовані значення:**

| Параметр | Перше виконання | Повторне виконання |
|---|---|---|
| Час виконання (год:хв) | 21:08 | 21:16 |
| IP-адреса | 104.18.21.81; 104.18.20.81 | 104.18.21.81; 104.18.20.81 |
| Значення TTL | 145 | 300 |

> Якщо друге значення TTL виявилося більшим за перше — це нормально: кеш резолвера встиг оновитися. Зафіксуйте як є.

---

### A.4. Контрольний ресурс

**Команда:**

```
curl -v https://google.com
```

**Вивід:**

```
*   Trying 142.250.120.102:443...
* Connected to google.com (142.250.120.102) port 443 (#0)
* ALPN, offering h2
* ALPN, offering http/1.1
*  CAfile: /etc/ssl/certs/ca-certificates.crt
*  CApath: /etc/ssl/certs
* TLSv1.0 (OUT), TLS header, Certificate Status (22):
* TLSv1.3 (OUT), TLS handshake, Client hello (1):
* TLSv1.2 (IN), TLS header, Certificate Status (22):
* TLSv1.3 (IN), TLS handshake, Server hello (2):
* TLSv1.2 (IN), TLS header, Finished (20):
* TLSv1.2 (IN), TLS header, Supplemental data (23):
* TLSv1.3 (IN), TLS handshake, Encrypted Extensions (8):
* TLSv1.3 (IN), TLS handshake, Certificate (11):
* TLSv1.3 (IN), TLS handshake, CERT verify (15):
* TLSv1.3 (IN), TLS handshake, Finished (20):
* TLSv1.2 (OUT), TLS header, Finished (20):
* TLSv1.3 (OUT), TLS change cipher, Change cipher spec (1):
* TLSv1.2 (OUT), TLS header, Supplemental data (23):
* TLSv1.3 (OUT), TLS handshake, Finished (20):
* SSL connection using TLSv1.3 / TLS_AES_256_GCM_SHA384
* ALPN, server accepted to use h2
* Server certificate:
*  subject: CN=*.google.com
*  start date: Nov  3 08:26:50 2026 GMT
*  expire date: Jan 26 08:26:49 2027 GMT
*  subjectAltName: host "google.com" matched cert's "google.com"
*  issuer: C=US; O=Google Trust Services; CN=WE2
*  SSL certificate verify ok.
* Using HTTP2, server supports multiplexing
* Connection state changed (HTTP/2 confirmed)
* Copying HTTP/2 data in stream buffer to connection buffer after upgrade: len=0
* TLSv1.2 (OUT), TLS header, Supplemental data (23):
* TLSv1.2 (OUT), TLS header, Supplemental data (23):
* TLSv1.2 (OUT), TLS header, Supplemental data (23):
* Using Stream ID: 1 (easy handle 0x5c2cc8aada90)
* TLSv1.2 (OUT), TLS header, Supplemental data (23):
> GET / HTTP/2
> Host: google.com
> user-agent: curl/7.81.0
> accept: */*
> 
* TLSv1.2 (IN), TLS header, Supplemental data (23):
* TLSv1.3 (IN), TLS handshake, Newsession Ticket (4):
* TLSv1.3 (IN), TLS handshake, Newsession Ticket (4):
* old SSL session ID is stale, removing
* TLSv1.2 (IN), TLS header, Supplemental data (23):
* TLSv1.2 (OUT), TLS header, Supplemental data (23):
* TLSv1.2 (IN), TLS header, Supplemental data (23):
* TLSv1.2 (IN), TLS header, Supplemental data (23):
< HTTP/2 301 
< location: https://www.google.com/
< content-type: text/html; charset=UTF-8
< content-security-policy-report-only: object-src 'none';base-uri 'self';script-src 'nonce-qstP4xhQK3mDnK6PZkqi7g' 'strict-dynamic' 'report-sample' 'unsafe-eval' 'unsafe-inline' https: http:;report-uri https://csp.withgoogle.com/csp/gws/other-hp
< date: Tue, 17 Nov 2026 19:19:52 GMT
< expires: Thu, 17 Dec 2026 19:19:52 GMT
< cache-control: public, max-age=2592000
< server: gws
< content-length: 220
< x-xss-protection: 0
< x-frame-options: SAMEORIGIN
< alt-svc: h3=":443"; ma=2592000,h3-29=":443"; ma=2592000
< 
* TLSv1.2 (IN), TLS header, Supplemental data (23):
<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>301 Moved</TITLE></HEAD><BODY>
<H1>301 Moved</H1>
The document has moved
<A HREF="https://www.google.com/">here</A>.
</BODY></HTML>
* TLSv1.2 (IN), TLS header, Supplemental data (23):
* TLSv1.2 (OUT), TLS header, Supplemental data (23):
* Connection #0 to host google.com left intact

```

---

### A.5. Ресурси з некоректною конфігурацією сертифіката

**Випадок 1**

```
curl -v https://expired.badssl.com
```

```
*   Trying 104.154.89.105:443...
* Connected to expired.badssl.com (104.154.89.105) port 443 (#0)
* ALPN, offering h2
* ALPN, offering http/1.1
*  CAfile: /etc/ssl/certs/ca-certificates.crt
*  CApath: /etc/ssl/certs
* TLSv1.0 (OUT), TLS header, Certificate Status (22):
* TLSv1.3 (OUT), TLS handshake, Client hello (1):
* TLSv1.2 (IN), TLS header, Certificate Status (22):
* TLSv1.3 (IN), TLS handshake, Server hello (2):
* TLSv1.2 (IN), TLS header, Certificate Status (22):
* TLSv1.2 (IN), TLS handshake, Certificate (11):
* TLSv1.2 (OUT), TLS header, Unknown (21):
* TLSv1.2 (OUT), TLS alert, certificate expired (557):
* SSL certificate problem: certificate has expired
* Closing connection 0
curl: (60) SSL certificate problem: certificate has expired
More details here: https://curl.se/docs/sslcerts.html

curl failed to verify the legitimacy of the server and therefore could not
establish a secure connection to it. To learn more about this situation and
how to fix it, please visit the web page mentioned above.

```

**Випадок 2**

```
curl -v https://wrong.host.badssl.com
```

```
*   Trying 104.154.89.105:443...
* Connected to wrong.host.badssl.com (104.154.89.105) port 443 (#0)
* ALPN, offering h2
* ALPN, offering http/1.1
*  CAfile: /etc/ssl/certs/ca-certificates.crt
*  CApath: /etc/ssl/certs
* TLSv1.0 (OUT), TLS header, Certificate Status (22):
* TLSv1.3 (OUT), TLS handshake, Client hello (1):
* TLSv1.2 (IN), TLS header, Certificate Status (22):
* TLSv1.3 (IN), TLS handshake, Server hello (2):
* TLSv1.2 (IN), TLS header, Certificate Status (22):
* TLSv1.2 (IN), TLS handshake, Certificate (11):
* TLSv1.2 (IN), TLS header, Certificate Status (22):
* TLSv1.2 (IN), TLS handshake, Server key exchange (12):
* TLSv1.2 (IN), TLS header, Certificate Status (22):
* TLSv1.2 (IN), TLS handshake, Server finished (14):
* TLSv1.2 (OUT), TLS header, Certificate Status (22):
* TLSv1.2 (OUT), TLS handshake, Client key exchange (16):
* TLSv1.2 (OUT), TLS header, Finished (20):
* TLSv1.2 (OUT), TLS change cipher, Change cipher spec (1):
* TLSv1.2 (OUT), TLS header, Certificate Status (22):
* TLSv1.2 (OUT), TLS handshake, Finished (20):
* TLSv1.2 (IN), TLS header, Finished (20):
* TLSv1.2 (IN), TLS header, Certificate Status (22):
* TLSv1.2 (IN), TLS handshake, Finished (20):
* SSL connection using TLSv1.2 / ECDHE-RSA-AES128-GCM-SHA256
* ALPN, server accepted to use http/1.1
* Server certificate:
*  subject: CN=*.badssl.com
*  start date: Sep 29 20:02:56 2026 GMT
*  expire date: Dec 28 20:02:55 2026 GMT
*  subjectAltName does not match wrong.host.badssl.com
* SSL: no alternative certificate subject name matches target host name 'wrong.host.badssl.com'
* Closing connection 0
* TLSv1.2 (OUT), TLS header, Unknown (21):
* TLSv1.2 (OUT), TLS alert, close notify (256):
curl: (60) SSL: no alternative certificate subject name matches target host name 'wrong.host.badssl.com'
More details here: https://curl.se/docs/sslcerts.html

curl failed to verify the legitimacy of the server and therefore could not
establish a secure connection to it. To learn more about this situation and
how to fix it, please visit the web page mentioned above.

```

**Випадок 3**

```
curl -v https://self-signed.badssl.com
```

```
*   Trying 104.154.89.105:443...
* Connected to self-signed.badssl.com (104.154.89.105) port 443 (#0)
* ALPN, offering h2
* ALPN, offering http/1.1
*  CAfile: /etc/ssl/certs/ca-certificates.crt
*  CApath: /etc/ssl/certs
* TLSv1.0 (OUT), TLS header, Certificate Status (22):
* TLSv1.3 (OUT), TLS handshake, Client hello (1):
* TLSv1.2 (IN), TLS header, Certificate Status (22):
* TLSv1.3 (IN), TLS handshake, Server hello (2):
* TLSv1.2 (IN), TLS header, Certificate Status (22):
* TLSv1.2 (IN), TLS handshake, Certificate (11):
* TLSv1.2 (OUT), TLS header, Unknown (21):
* TLSv1.2 (OUT), TLS alert, unknown CA (560):
* SSL certificate problem: self-signed certificate
* Closing connection 0
curl: (60) SSL certificate problem: self-signed certificate
More details here: https://curl.se/docs/sslcerts.html

curl failed to verify the legitimacy of the server and therefore could not
establish a secure connection to it. To learn more about this situation and
how to fix it, please visit the web page mentioned above.

```

> Якщо використано альтернативний спосіб із параметром `--resolve` — зазначити це та навести фактичну команду.

---

## Частина B. Власна модель рівнів

**Кількість виділених груп:** 6

| № | Назва групи (власне формулювання) | Рядки виводу, віднесені до групи | Обґрунтування |
|---|---|---|---|
| 1 | Вміст відповіді застосунку | A.1: `> GET / HTTP/2`, `< HTTP/2 301`, `< location: https://www.rfc-editor.org/`, тіло `<html>...301 Moved Permanently...`; A.2: `> GET / HTTP/1.1`, `< HTTP/1.1 200 OK`, `< Content-Length: 3961`, повне тіло сторінки NeverSSL; A.4: `> GET / HTTP/2`, `< HTTP/2 301`, `< location: https://www.google.com/`, тіло `<HTML>...301 Moved...` | Це рядки, які відповідають на запит користувача. Вони несуть текст сторінки або код переадресації. |
| 2 | Узгодження прикладного протоколу | A.1/A.4: `ALPN, offering h2`, `ALPN, offering http/1.1`, `ALPN, server accepted to use h2`, `Using HTTP2, server supports multiplexing`, `Connection state changed (HTTP/2 confirmed)`, `Using Stream ID: 1 (easy handle ...)`, `Connection state changed (MAX_CONCURRENT_STREAMS == 256)!`; A.2: `Mark bundle as not supporting multiuse` | Ці рядки фіксують, якою версією HTTP і в якому режимі домовилися обмінюватися клієнт і сервер. |
| 3 | Встановлення захищеного каналу (TLS-рукостискання) | A.1/A.4: `TLS handshake, Client hello (1)`, `Server hello (2)`, `Encrypted Extensions (8)`, `CERT verify (15)`, `Finished (20)`, `TLS change cipher, Change cipher spec (1)`, `SSL connection using TLSv1.3 / TLS_AES_256_GCM_SHA384`, `Newsession Ticket (4)`; A.5 (усі три випадки): `Client hello (1)`, `Server hello (2)` | Рядки описують саму процедуру узгодження шифрів і ключів між клієнтом і сервером. Вона відбувається однаково незалежно від того, якому сайту зрештою дадуть довіру. |
| 4 | Перевірка довіри до сертифіката сервера | A.1/A.4: `Server certificate: subject: CN=...`, `start date`, `expire date`, `subjectAltName host "..." matched cert's "..."`, `issuer:`, `SSL certificate verify ok.`; A.5 випадок 1: `TLS alert, certificate expired (557)`, `curl: (60) SSL certificate problem: certificate has expired`; випадок 2: `subjectAltName does not match wrong.host.badssl.com`, `SSL: no alternative certificate subject name matches target host name...`; випадок 3: `TLS alert, unknown CA (560)`, `curl: (60) SSL certificate problem: self-signed certificate` | Тут ухвалюється саме рішення «довіряти або не довіряти» конкретному сертифікату (ім'я, строк дії, видавець). Завдання A.5 показує, що відмова на цьому кроці обриває з'єднання ще до появи будь-якого прикладного вмісту. |
| 5 | Встановлення й завершення транспортного з'єднання | A.1/A.2/A.4/A.5 (усі): `Trying <IP>:443...` / `:80...`, `Connected to <host> (<IP>) port ... (#0)`, `Connection #0 to host ... left intact`, `Closing connection 0`; A.2: `Immediate connect fail for 2600:1f13:...: Network is unreachable` | Рядки стосуються самого факту з'єднання (або невдалої спроби) між конкретною IP-адресою та портом. |
| 6 | Визначення адреси сервера за іменем | A.3: `;; QUESTION SECTION: rfc-editor.org. IN A`, `;; ANSWER SECTION: rfc-editor.org. 145 IN A 104.18.21.81 / 104.18.20.81`, `;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)`, зміна TTL зі 145 на 300 між двома запитами | Це не сам запит до сайту, а просто попередній пошук його IP-адреси через DNS, щоб curl взагалі знав, куди підключатися. |

*Групи впорядковано від найближчої до користувача (№ 1) до найближчої до апаратного забезпечення.*

**Рядки, які не вдалося віднести до жодної групи:**

| Рядок виводу | Причина утруднення |
|---|---|
| `* CAfile: /etc/ssl/certs/ca-certificates.crt` / `* CApath: /etc/ssl/certs` | Це локальна конфігурація самого curl (де на диску шукати довірені сертифікати), а не повідомлення, яким обмінюються клієнт і сервер. |
| `* old SSL session ID is stale, removing` | Стосується внутрішнього кешу TLS-сесій на стороні клієнта. |
| `* Copying HTTP/2 data in stream buffer to connection buffer after upgrade: len=0` | Опис внутрішньої роботи буфера curl, а не крок протоколу взаємодії з сервером. |

---

## Контрольні питання

**1. Скільки рядків діагностичного виводу передує отриманню даних сторінки (завдання A.1)?**

> 46 рядків, які починаються з *. Те що позначено > це то що пішло в мережу, а < що прийшло.

**2. Які рядки наявні у виводі A.1 і відсутні у виводі A.2? Чим це зумовлено?**

> У A.1 є "* ALPN, offering h2, * ALPN, offering http/1.1, * ALPN, server accepted to use h2", а у А.2 немає, бо А.1 це HTTPS, а A.2 HTTP. Тобто ці рядки позначають ALPN, що є розширенням TLS-рукостискання, якого у A.2 немає. Також в A.1 вказується шлях до сертифікатів "* CAfile: /etc/ssl/certs/ca-certificates.crt, * CApath: /etc/ssl/certs". Якщо TLS відсутній, як у А.2, то і сертифікати не потрібні. TLS-рукостискання "Client hello (1), Server hello (2), Encrypted Extensions (8), Certificate (11), CERT verify (15), Finished (20), Change cipher spec (1)" це процедура встановлення шифрованого каналу, а у A.2 порт 80 без шифрування. Підсумки TLS "* SSL connection using TLSv1.3 / TLS_AES_256_GCM_SHA384", дані сертифіката сервера "* Server certificate:, subject:, start date:, expire date:, subjectAltName:, issuer:, SSL certificate verify ok." та сесійні квитки TLS "* TLSv1.3 (IN), TLS handshake, Newsession Ticket (4):, * old SSL session ID is stale, removing" відстуні з тих самих причин. У A.1 використовується порт 443 (HTTPS), а у A.2 80(HTTP).

**3. Звідки у виводі з'явилося значення `443`, якщо його не було вказано в адресі?**

> Бо йшло посилання на HTTPS (https://rfc-editor.org), який стоїть на порту 443. Якщо було б HTTP(http://rfc-editor.org), то був б порт 80.

**4. Як змінилося значення TTL між двома запитами (A.3)? Що означає це число?**

> TTL позначає час у секундах, протягом якого DNS-сервер дозволяє кешувати відповідь та віддавати назад користувачу на його запит, перш ніж питати знову у сервера. У моєму випадку перше значення TTL було 145, а друге зросло та стало 300. Це трапилось тому що поки я чекала між запитами, старий запис у кеші встиг повністю "згоріти", тому другий запит отримав уже нову відповідь з сервера з оновленим TTL.

**5. Чим відрізняються між собою три причини помилок із завдання A.5? Сформулювати кожну однією фразою.**

| Випадок | Причина недовіри |
|---|---|
| `expired` | Сертифікат дійсний, але строк дії минув. |
| `wrong.host` | Сертифікат дійсний і не прострочений, але випущений на інше ім'я, яке не збігається з іменем хоста в адресі. |
| `self-signed` | Сертифікат дійсний і не прострочений, але підписаний не довіреним центром сертифікації та curl не може його перевірити йому відовим підписом CA. |

**6. Три рядки з власних виводів, про які не йшлося на лекції 1:**

| № | Рядок виводу | Джерело (номер завдання) |
|---|---|---|
| 1 | `* SSL connection using TLSv1.3 / TLS_AES_256_GCM_SHA384` | A.1 |
| 2 | `* TLSv1.3 (IN), TLS handshake, Newsession Ticket (4):` / `* old SSL session ID is stale, removing` | A.1 |
| 3 | `* Immediate connect fail for 2600:1f13:37c:1400:ba21:7165:5fc7:736e: Network is unreachable` | A.2 |

*Пояснення до цих рядків не потрібне.*

---не довіреним центром сертифікації,

## Висновки

*150–300 слів. Спиратися на власні спостереження, а не на матеріал лекції.*

> Дізналася, що ALPN це розширення для протоколу TLS. У A.1 і A.4 (https://) curl спочатку пропонує дві версії HTTP (`* ALPN, offering h2`), а вже після рукостискання сервер вибирає одну (`* ALPN, server accepted to use h2`) самостійно, тобто curl виступає з пропозицією, а сервер вже обирає. У A.2 (http://neverssl.com) такого рядка взагалі немає, бо там немає TLS. Виявила, що curl може сам обирати порти такі як, наприклад, `:443` і `:80` залежно від того, https чи http в адресі та користувачу не потрібно це вказувати вручну. У A.5 я побачила, що "не довіряти сертифікату" може означати три різні речі: сертифікат прострочений, виданий на інше ім'я або взагалі не підписаний довіреним центром. Я ніколи до цього не привертала увагу як само підписан сертифікат та ким. Якщо він self-signed, це повинно понизити довіру до такого домену. Раніше я використовувала команду curl лише для того щоб перевірити, що домен взагалі живий. Ця практична розширила використання цієї команди вже для повноцінної діагностики сторінки та перевірки шифрування та сертифікатів.

**D.1. Що виявилося неочевидним або несподіваним**

*Назвати конкретно, з посиланням на рядок виводу.*

> Рядок `* ALPN, server accepted to use h2` з A.1/A.4 показав, що версію HTTP обирає сервер, а не клієнт, хоча здається, що curl усе вирішує сам.

**D.2. Чому саме така кількість груп у частині B**

*На якій підставі ухвалено рішення. Що змусило б його змінити.*

> Я обрала 6 груп, бо саме стільки окремих дій знайшла у своїх виводах: відповідь, версія HTTP, TLS-рукостискання, перевірка сертифіката, TCP-з'єднання, DNS. Якби не три різні помилки в A.5, я б об'єднала перевірку сертифіката з рукостисканням в одну групу.

**D.3. Питання, яке залишилося без відповіді**

> Не зрозуміла, чому в A.1 рукостискання підписане як TLSv1.3, а частина службових рядків навколо нього як TLSv1.2.

---

## Використання штучного інтелекту

*Розділ обов'язковий. Заповнюється незалежно від того, чи використовувався ШІ. Детальні вимоги — у документі «Політика використання технологій штучного інтелекту».*

**Факт використання:** використано

**Установлений рівень для цієї роботи:** Р2 — ШІ для підготовки

**Фактичний рівень використання:** Р___

### Використані системи

| Система | Версія або модель | Період використання |
|---|---|---|
| | | |

### Промпти

*Наводити дослівно, у тому вигляді, у якому запит було надано системі. Переказ не приймається.*

| № | Розділ роботи | Текст промпта |
|---|---|---|
| 1 | Збір експериментальних даних | Що таке ALPN і яку версію HTTP він використовує? |
| 2 | | |
| 3 | | |

### Дії з отриманим результатом

| № промпта | Що перевірено | Що змінено | Що відхилено і чому |
|---|---|---|---|
| 1 | Звірила пояснення ALPN і вибору версії HTTP із власними рядками з A.1, A.2, A.4 | | |
| 2 | | | |
| 3 | | | |

### Підтвердження

Підтверджую, що всі наведені в цьому звіті виводи команд отримано мною особисто внаслідок фактичного виконання відповідних дій, а відомості цього розділу є повними та достовірними.

> Виводи `curl`, `dig` та інші артефакти не можуть бути згенеровані. Це стосується будь-якого рівня використання ШІ.

---

## Примітки виконавця

*(необов'язковий розділ: що не спрацювало, які команди довелося змінити, які виникли труднощі)*

> 

# ZAP Scanning Report


## Summary of Alerts

| Risk Level | Number of Alerts |
| --- | --- |
| High | 0 |
| Medium | 5 |
| Low | 4 |
| Informational | 0 |




## Alerts

| Name | Risk Level | Number of Instances |
| --- | --- | --- |
| Absence of Anti-CSRF Tokens | Medium | 2 |
| Anti-CSRF Tokens Check | Medium | 2 |
| Content Security Policy (CSP) Header Not Set | Medium | 11 |
| HTTP Only Site | Medium | 1 |
| Missing Anti-clickjacking Header | Medium | 4 |
| Application Error Disclosure | Low | 1 |
| Information Disclosure - Debug Error Messages | Low | 1 |
| Server Leaks Version Information via "Server" HTTP Response Header Field | Low | 11 |
| X-Content-Type-Options Header Missing | Low | 4 |




## Alert Detail



### [ Absence of Anti-CSRF Tokens ](https://www.zaproxy.org/docs/alerts/10202/)



##### Medium (Low)

### Description

No Anti-CSRF tokens were found in a HTML submission form.
A cross-site request forgery is an attack that involves forcing a victim to send an HTTP request to a target destination without their knowledge or intent in order to perform an action as the victim. The underlying cause is application functionality using predictable URL/form actions in a repeatable way. The nature of the attack is that CSRF exploits the trust that a web site has for a user. By contrast, cross-site scripting (XSS) exploits the trust that a user has for a web site. Like XSS, CSRF attacks are not necessarily cross-site, but they can be. Cross-site request forgery is also known as CSRF, XSRF, one-click attack, session riding, confused deputy, and sea surf.

CSRF attacks are effective in a number of situations, including:
    * The victim has an active session on the target site.
    * The victim is authenticated via HTTP auth on the target site.
    * The victim is on the same local network as the target site.

CSRF has primarily been used to perform an action against a target site using the victim's privileges, but recent techniques have been discovered to disclose information by gaining access to the response. The risk of information disclosure is dramatically increased when the target site is vulnerable to XSS, because XSS can be used as a platform for CSRF, allowing the attack to operate within the bounds of the same-origin policy.

* URL: http://localhost:5050/xxe
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: `<form action = "/xxe_uploader" method = "POST" enctype = "multipart/form-data">`
* URL: http://localhost:5050/yaml
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: `<form action = "/yaml_hammer" method = "POST" enctype = "multipart/form-data">`

Instances: 2

### Solution

Phase: Architecture and Design
Use a vetted library or framework that does not allow this weakness to occur or provides constructs that make this weakness easier to avoid.
For example, use anti-CSRF packages such as the OWASP CSRFGuard.

Phase: Implementation
Ensure that your application is free of cross-site scripting issues, because most CSRF defenses can be bypassed using attacker-controlled script.

Phase: Architecture and Design
Generate a unique nonce for each form, place the nonce into the form, and verify the nonce upon receipt of the form. Be sure that the nonce is not predictable (CWE-330).
Note that this can be bypassed using XSS.

Identify especially dangerous operations. When the user performs a dangerous operation, send a separate confirmation request to ensure that the user intended to perform that operation.
Note that this can be bypassed using XSS.

Use the ESAPI Session Management control.
This control includes a component for CSRF.

Do not use the GET method for any request that triggers a state change.

Phase: Implementation
Check the HTTP Referer header to see if the request originated from an expected page. This could break legitimate functionality, because users or proxies may have disabled sending the Referer for privacy reasons.

### Reference


* [ http://projects.webappsec.org/Cross-Site-Request-Forgery ](http://projects.webappsec.org/Cross-Site-Request-Forgery)
* [ http://cwe.mitre.org/data/definitions/352.html ](http://cwe.mitre.org/data/definitions/352.html)


#### CWE Id: [ 352 ](https://cwe.mitre.org/data/definitions/352.html)


#### WASC Id: 9

#### Source ID: 3

### [ Anti-CSRF Tokens Check ](https://www.zaproxy.org/docs/alerts/20012/)



##### Medium (Medium)

### Description

A cross-site request forgery is an attack that involves forcing a victim to send an HTTP request to a target destination without their knowledge or intent in order to perform an action as the victim. The underlying cause is application functionality using predictable URL/form actions in a repeatable way. The nature of the attack is that CSRF exploits the trust that a web site has for a user. By contrast, cross-site scripting (XSS) exploits the trust that a user has for a web site. Like XSS, CSRF attacks are not necessarily cross-site, but they can be. Cross-site request forgery is also known as CSRF, XSRF, one-click attack, session riding, confused deputy, and sea surf.

CSRF attacks are effective in a number of situations, including:
    * The victim has an active session on the target site.
    * The victim is authenticated via HTTP auth on the target site.
    * The victim is on the same local network as the target site.

CSRF has primarily been used to perform an action against a target site using the victim's privileges, but recent techniques have been discovered to disclose information by gaining access to the response. The risk of information disclosure is dramatically increased when the target site is vulnerable to XSS, because XSS can be used as a platform for CSRF, allowing the attack to operate within the bounds of the same-origin policy.

* URL: http://localhost:5050/xxe
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: `<form action = "/xxe_uploader" method = "POST" enctype = "multipart/form-data">`
* URL: http://localhost:5050/yaml
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: `<form action = "/yaml_hammer" method = "POST" enctype = "multipart/form-data">`

Instances: 2

### Solution

Phase: Architecture and Design
Use a vetted library or framework that does not allow this weakness to occur or provides constructs that make this weakness easier to avoid.
For example, use anti-CSRF packages such as the OWASP CSRFGuard.

Phase: Implementation
Ensure that your application is free of cross-site scripting issues, because most CSRF defenses can be bypassed using attacker-controlled script.

Phase: Architecture and Design
Generate a unique nonce for each form, place the nonce into the form, and verify the nonce upon receipt of the form. Be sure that the nonce is not predictable (CWE-330).
Note that this can be bypassed using XSS.

Identify especially dangerous operations. When the user performs a dangerous operation, send a separate confirmation request to ensure that the user intended to perform that operation.
Note that this can be bypassed using XSS.

Use the ESAPI Session Management control.
This control includes a component for CSRF.

Do not use the GET method for any request that triggers a state change.

Phase: Implementation
Check the HTTP Referer header to see if the request originated from an expected page. This could break legitimate functionality, because users or proxies may have disabled sending the Referer for privacy reasons.

### Reference


* [ http://projects.webappsec.org/Cross-Site-Request-Forgery ](http://projects.webappsec.org/Cross-Site-Request-Forgery)
* [ http://cwe.mitre.org/data/definitions/352.html ](http://cwe.mitre.org/data/definitions/352.html)


#### CWE Id: [ 352 ](https://cwe.mitre.org/data/definitions/352.html)


#### WASC Id: 9

#### Source ID: 1

### [ Content Security Policy (CSP) Header Not Set ](https://www.zaproxy.org/docs/alerts/10038/)



##### Medium (High)

### Description

Content Security Policy (CSP) is an added layer of security that helps to detect and mitigate certain types of attacks, including Cross Site Scripting (XSS) and data injection attacks. These attacks are used for everything from data theft to site defacement or distribution of malware. CSP provides a set of standard HTTP headers that allow website owners to declare approved sources of content that browsers should be allowed to load on that page — covered types are JavaScript, CSS, HTML frames, fonts, images and embeddable objects such as Java applets, ActiveX, audio and video files.

* URL: http://localhost:5050
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: ``
* URL: http://localhost:5050/
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: ``
* URL: http://localhost:5050/fetch/customer
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: ``
* URL: http://localhost:5050/login
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: ``
* URL: http://localhost:5050/register/customer
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: ``
* URL: http://localhost:5050/register/user
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: ``
* URL: http://localhost:5050/robots.txt
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: ``
* URL: http://localhost:5050/search
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: ``
* URL: http://localhost:5050/sitemap.xml
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: ``
* URL: http://localhost:5050/xxe_uploader
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: ``
* URL: http://localhost:5050/yaml_hammer
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: ``

Instances: 11

### Solution

Ensure that your web server, application server, load balancer, etc. is configured to set the Content-Security-Policy header, to achieve optimal browser support: "Content-Security-Policy" for Chrome 25+, Firefox 23+ and Safari 7+, "X-Content-Security-Policy" for Firefox 4.0+ and Internet Explorer 10+, and "X-WebKit-CSP" for Chrome 14+ and Safari 6+.

### Reference


* [ https://developer.mozilla.org/en-US/docs/Web/Security/CSP/Introducing_Content_Security_Policy ](https://developer.mozilla.org/en-US/docs/Web/Security/CSP/Introducing_Content_Security_Policy)
* [ https://cheatsheetseries.owasp.org/cheatsheets/Content_Security_Policy_Cheat_Sheet.html ](https://cheatsheetseries.owasp.org/cheatsheets/Content_Security_Policy_Cheat_Sheet.html)
* [ http://www.w3.org/TR/CSP/ ](http://www.w3.org/TR/CSP/)
* [ http://w3c.github.io/webappsec/specs/content-security-policy/csp-specification.dev.html ](http://w3c.github.io/webappsec/specs/content-security-policy/csp-specification.dev.html)
* [ http://www.html5rocks.com/en/tutorials/security/content-security-policy/ ](http://www.html5rocks.com/en/tutorials/security/content-security-policy/)
* [ http://caniuse.com/#feat=contentsecuritypolicy ](http://caniuse.com/#feat=contentsecuritypolicy)
* [ http://content-security-policy.com/ ](http://content-security-policy.com/)


#### CWE Id: [ 693 ](https://cwe.mitre.org/data/definitions/693.html)


#### WASC Id: 15

#### Source ID: 3

### [ HTTP Only Site ](https://www.zaproxy.org/docs/alerts/10106/)



##### Medium (Medium)

### Description

The site is only served under HTTP and not HTTPS.

* URL: http://localhost:5050/xxe_uploader
  * Method: `POST`
  * Parameter: ``
  * Attack: ``
  * Evidence: ``

Instances: 1

### Solution

Configure your web or application server to use SSL (https).

### Reference


* [ https://cheatsheetseries.owasp.org/cheatsheets/Transport_Layer_Protection_Cheat_Sheet.html ](https://cheatsheetseries.owasp.org/cheatsheets/Transport_Layer_Protection_Cheat_Sheet.html)
* [ https://letsencrypt.org/ ](https://letsencrypt.org/)


#### CWE Id: [ 311 ](https://cwe.mitre.org/data/definitions/311.html)


#### WASC Id: 4

#### Source ID: 1

### [ Missing Anti-clickjacking Header ](https://www.zaproxy.org/docs/alerts/10020/)



##### Medium (Medium)

### Description

The response does not include either Content-Security-Policy with 'frame-ancestors' directive or X-Frame-Options to protect against 'ClickJacking' attacks.

* URL: http://localhost:5050
  * Method: `GET`
  * Parameter: `X-Frame-Options`
  * Attack: ``
  * Evidence: ``
* URL: http://localhost:5050/
  * Method: `GET`
  * Parameter: `X-Frame-Options`
  * Attack: ``
  * Evidence: ``
* URL: http://localhost:5050/xxe
  * Method: `GET`
  * Parameter: `X-Frame-Options`
  * Attack: ``
  * Evidence: ``
* URL: http://localhost:5050/yaml
  * Method: `GET`
  * Parameter: `X-Frame-Options`
  * Attack: ``
  * Evidence: ``

Instances: 4

### Solution

Modern Web browsers support the Content-Security-Policy and X-Frame-Options HTTP headers. Ensure one of them is set on all web pages returned by your site/app.
If you expect the page to be framed only by pages on your server (e.g. it's part of a FRAMESET) then you'll want to use SAMEORIGIN, otherwise if you never expect the page to be framed, you should use DENY. Alternatively consider implementing Content Security Policy's "frame-ancestors" directive.

### Reference


* [ https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options ](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options)


#### CWE Id: [ 1021 ](https://cwe.mitre.org/data/definitions/1021.html)


#### WASC Id: 15

#### Source ID: 3

### [ Application Error Disclosure ](https://www.zaproxy.org/docs/alerts/90022/)



##### Low (Medium)

### Description

This page contains an error/warning message that may disclose sensitive information like the location of the file that produced the unhandled exception. This information can be used to launch further attacks against the web application. The alert could be a false positive if the error message is found inside a documentation page.

* URL: http://localhost:5050/xxe_uploader
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: `HTTP/1.1 500 INTERNAL SERVER ERROR`

Instances: 1

### Solution

Review the source code of this page. Implement custom error pages. Consider implementing a mechanism to provide a unique error reference/identifier to the client (browser) while logging the details on the server side and not exposing them to the user.

### Reference



#### CWE Id: [ 200 ](https://cwe.mitre.org/data/definitions/200.html)


#### WASC Id: 13

#### Source ID: 3

### [ Information Disclosure - Debug Error Messages ](https://www.zaproxy.org/docs/alerts/10023/)



##### Low (Medium)

### Description

The response appeared to contain common error messages returned by platforms such as ASP.NET, and Web-servers such as IIS and Apache. You can configure the list of common debug messages.

* URL: http://localhost:5050/xxe_uploader
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: `Internal Server Error`

Instances: 1

### Solution

Disable debugging messages before pushing to production.

### Reference



#### CWE Id: [ 200 ](https://cwe.mitre.org/data/definitions/200.html)


#### WASC Id: 13

#### Source ID: 3

### [ Server Leaks Version Information via "Server" HTTP Response Header Field ](https://www.zaproxy.org/docs/alerts/10036/)



##### Low (High)

### Description

The web/application server is leaking version information via the "Server" HTTP response header. Access to such information may facilitate attackers identifying other vulnerabilities your web/application server is subject to.

* URL: http://localhost:5050
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: `TornadoServer/4.5.1`
* URL: http://localhost:5050/
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: `TornadoServer/4.5.1`
* URL: http://localhost:5050/fetch/customer
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: `TornadoServer/4.5.1`
* URL: http://localhost:5050/login
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: `TornadoServer/4.5.1`
* URL: http://localhost:5050/register/customer
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: `TornadoServer/4.5.1`
* URL: http://localhost:5050/register/user
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: `TornadoServer/4.5.1`
* URL: http://localhost:5050/robots.txt
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: `TornadoServer/4.5.1`
* URL: http://localhost:5050/search
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: `TornadoServer/4.5.1`
* URL: http://localhost:5050/sitemap.xml
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: `TornadoServer/4.5.1`
* URL: http://localhost:5050/xxe_uploader
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: `TornadoServer/4.5.1`
* URL: http://localhost:5050/yaml_hammer
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: `TornadoServer/4.5.1`

Instances: 11

### Solution

Ensure that your web server, application server, load balancer, etc. is configured to suppress the "Server" header or provide generic details.

### Reference


* [ http://httpd.apache.org/docs/current/mod/core.html#servertokens ](http://httpd.apache.org/docs/current/mod/core.html#servertokens)
* [ http://msdn.microsoft.com/en-us/library/ff648552.aspx#ht_urlscan_007 ](http://msdn.microsoft.com/en-us/library/ff648552.aspx#ht_urlscan_007)
* [ http://blogs.msdn.com/b/varunm/archive/2013/04/23/remove-unwanted-http-response-headers.aspx ](http://blogs.msdn.com/b/varunm/archive/2013/04/23/remove-unwanted-http-response-headers.aspx)
* [ http://www.troyhunt.com/2012/02/shhh-dont-let-your-response-headers.html ](http://www.troyhunt.com/2012/02/shhh-dont-let-your-response-headers.html)


#### CWE Id: [ 200 ](https://cwe.mitre.org/data/definitions/200.html)


#### WASC Id: 13

#### Source ID: 3

### [ X-Content-Type-Options Header Missing ](https://www.zaproxy.org/docs/alerts/10021/)



##### Low (Medium)

### Description

The Anti-MIME-Sniffing header X-Content-Type-Options was not set to 'nosniff'. This allows older versions of Internet Explorer and Chrome to perform MIME-sniffing on the response body, potentially causing the response body to be interpreted and displayed as a content type other than the declared content type. Current (early 2014) and legacy versions of Firefox will use the declared content type (if one is set), rather than performing MIME-sniffing.

* URL: http://localhost:5050
  * Method: `GET`
  * Parameter: `X-Content-Type-Options`
  * Attack: ``
  * Evidence: ``
* URL: http://localhost:5050/
  * Method: `GET`
  * Parameter: `X-Content-Type-Options`
  * Attack: ``
  * Evidence: ``
* URL: http://localhost:5050/xxe
  * Method: `GET`
  * Parameter: `X-Content-Type-Options`
  * Attack: ``
  * Evidence: ``
* URL: http://localhost:5050/yaml
  * Method: `GET`
  * Parameter: `X-Content-Type-Options`
  * Attack: ``
  * Evidence: ``

Instances: 4

### Solution

Ensure that the application/web server sets the Content-Type header appropriately, and that it sets the X-Content-Type-Options header to 'nosniff' for all web pages.
If possible, ensure that the end user uses a standards-compliant and modern web browser that does not perform MIME-sniffing at all, or that can be directed by the web application/web server to not perform MIME-sniffing.

### Reference


* [ http://msdn.microsoft.com/en-us/library/ie/gg622941%28v=vs.85%29.aspx ](http://msdn.microsoft.com/en-us/library/ie/gg622941%28v=vs.85%29.aspx)
* [ https://owasp.org/www-community/Security_Headers ](https://owasp.org/www-community/Security_Headers)


#### CWE Id: [ 693 ](https://cwe.mitre.org/data/definitions/693.html)


#### WASC Id: 15

#### Source ID: 3



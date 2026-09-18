# SRI finding on bettdatllc.com — AdSense script

Aikido: Sub Resource Integrity Attribute Missing (score 15)

The only third-party script on the listed URLs is Google AdSense:

```html
<script async="" src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-2777341077040240" crossorigin="anonymous"></script>
```

## Why not add integrity=

Google rotates `adsbygoogle.js`. Official AdSense snippets have no SRI hash. Pinning one breaks ads on the next Google publish.

## Fix

Delete that `<script>` from every page. Patched HTML is in this conversation under `artifacts/bettdatllc-sri-fix/`.

Find:
```html
<script async="" src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-2777341077040240" crossorigin="anonymous"></script>
```

Replace with nothing.

Redeploy the full existing Netlify site (lustrous-liger-981971). Do not publish only this repo.

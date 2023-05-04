# No more shorts on youtube
YouTube shorts and all their derivatives (Reels, TikTok, ...) are shit and a cancer for our society. Their algorithms are designed to steal our time and destroy our brains and our concentration.

Here is a script to never be locked in the shorts loop again. It redirects the shorts on the canonical "watch?v=" url.

## Installation 
- Install [Tampermonkey browser extension](https://www.tampermonkey.net/) (if you don't have it already)
- Click on "Create a new script..." and copy paste :
```js
// ==UserScript==
// @name         NoMoreShorts
// @version      0.1
// @description  Redirects "shorts" to the canonical "watch?v=" url.
// @match        https://youtube.com/*
// @run-at       document-start
// @include      *youtube.com*
// ==/UserScript==

(function() {
    'use strict';
    function checkShorts() {
        if (window.location.pathname.startsWith("/shorts/")) {
            window.location.href = 'https://www.youtube.com/watch?v=' + window.location.pathname.split('/')[2];
        }
    }
    document.addEventListener('yt-navigate-start', checkShorts);

    if (document.body) checkShorts();
    else document.addEventListener('DOMContentLoaded', checkShorts);
})();
```

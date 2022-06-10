<div id="top"></div>
<br />
<div align="center">
  <a href="https://betastar.org">
    <img src="https://betastargame.github.io/images/logo.png" alt="Logo" width="300" height="300">
  </a>
  <h1 align="center">Betastar Scripts</h1>

  <p align="center">
    <b>Almost all of these are compatible with Tampermonkey!</b><br>
    <br>
    <a href="https://github.com/BetastarGame/BetastarGame.github.io/issues">Report an Issue</a>
  </p>
</div>
<div id="top"></div>
<br />
<div align="center">
  <h3 align="center">Using a Script</h3>

  <p align="center">
    1. Find the script you want below.<br>
    2. Copy the script to your clipboard.<br>
    3. Open <a href="https://betastar.org">Betastar</a>.<br>
    4. Use Control/Command + Shift + J.<br>
    5. A window should pop up. Paste the script in where it has a <b>></b> symbol.<br>
    6. Follow any instructions (in popups) on the Betastar page.
  </p>
</div>
<br>
<br>
<br>
<br>
<div id="top"></div>
<br />
<div align="center">
  <img src="https://betastargame.github.io/images/spaceTerminal.png" alt="Logo" width="200" height="200">
  <h3 align="center">Appear Offline</h3>

  <p align="center">
    Appear Offline at any time.<br>
    WARNING: This disables trading.<br>
    <br>
    <b>Incompatible with Tampermonkey</b>
  </p>
</div>

```js
alert('Script coded by Zastix, Betastar tester\nFor more scripts, visit\nhttps://betastargame.github.io/')
alert('WARNING: you will not be able to trade with this script enabled')
socket.disconnect()
if (location.pathname === '/stats/' || location.pathname === '/stats') {
  document.getElementById('#userElement').style.filter = 'drop-shadow(0px 0px 100px red)'
}
```
<br>
<div id="top"></div>
<br />
<div align="center">
  <h3 align="center">Chat Downloader</h3>

  <p align="center">
    Adds a handy button that downloads the chat upon click...
  </p>
</div>

```js
// ==UserScript==
// @name         Betastar Chat Downloader
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  Adds a handy button that downloads the chat upon click...MORE SCRIPTS --> https://betastargame.github.io/scripts
// @author       l2vy7/acai
// @match        https://betastar.org/chat/
// @icon         https://www.google.com/s2/favicons?sz=64&domain=betastar.org
// @grant        none
// ==/UserScript==

(function() {
    'use strict';

    var style = document.createElement('style');
    style.textContent = `

    .chatExport {
        font-family: jua;
        color: white;
        border-radius: 0.25rem;
        position: absolute;
        bottom: 0;
        right: 0;
        background-color: black;
        box-shadow: 0px 10px 25px 15px rgba(100,100,100,0.2);
        padding: 5px 10px;
    }

    `;
    document.body.appendChild(style);

    var bruh = document.createElement('h3');
    bruh.textContent = 'Download Chat Logs';
    bruh.classList.add('chatExport');
    document.body.appendChild(bruh);

    bruh.addEventListener('click', function (e) {
        var text = ``;
        for (var elem of document.getElementsByClassName('chatBox')[0].children) {
            var profile = elem.children[0].src.endsWith('gif') ? 'Owner' : capitalizeFirstLetter(elem.children[0].src.replace('https://betastar.org', '').replace('/image/elements/', '').replace('.png', ''));
            text += `${profile} - ${elem.children[1].textContent.replace(' > ', '')}: ${elem.children[2].textContent}\n`.replace('Https://betastar.org', '');
        }
        downloadFile(`data:application/txt,${encodeURIComponent(text)}`);
    });

    function capitalizeFirstLetter(string) {
        return string.charAt(0).toUpperCase() + string.slice(1);
    }

    function downloadFile(url) {
        const a = document.createElement('a');

        a.style.display = 'none';
        a.href = url;

        var today = new Date();
        var dd = String(today.getDate()).padStart(2, '0');
        var mm = String(today.getMonth() + 1).padStart(2, '0');
        var yyyy = today.getFullYear();

        a.download = `logs-${mm}-${dd}-${yyyy}-${today.getSeconds()}.txt`;

        document.body.appendChild(a);

        a.click();

        window.URL.revokeObjectURL(url);
    }
})();
```
<br>
<div id="top"></div>
<br />
<div align="center">
  <h3 align="center">Chat Spammer</h3>

  <p align="center">
    Spams the chat with "free atoms", then a decimal.<br>
    You may be muted or banned, I wouldn't try it.
  </p>
</div>

```js
// ==UserScript==
// @name         Betastar Chat Spammer
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  Spams the chat with "free atoms", then a decimal. You may be muted or banned, I wouldn't try it. MORE SCRIPTS --> https://betastargame.github.io/scripts
// @author       zastix
// @match        https://betastar.org/chat/
// @icon         https://www.google.com/s2/favicons?sz=64&domain=betastar.org
// @grant        none
// ==/UserScript==

alert('Script coded by Zastix, Betastar tester\nFor more scripts, visit\nhttps://betastargame.github.io/')
alert('WARNING: this will cause SO MUCH LAG, some devices cannot handle it.\nDO NOT USE THIS on Chromebooks, Phones, iPads, or odl devices. It might break them.')
setInterval(()=>{ socket.emit('smes', `free atoms | ${Math.random()}`) })
```
<br>
<div id="top"></div>
<br />
<div align="center">
  <img src="https://betastargame.github.io/images/sellElement.png" alt="Logo" width="200" height="90">
  <h3 align="center">Sell Duplicate Elements</h3>

  <p align="center">
    Sell all your duplicate Elements, automatically.
  </p>
</div>

```js
// ==UserScript==
// @name         Betastar Duplicate Element Seller
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  Sell all your duplicate Elements, automatically. MORE SCRIPTS --> https://betastargame.github.io/scripts
// @author       zastix
// @match        https://betastar.org/elements/
// @icon         https://www.google.com/s2/favicons?sz=64&domain=betastar.org
// @grant        none
// ==/UserScript==

alert('Script coded by Zastix, Betastar tester\nFor more scripts, visit\nhttps://betastargame.github.io/')
alert('Are you sure? There is no way to exempt elements in ANY WAY.')

$.get('/api/user/elements', function(data) {
    userElements = JSON.parse(data)
    Object.keys(elementList).forEach(element => sell(element))
})
async function sell(element) {
    var amt = userElements[element] - 1
    if (0 >= amt) return;
    var postData = `element=${element}&quantity=${amt}`;
    $.post(`/api/sell/`, postData, function() {
        if (isNaN(amt)) return;
        else console.log(`Sold ${amt} ${element}(s)`);
    })
}
```
<br>
<div id="top"></div>
<br />
<div align="center">
  <img src="https://betastargame.github.io/images/spamCrates.png" alt="Logo" width="110" height="300">
  <h3 align="center">Spam Open Crates</h3>

  <p align="center">
    Quickly get the elements from any crate. Works QUITE quickly.
  </p>
</div>

```js
// ==UserScript==
// @name         Betastar Crate Spammer
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  Quickly get the elements from any crate. Works QUITE quickly. MORE SCRIPTS --> https://betastargame.github.io/scripts
// @author       zastix
// @match        https://betastar.org/crates/
// @icon         https://www.google.com/s2/favicons?sz=64&domain=betastar.org
// @grant        none
// ==/UserScript==

alert('Script coded by Zastix, Betastar tester\nFor more scripts, visit\nhttps://betastargame.github.io/')

var i = 0;
var boxes = []
colors = {
    divine: '#ee82ee',
    mythical: '#a335ee',
    perfect: '#fffacd',
    fabled: '#0c7500',
    legendary: '#ff910f',
    epic: '#be0000',
    rare: '#0a14fa',
    uncommon: '#4bc22e',
    common: '#ffffff'
}
Object.keys(cratesList).forEach(e => {
    boxes.push(e)
})
var name = prompt("Which crate would you like to open?\n\nOptions:\n" + boxes.join('\n'));
if (!boxes.includes(name)) {
    alert('That crate doesn\'t exist...')
    name = prompt("Which crate would you like to open?\n\nOptions:\n" + boxes.join('\n'));
}
var amt = Number(prompt("How many crates would you like to open?\ntype \"*\" to unlock all you can with your current atoms."));
if (isNaN(amt)) amt = 99999999999999
function buyBox() {
    $.post('/api/open/', `crate=${name}`, function(data) {
        try {
            if (data === "You're being rate limited.") i--
            else {
                rarity = elementList[data]['rarity'].toLowerCase()
                console.log('%c%s', `color: ${colors[rarity]}; font-size: 25px; text-shadow: 0px 0px 15px ${colors[rarity]};`, `${data}`);
            }
        } catch (e) {
            i = amt
        }
    });
}
var check = setInterval(() => {
    if (i < amt) {
        buyBox();
        i++;
    } else {
        clearInterval(check);
        alert("Done buying boxes! Check the console or the Elements page.");
    }
}, 751);
```
<br>
<div id="top"></div>
<br />
<div align="center">
  <img src="https://betastargame.github.io/images/allElements.png" alt="Logo" width="500" height="250">
  <h3 align="center">Spoof Elements</h3>

  <p align="center">
    Make it look as if you have EVERY ELEMENT, even unobtainable ones!
  </p>
</div>

```js
// ==UserScript==
// @name         Betastar Element Spoofer
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  Make it look as if you have EVERY ELEMENT, even unobtainable ones! MORE SCRIPTS --> https://betastargame.github.io/scripts
// @author       zastix
// @match        https://betastar.org/elements/
// @icon         https://www.google.com/s2/favicons?sz=64&domain=betastar.org
// @grant        none
// ==/UserScript==

alert('Script coded by Zastix, Betastar tester\nFor more scripts, visit\nhttps://betastargame.github.io/')

Array.from(document.getElementById('#elementList').children).forEach(a => a.remove())
Object.entries(elementList).forEach((entry) => {
	const [key, value] = entry;
	$(`<img id="${key}" src="${elementList[key].imageURL}" onclick="viewElement('${key}')" class="bottomElement">`).appendTo(".elementList");
})
for (i=0;i<Object.keys(elementList).length;i++) {
    elemes = Object.keys(elementList)
    if (elemes[i] === 'nigger') userElements[elemes[i]] = Math.floor(Math.random() * 4);
    else userElements[elemes[i]] = Math.floor(elementList[elemes[i]]['chance'] / 2 + Math.round(Math.random() * 20));
}
```
<br>
<br>
<br>
<br>
<div id="top"></div>
<br />
<div align="center">
  <a href="https://github.com/notzastix/blacket-hacks">
    <img src="https://betastargame.github.io/images/diamondGift.png" alt="Logo" width="190" height="200">
  </a>
  <h3 align="center">Script Credits</h3>

  <p align="center">
    Credit to <b>@notzastix</b>.
  </p>
</div>
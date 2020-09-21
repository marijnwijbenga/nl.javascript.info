# Een introductie tot JavaScript.

Laten we eens zien wat er bijzonder is aan JavaScript, wat we ermee kunnen bereiken en met welke andere technologieën het goed samenwerkt. 

## Wat is JavaScript?

*JavaScript* is oorspronkelijk gemaakt om webpagina's "tot leven te laten komen".

De programmatjes's in deze taal noemen we *scripts*. Die kan je rechtstreeks in de HTML van een webpagina plaatsen, en starten vanzelf wanneer de pagina laadt.

Scripts worden aangeleverd en uitgevoerd als gewone tekst. Ze hebben geen verdere behandeling nodig en behoeven niet gecompileerd te worden. In dit aspect is JavaScript heel anders dan een andere programmeertaal genaamd [Java](https://nl.wikipedia.org/wiki/Java_(programmeertaal)).

```smart header="Waarom heet het <u>Java</u>Script?"
Toen JavaScript gemaakt werd had het in eerste instantie een andere naam: "LiveScript". Echter was Java in die tijd erg populair geworden, dus besloot men dat de nieuwe taal positioneren als een "broertje" van Java, kon helpen bij de naamsbekendheid. 

Echter, JavaScript groeide uit tot een volwaardige en op zichzelf staande taal met zijn eigen specificatie genaamd [ECMAScript](https://nl.wikipedia.org/wiki/ECMAScript), en nu is er geen enkele relatie meer met Java.
```

Tegenwoordig werkt JavaScript niet alleen in de browser, maar ook op de server en op elk apparaat dat een speciaal programma genaamd [the JavaScript engine](https://en.wikipedia.org/wiki/JavaScript_engine) heeft.

De browser heeft een ingebedde engine die ook wel de "Javascript virtual machine" genoemd wordt.

Verschillende engines hebben verschillende "codenamen". Bijvoorbeeld:
- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- in Chrome and Opera.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- in Firefox.
- ...Er zijn andere codenamen zoals "Trident" en "Chakra" voor andere versies van IE, "ChakraCore" voor Microsoft Edge, "Nitro" en "SquirrelFish" voor Safari, etc.

De termen hierboven zijn goed om te onthouden omdat ze vaak worden gebruikt in artikelen over ontwikkelen op het internet. Wij zullen ze hier ook gebruiken, bijvoorbeeld: "Als feature x wordt ondersteund door V8, werkt het waarschijnlijk ook in Chrome en Opera."


```smart header="Hoe werken engines?"

Engines zijn ingewikkeld, maar de basis is het vrij simpel.

1. De engine (embedded in het geval van de browser) leest ("parsed") het script.
2. Dan converteert (compiled) het het script naar machine code.
3. En dan draait de machine code, vrij snel.

De engine past elke stap optimalisaties van het proces toe. Het kijkt zelfs naar het gecompilede script terwijl het loopt, analyseert de data die er doorheen loopt, en optimaliseert de machine code gebaseerd op de opgedane kennis.
```

## What can in-browser JavaScript do?

Modern JavaScript is a "safe" programming language. It does not provide low-level access to memory or CPU, because it was initially created for browsers which do not require it.

JavaScript's capabilities greatly depend on the environment it's running in. For instance, [Node.js](https://wikipedia.org/wiki/Node.js) supports functions that allow JavaScript to read/write arbitrary files, perform network requests, etc.

In-browser JavaScript can do everything related to webpage manipulation, interaction with the user, and the webserver.

For instance, in-browser JavaScript is able to:

- Add new HTML to the page, change the existing content, modify styles.
- React to user actions, run on mouse clicks, pointer movements, key presses.
- Send requests over the network to remote servers, download and upload files (so-called [AJAX](https://en.wikipedia.org/wiki/Ajax_(programming)) and [COMET](https://en.wikipedia.org/wiki/Comet_(programming)) technologies).
- Get and set cookies, ask questions to the visitor, show messages.
- Remember the data on the client-side ("local storage").

## What CAN'T in-browser JavaScript do?

JavaScript's abilities in the browser are limited for the sake of the user's safety. The aim is to prevent an evil webpage from accessing private information or harming the user's data.

Examples of such restrictions include:

- JavaScript on a webpage may not read/write arbitrary files on the hard disk, copy them or execute programs. It has no direct access to OS functions.

    Modern browsers allow it to work with files, but the access is limited and only provided if the user does certain actions, like "dropping" a file into a browser window or selecting it via an `<input>` tag.

    There are ways to interact with camera/microphone and other devices, but they require a user's explicit permission. So a JavaScript-enabled page may not sneakily enable a web-camera, observe the surroundings and send the information to the [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).
- Different tabs/windows generally do not know about each other. Sometimes they do, for example when one window uses JavaScript to open the other one. But even in this case, JavaScript from one page may not access the other if they come from different sites (from a different domain, protocol or port).

    This is called the "Same Origin Policy". To work around that, *both pages* must agree for data exchange and contain a special JavaScript code that handles it. We'll cover that in the tutorial.

    This limitation is, again, for the user's safety. A page from `http://anysite.com` which a user has opened must not be able to access another browser tab with the URL `http://gmail.com` and steal information from there.
- JavaScript can easily communicate over the net to the server where the current page came from. But its ability to receive data from other sites/domains is crippled. Though possible, it requires explicit agreement (expressed in HTTP headers) from the remote side. Once again, that's a safety limitation.

![](limitations.svg)

Such limits do not exist if JavaScript is used outside of the browser, for example on a server. Modern browsers also allow plugin/extensions which may ask for extended permissions.

## What makes JavaScript unique?

There are at least *three* great things about JavaScript:

```compare
+ Full integration with HTML/CSS.
+ Simple things are done simply.
+ Support by all major browsers and enabled by default.
```
JavaScript is the only browser technology that combines these three things.

That's what makes JavaScript unique. That's why it's the most widespread tool for creating browser interfaces.

That said, JavaScript also allows to create servers, mobile applications, etc.

## Languages "over" JavaScript

The syntax of JavaScript does not suit everyone's needs. Different people want different features.

That's to be expected, because projects and requirements are different for everyone.

So recently a plethora of new languages appeared, which are *transpiled* (converted) to JavaScript before they run in the browser.

Modern tools make the transpilation very fast and transparent, actually allowing developers to code in another language and auto-converting it "under the hood".

Examples of such languages:

- [CoffeeScript](http://coffeescript.org/) is a "syntactic sugar" for JavaScript. It introduces shorter syntax, allowing us to write clearer and more precise code. Usually, Ruby devs like it.
- [TypeScript](http://www.typescriptlang.org/) is concentrated on adding "strict data typing" to simplify the development and support of complex systems. It is developed by Microsoft.
- [Flow](http://flow.org/) also adds data typing, but in a different way. Developed by Facebook.
- [Dart](https://www.dartlang.org/) is a standalone language that has its own engine that runs in non-browser environments (like mobile apps), but also can be transpiled to JavaScript. Developed by Google.
- [Brython](https://brython.info/) is a Python transpiler to JavaScript that allow to write application in pure Python without JavaScript.

There are more. Of course, even if we use one of transpiled languages, we should also know JavaScript to really understand what we're doing.

## Summary

- JavaScript was initially created as a browser-only language, but is now used in many other environments as well.
- Today, JavaScript has a unique position as the most widely-adopted browser language with full integration with HTML/CSS.
- There are many languages that get "transpiled" to JavaScript and provide certain features. It is recommended to take a look at them, at least briefly, after mastering JavaScript.

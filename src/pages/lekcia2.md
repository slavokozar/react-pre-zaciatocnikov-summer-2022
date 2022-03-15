---
title: "Lekcia 2"
heading: "Lekcia 2 - React component"
layout: ../layouts/Lekcia.astro
---

## Vytvorenie React projektu

```shell
$npx create-react-app my-app
cd my-app
npm start
```

## Základá štruktúra projektu

```
├── public
│   ├── favicon.ico
│   ├── index.html
│   ├── logo512.png
│   ├── manifest.json
│   ├── robots.txt
│   ├── logo192.png
├── src
│   ├── reportWebVitals.js
│   ├── App.css
│   ├── index.js
│   ├── index.css
│   ├── App.test.js
│   ├── setupTests.js
│   ├── logo.svg
│   └── App.js
├── README.md
├── .gitignore
├── package-lock.json
└── package.json
```

### dôležité umiestnenia

**package.json**
- súbor definujúci závislosti projektu

**public**

- všetky zdroje určené pre zobrazenie v prehliadači - obrázky...

**public/index.html**

- HTML súbor otváraný prehliadačom​

**src/index.js**

- koreňový súbor celého projektu​

**src/App.js**

- hlavná komponenta projektu

---

## FAQ Aplikácia

<style>
    .faq-item {
        margin: 2rem 0;
    }
    .faq-item p {
        display: none;
    }
</style> 

<div class="faq-item">
<h5>Je akademie zdarma?</h5>
<p>Akademie je zdarma pro všechny členy klubu Silicon Hill s platním základním a síťovím členstvím.</p>
<button>Ukaž odpověď</button>
</div>

<div class="faq-item">
<h5>Co si vzít sebou?</h5>
<p>Vlastní notebook.</p>
<button>Ukaž odpověď</button>
</div>

<div class="faq-item">
<h5>Co musím mít nainstalováno v notebooku?</h5>
<p>Node.JS, Editor zdrojového kódu, např. Visual Studio Code.</p>
<button>Ukaž odpověď</button>
</div>

<div class="faq-item">
<h5>Musím umět programovat?</h5>
<p>Je dobré znát nějaké základní pojmy jako je if a else, ale vše se naučíte během kurzu.</p>
<button>Ukaž odpověď</button>
</div>

<script>
    Array.from(document.querySelectorAll('.faq-item')).forEach((item) => {
        const button = item.querySelector('button');
        const answer = item.querySelector('p');
        
        console.log(answer.style.display);

        button.addEventListener('click', (e) => {
            console.log(e.target);

            if(answer.style.display === ''){
                answer.style.display = 'block';
                button.innerText = 'Schovej odpověď';
            } else {
                answer.style.display = '';
                button.innerText = 'Ukaž odpověď';
            }
        });
    })
</script>


### HTML jednej FAQ položky

```jsx
<div>
    <strong>Je akademie zdarma?</strong>
    <p>Akademie je zdarma pro všechny členy klubu Silicon Hill s platním základním a síťovím členstvím.</p>
    <button>Ukaž odpověď</button>
</div>
```



### Texty tlačidla

- `Schovej odpověď`
- `Ukaž odpověď`


### Texty FAQ položiek

```
Je akademie zdarma?
```

```
Akademie je zdarma pro všechny členy klubu Silicon Hill s platním základním a síťovím členstvím.
```
---
```
Co si vzít sebou?
```

```
Vlastní notebook.
```
---

```
Co musím mít nainstalováno v notebooku?
```
```
Node.JS, Editor zdrojového kódu, např. Visual Studio Code.
```
---
```
Musím umět programovat?
```
```
Je dobré znát nějaké základní pojmy jako je if a else, ale vše se naučíte během kurzu.
```
<br/>
<br/>
<br/>
<br/>
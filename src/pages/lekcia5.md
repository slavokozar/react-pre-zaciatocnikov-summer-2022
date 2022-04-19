---
title: "Lekcia 5"
heading: "Lekcia 5 - Pripojenie na API"
layout: ../layouts/Lekcia.astro
---

## Pouzitie .env

### Motivácia

- aplikácia často beží na lokálnom, testovacom, produkčnom rozhraní
- na týchto rozhraniach chceme mať aplikáciu ( napríklad ) pripojenú k rôznym verziam API (lokálne API, testovacie API...)
- nechceme aby sa naše heslá / tokeny ukladali mimo našej kontroly na gite
- čo ak náš kolega s ktorym vyvíjame aplikáciu používa inú adresu lokálneho API?
- co ak má náš kolega iný token pre API?



`.env` je štandardný súbor ktorý sa používa v množstve moderných frameworkov (React, Laravel, Symfony, Flusk, Next.js ...) a je zahrnutý v `.gitignore` - nikdy sa nedostane do vzdialeného git repozitára


### Vytvorenie env súbora

Vytvorme subor .env v roote projektu.

Tento súbor obsahuje dvojice:
```
NAZOV_PREMENNEJ="hodnota"
```

**Pozor!**

**Keďže React často zdieľa repozitár a projekt aj s nejakou ďalšou technológiou musia všetky env premenná použité v React aplikácii začínať prefixom REACT_APP teda:**


```
REACT_APP_NAZOV_PREMENNEJ="hodnota"
```

V našom prípade

```
REACT_APP_API_URL="https://todo.eragon.digital/api/"
REACT_APP_API_TOKEN="react-pro-zacatecniky"
```

**Pozor!**

**Hodnoty env premenných sa aplikujú len v monente štartu procesu projektu - v prípade zmeny hodnôt env premenných je nutné vypnúť proces aplikácie a znova ho spustiť pomocou `npm start`.**


### Použitie env premenných v kóde

V aplikácii potom tieto hodnoty použijeme pomocou `process.env.RREACT_APP_API_URL` a `process.env.RREACT_APP_API_TOKEN`

V App.js potrebujeme nahradiť volanie API so staticky definovanou URL a tokenom za verziu ktorá využíva env premenné.

```js
axios.get( 'https://todo.eragon.digital/api/tasks?api_token=react-pro-zacatecniky' );
```

URL pre api call potrebujeme zložiť zo statických častí a dynamických env premenných.

**Prvá možnosť je využiť operátor + určený pre spájanie reťazcov:**
```js
axios.get( process.env.REACT_APP_API_URL + '/tasks?api_token=' + process.env.REACT_APP_API_TOKEN )
```

**Druhá (preferovaná ES6 možnosť) je použitie tzv. `template literals`**
```js
axios.get( `${process.env.REACT_APP_API_URL}/tasks?api_token=${process.env.REACT_APP_API_TOKEN}` )
```

Viac info o template literals:

<a href="https://www.hongkiat.com/blog/ecmascript-6-template-literals/" target="_blank">https://www.hongkiat.com/blog/ecmascript-6-template-literals/</a>

### Git 

Vzorové riešenie s použitím `.env` súboru je na git-e:

<a href="https://github.com/slavokozar/react-pre-zaciatocnikov-todo-project/tree/pouzitie_env_premennych" target="_blank">https://github.com/slavokozar/react-pre-zaciatocnikov-todo-project/tree/pouzitie_env_premennych</a>



**Pozor!**

**Na gite nie je dostupný .env súbor. Je tam dostupný `.env.example` súbor, ktorý je nutné prekopírovať do súboru `.env` v koreňovom adresári projektu.**

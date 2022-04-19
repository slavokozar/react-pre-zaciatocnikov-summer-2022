---
title: "Lekcia 5"
heading: "Lekcia 5 - Pripojenie na API"
layout: ../layouts/Lekcia.astro
---

## CRUD s použitím API 

Základné operácie s dátami často nazývame aj CRUD. Jednotlivé písmená tejto skratky pomenúvajú základné operácie, ktoré je možné s dátami robiť.

- **C**reate 
- **R**ead
- **U**pdate
- **D**elete

V ToDo aplikácii sme zatiaľ implementovali operáciu Read. Témou nasledujúceho cvičenia bude teda implementácia operácii Create, Update a Delete. 


### Create

Pre vytvorenie nového tasku využijeme API endpoint zdokumentovaný na 
<a href="https://todo.eragon.digital/#endpoints-POSTapi-tasks" target="_blank">https://todo.eragon.digital/#endpoints-POSTapi-tasks</a>.

Tento endpoint očakáva request typu `POST`. 

Hlavným rozdielom pri volaní endpointu requestom typu `POST` voči `GET` spočíva v pridaní dalšieho parametra ktorý obsahuje dáta odoslané v requeste. 

```js
axios.post('URL', {
    atribut1: 'Hodnota 1',
    atribut2: 'Hodnota 2'
})
```

Post request pre vytvorenie nového tasku bude teda 

```js
const response = await axios.post(`${process.env.REACT_APP_API_URL}/tasks?api_token=${process.env.REACT_APP_API_TOKEN}`, {
    text: input
});
```

Ideálne miesto pre poslanie requestu na endpoint je vo funkcii `function handleSubmit(e)` ktorá je vykonaná po odoslaní formulára. 

Keďže v tejto metóde chceme použiť kľúčové slovo `await` v pre asynchrónne správanie metódy `axios.post` definíciu funkcie musíme rozšíriť o kľúčové slovo `async`. 

Odpoveď z tohto endpointu obsahuje dáta vo formáte určenom pre zobrazenie v našej aplikácii. 

Túto odpoveď preto využijeme pre uloženie novo vytvoreného tasku do našeho state atribútu `tasks`. 

Finálna implementácia vytvorenie nového tasku je na gite:
https://github.com/slavokozar/react-pre-zaciatocnikov-todo-project/blob/api-crud/src/App.js


### Update

Pre úpravu existujúceho tasku využijeme api endpoint http://todo.eragon.digital/#endpoints-PUTapi-tasks--id-

Tento endpoint definovaný podľa REST štandardu - používa request typu `PUT`, alebo `PATCH`. 

Tento typ requestu - podobne ako request typu `POST` posiela na server data.

Základná syntax odoslania requestu typu `PUT`


```js
axios.put('URL', {
    atribut1: 'Hodnota 1',
    atribut2: 'Hodnota 2'
})
```
```js
axios.patch('URL', {
    atribut1: 'Hodnota 1',
    atribut2: 'Hodnota 2'
})
```

Pre účely úpravy existujúceho tasku vytvoríme novú asynchrónnu funkciu handleActiveChange s parametrami `task` - objekt tasku, ktorý chceme upraviť a `active` - novú hodnotu atribútu active tohto tasku.

Táto funkcia odošle request na API a následne upraví task v state aplikácie.

Finálna implementácia úpravy tasku je na gite:
https://github.com/slavokozar/react-pre-zaciatocnikov-todo-project/blob/api-crud/src/App.js


---

**Tip!**

Pre úpravu stavu obsahujúcom tasky v ToDo aplikácii sme používali `index` tohto tasku v poli. 

V prípade, že sme napojení na API máme možnosť využiť unikátny identifikátor `id` ktorý obsahuje každý task.

---

**Tip!**

Doteraz sme pre detekovanie udalostí používali arraw funkcie. 
Napríklad:

```jsx
<button onClick={() => {  
    ...
}}>
```

Ak v tejto funkcii chceme použiť kľúčové slovo `async` funkcia musí byť definovaná ako asynchrónna. To v tomto prípade nie je možné. 
V praxi sa tento problém rieši definovaním asynchrónnej funkcie a následne volaním tejto funkcie v event listeneri. 

```jsx
async function handle(){
    
}

<button onClick={() => {  
    handle();
}}>
```

### Delete

Pre úpravu existujúceho tasku využijeme api endpoint http://todo.eragon.digital/#endpoints-DELETEapi-tasks--id-

Finálna implementácia vymazania tasku je na gite:
https://github.com/slavokozar/react-pre-zaciatocnikov-todo-project/blob/api-crud/src/App.js



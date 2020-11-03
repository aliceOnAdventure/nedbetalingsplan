# nedbetalinsplan
Jeg har brukt vue 2.0 for å løse kodeoppgaven. For instrukser om hvordan
komme i gang med vue, se https://vuejs.org/v2/guide/.

Bruker du kommandolinjen, naviger til mappen med prosjetet (nedbetalingsplan). For å kjøre appen kan du enten kjøre kommandoen "npm run serve" fra kommandolinjen, eller "vue ui" for å åpne en GUI hvor du kan starte oppgaven "serve" (jeg foretrekker den første måten).

Jeg har valgt å hente nedbetalingsplanen fra APIet deres, for så å vise det i en tabell. Over tabellen er det en collapsable komponent som gjør det mulig for brukeren å endre på informasjonen av lånet. Altså endre lånebeløpet, osv. Her har jeg ikke brukt noe til på å "sikre" inputen til brukeren, men det er nok det neste jeg ville gjort. Tabellen som viser nedbetalinsplanen er en egen komponent, for å gjøre det enklere å gjøre endringer i den ene komponenten uten at det skal kreve store endring i den andre.

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

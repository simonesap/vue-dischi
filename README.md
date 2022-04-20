# vue-dischi

# vue-cli-rick-and-morty

# 1° Creare il progetto con Vue cli
Dopo aver creato la repository vuota su github, la cloniamo sul pc e apriamo lacartella con vs code.
Utilizzando il terminale nella cartella del progetto il comando Node:

```
vue create .
```

# 2° Importare Boostrap 5 (opzionale)
Per importarlo dobbiamo lanciare da terminale due comandi:

```
npm install --save boostrap
```

```
npm install --save @popperjs/core
```

Dopo aver installato le 2 dipendenze di boostrap 5 dobbiamo importare i file CSS e JS di riferimento dentro app.vue

Dentro la sezione "script" scriviamo:
```
import "boostrap"
```

Dentro la sezione "style" scriviamo: 
```
@import 'bootstrap/dist/css/bootstrap.min.css';
```

Da qui in poi possiamo usare le classi di Boostrap 5

# 3° Creiamo un componente
Prima cosa creare un file all'interno della cartella "components", il nome del file deve essere con la prima lettera maiuscola e di due
parole in camelcase,
esempio: HeaderComp.vue

La struttura del componente deve essere all'inizio la seguente:

``` javascript
<template>
  <div id="app">
    <header>
    <!--Inserire il contenuto del componente>
    </header>
  </div>
</template>

<script>

export default {
    // Cambiare il nome con quello del componente creato
  name: 'HeaderComp',
  components: {
  }
}
</script>

<style lang="scss">
/* Inserire style del componente */

@import 'bootstrap/dist/css/bootstrap.min.css';

</style>
```

Secondo passaggio andare in app.vue e importare il componente alli'interno dello "script" in questo modo:

``` javascript
<script>
import './HeaderComp.vue'
import 'bootstrap/dist/css/bootstrap.min.css';

export default {
  name: 'App',
  components: {
      // Inseriamo il nome del componente
    HeaderComp,
  }
}
</script>
```

Utilizziamo il componente ndentro il template di app.vue in questo modo:

``` javascript
<template>
  <div id="app">
    <HeaderComp
  </div>
</template>
```

# 4° Utilizzare Axios nel progetto

Per utilizzarlo dobbiamo importare Axios tramite npm da terminale con questo comando:

``` javascript
npm i axios
```

Dopo l'installazione bisogna importarlo nel componente di utilizzo nella sezione script
in questo modo:

``` javascript
<script>
// Importiamo Axios
import axios from 'axios';

// Cambiare il nome con quello del componente creato
export default {
  name: 'AvatarComp',
  data() {
      return {
          // Creare un array dove salvare i dati della chiamata axios
          // modificare il nome a piacere
          avatarsArray: [],
      }
  },
  components: {
      CardAvatar,
  },
  created() {
      // Qui utilizziamo axios
      // modificare il link con l'API che si vuole usare
      axios.get('https://flynn.boolean.careers/exercises/api/array/music')
      .then( (res) => {
          // Controllo delle informazioni che otteniamo alla chiamata
        console.log( res.data );
        // Pusho in automatico l'array dell'API nel mio array vuoto senza fare push
        // Modifica dell'array dove salveremo i dati
        this.avatarsArray = res.data
      } )
      // Salvataggio in console di possibili errori
      .catch( (error) => {
          console.log( error )
      })
  }
 
}
</script>
```

...
# 5 Come usare i props tra componente padre e figlio

I props ci servono quando vogliamo passare le informazioni tra due componenti
e il componente padre è colui che ha i dati da passare al componente figlio.


Componente padre:
``` javascript
<template>
  <div id="app" class="row">

        // Questo è il componente figlio a cui passare i props
          <CardAvatar
            v-for="(element, index) in avatarsArray"
            // Qui abbiamo i props dei dati che vogliamo passare al figlio "CardAvatar"
            // Questi dati sono ottenuti tramite axios e salavti in un array nei "Data"
            // Sono alcune informazioni del JSON dell'API
            :key="index"
            :image="element.image"
            :name="element.name"
            :species="element.species"
            :origin="element.origin"
          />

  </div>
</template>

<script>
// Importiamo Axios
import axios from 'axios';

// Cambiare il nome con quello del componente creato
export default {
  name: 'AvatarComp',
  data() {
      return {
          // Creare un array dove salvare i dati della chiamata axios
          // modificare il nome a piacere
          avatarsArray: [],
      }
  },
  components: {
      CardAvatar,
  },
  created() {
      // Qui utilizziamo axios
      // modificare il link con l'API che si vuole usare
      axios.get('https://flynn.boolean.careers/exercises/api/array/music')
      .then( (res) => {
          // Controllo delle informazioni che otteniamo alla chiamata
        console.log( res.data );
        // Pusho in automatico l'array dell'API nel mio array vuoto senza fare push
        // Modifica dell'array dove salveremo i dati
        this.avatarsArray = res.data
      } )
      // Salvataggio in console di possibili errori
      .catch( (error) => {
          console.log( error )
      })
  }
 
}
</script>
```

IL  componente figlio:
``` javascript
<template>

    <div class="col-3 text-center my-5">
    // Inserire il componente
    // Il contenuto del componente richiama le informazioni dei props
        <img :src="image" alt="" class="rounded-circle">
        <h3 class="my-3">{{name}}</h3>
        <div class="divider my-3"></div>
        <h4 class="my-3">{{origin}}</h4>
        <span class="fw-bolder my-3">{{species}}</span>
    </div>

</template>

<script>

export default {
  name: 'CardAvatar',
  // Sezione dove riportare i props e la loro tipologia
  props: {
      image: String,
      name: String,
      species: String,
      origin: String,
  },
  components: {
  },
 
}
</script>

<style lang="scss">
// @import 'bootstrap/dist/css/bootstrap.min.css';

    .divider {
        width: 30%;
        height: 1px;
        background-color: #1a1a1a;
        margin: 0 auto;
    }

</style>
```
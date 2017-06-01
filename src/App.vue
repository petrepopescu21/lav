<!-- WELCOME! 

Cateva reguli de baza legate de template - de fapt, doar una:
!!! In interiorul lui <template> va exista UN SINGUR TAG parent. (foi folosi div peste tot in exemple. se aplica pentru orice tag de HTML)

<template>
  <div>
    blablabla alte divuri etc
  </div>
<template>

^ this is fine

<template>
  <div>
    bla bla
  </div>
  <div>
    bla bla
  </div>
</template>

^ this is not fine.

-->
<template>
  <div id="app">
    <header>
      <span>Secretariat virtual</span>
    </header>
    <main>
    <!-- am lasat un img pentru a vedea cum arata src-ul -->
      <img src="./assets/logo.png" alt="Vue.js PWA">
      <!-- Hello este o alta componenta, ii poti vedea sursa in src/components/Hello.vue -->
      <hello></hello>
      <!-- vom reveni asupra minunii de aici un pic mai jos -->
      <h1>{{title}}</h1>
      <div>{{firstElement}}</div>
    </main>
  </div>
</template>

<!-- Aici incepe partea mai complicata, anume javascript -->
<script>
// import este un fel de using. Aici incarcam componenta Hello.vue intr-o variabila numita Hello.

// importarea componentei este primul pas necesar pentru a o putea folosi in template
import Hello from './components/Hello'
// fiecare componenta are un export default. Gandeste-te la un void main() din C++, basically the same thing.
export default { 

  //bracket-urile de aici noteaza un obiect de tip JSON (JavaScript Object Notation).
  //Daca nu stii cum arata un JSON, look it up.

  //export default-ul are multe posibile proprietati (sau key-uri, inca vorbim de un JSON)
  //cateva notabile:
  /*

  name: '' - numele componentei folosit in incarcare recursiva (nu vom face asta, dar e best practice sa ii dai acest nume)
  components: { } - o lista de componente importate anterior pe care le vom folosi in template
  data () { } - o functie care reprezinta datele dinamice pe care le vom folosi in template sau in componente din template
  props: { } - un obiect in care incarcam datele primite de la o alta componenta
  computed: { } - computed este o lista de functii si se foloseste pentru a lua obiecte din data sau props, a le prelucra, si a le oferi prelucrate catre template
                  in template vom folosi numele functiei care va lua valoarea return-ului din interior
  created () { } - o functie care va rula automat atunci cand o componenta este creata

  si multe altele... exista documentatie online :)

  */
  name: 'app',
  components: {
    // Aici incarcam in "components" componentele importate mai devreme pe care le vom folosi in template
    Hello
    // Daca ar fi mai multe compontente, le-am fi pus cu virgula:
    // Hello,Navbar,News
  },
  data () {
    //din cauza ca data este o functie, va trebui sa aibe un return. Return-ul va returna tot un JSON
    return {
      title: "Secretariat Virtual",
      exampleArray: [
        "something", "something", "dark", "side"
      ]
    }
  }, //end of data
  computed: {
      //spre exemplu, o sa luam doar primul element din acel array de mai sus si il vom folosi in template
      firstElement () {
        // this se refera la aceasta componenta vue. NU trebuie specificat de unde luam o anume valoare (fie din data, computed sau props)
        return this.exampleArray[0]
      }
  }
}
</script>


<!-- Tag-ul de style contine CSS. That's all there is to it -->
<style>
body {
  margin: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

main {
  text-align: center;
  margin-top: 40px;
}

header {
  margin: 0;
  height: 56px;
  padding: 0 16px 0 24px;
  background-color: #4fc08d;
  color: #ffffff;
}

header span {
  display: block;
  position: relative;
  font-size: 20px;
  line-height: 1;
  letter-spacing: .02em;
  font-weight: 400;
  box-sizing: border-box;
  padding-top: 16px;
}
</style>

<template>
<!-- citeste intai partea de script, revino apoi aici -->
  <div class="hello">
<!-- revenind....

Acum in apiresponse avem un array cu 100 de item-uri. Pentru a le afisa pe toate, vom folosi un <ul> cu o directiva (cuvant rar) for.
Check this out: -->
    <ul>
      <li v-for="item in apiresponse">
        <!--aici, putem folosi item-->
        <span>{{item.title}}</span>
        <!-- and that's about it. te las sa incerci si tu sa faci o componenta -->
      </li>
    </ul>
    
  </div>
</template>

<script>
//Aici vom face ceva mai ciudat pentru a demonstra cum se incarca date dinamice dintr-un API (ca cel facut de David)
//Pentru asta, voi folosi o biblioteca numita AXIOS pentru a face HTTP requests
//Pentru date, vom folosi https://jsonplaceholder.typicode.com/posts/1

//vom initializa o variabila goala in "data", apoi vom incarca datele create in handler-ul "created" despre care am scris mai devreme
import Axios from 'axios'
export default {
  
  name: 'hello',
  
  data () {
    return {
      apiresponse: [] //vom primi un array ca raspuns de la jsonplaceholder, asa ca definim un array
    }
  },

  created () {
    //Chestia asta cu _this este un hack pentru felul in care lucreaza created. Just go with it for now.
    var _this = this
    //Axios returneaza promisiuni (chiar asa se numesc, promises) care se rezolva prin then. Imagineaza-ti then-ul ca un fel de await din C#
    //Await-ul de javascript, desi exista, inca nu este generally supported de browsere
    Axios.get('https://jsonplaceholder.typicode.com/posts')
         .then(function(response) {
           //Mai sus avem o functie anonima. Exista doar in scope-ul acestui then, de aceea nu este nevoie sa ii dam un nume
           _this.apiresponse=response.data
         })

         //in acest punct, apiresponse va avea informatia primita de la jsonplaceholder (poti accesa link-ul sa vezi exact informatia)
         //Informatia este un json cu 100 de iteme. Fiecare post are un titlu. Le vom afisa pe toate in template
         //Scroll up!
  }
}
</script>

<style>
  ul {
    list-style: none;
  }
</style>

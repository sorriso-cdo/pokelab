<template>
 <div>
     <div class="card" style="width: 18rem;">
  <img src="" class="card-img-top" alt="...">
  <div class="card-body">
      <h1> {{ url }} </h1>
    <img :src="pokemon.sprites.front_default" class="card-img-top" alt="..">  
    <h3 class="card-title">{{ pokemon.name }}</h3>
    <h5 class="card-title">Height: {{ pokemon.height * 3.937 }} inches</h5>
    <h5 class="card-title">Weight: {{ pokemon.weight }} pounds</h5>

    <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
    <a href="#" class="btn btn-primary">Go somewhere</a>
  </div>
</div>
 </div>
</template>

<script>
export default {
  name: 'card',
  data: function () {
      return {
      pokemon: "",
      
      }
  },
  props: {
    url: String
  },
  mounted: function() {
    console.log("mounted function ran")

    const axios = require('axios');
    const vm = this;

     axios({
        method: 'get',
        url: vm.url,
        responseType: 'stream'
        })
     .then(function (response) {
         console.log(response.data);
         vm.pokemon = response.data

  });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

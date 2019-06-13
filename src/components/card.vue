<template>
 <div class="col-3">
     <div class="card" style="width: 18rem;">
        <img :src="pokemon.sprites.front_default" class="card-img-top" alt="..">  
        <div class="card-body">
            <h5 class="card-title text-capitalize">{{ pokemon.name }}</h5>
            <p class="card-title">Height: {{ pokemon.height * 3.937 }} inches</p>
            <p class="card-title">Weight: {{ pokemon.weight }} pounds</p>
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
.card {
    text-align: center;
    margin-bottom: 30px;

}
</style>

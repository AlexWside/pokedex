<template>
  <v-app>

   <div class="aplication">
    <div class="titulo">
        Pokédex
    </div>
   
   <Pokedex/>
   </div>
 

  </v-app>
</template>

<script>

import Pokedex from "./components/pokedex.vue"


export default {
  name: 'App',

  components: {
  
    Pokedex
  },

  data: () => ({
    //
  })
};
</script>


<style >

@font-face {
  font-family: pokemon;
  src: url('fonts/Pokemon-Solid.ttf');
}

.aplication{
  margin-top: 3rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  
}

.v-application--wrap{
  background: radial-gradient(circle, rgba(255,255,255,1) 17%, rgba(72,156,255,1) 46%, rgba(255,29,29,1) 68%);
}

   
.titulo{
  font-family: pokemon;
 font-size: 3em;
 margin: 2rem;
 color: yellow;
 text-shadow: 2px 0 0 #1852f2, -2px 0 0 #1852f2, 0 2px 0 #1852f2, 0 -2px 0 #1852f2, 1px 1px #1852f2, -1px -1px 0 #1852f2, 1px -1px 0 #1852f2, -1px 1px 0 #1852f2;
 
}
</style>
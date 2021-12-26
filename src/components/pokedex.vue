<template>
  <div id="pokedex">
    <div class="display">
      <div class="resultado">
        <span v-if="resultado == 'aguardando...'"> {{ resultado }}</span>
        <span v-else>
          <img
            width="100"
            :src="resultado.sprites.front_default"
            alt="resultado"
          />
          <center>{{ pokemon }}</center>
        </span>
      </div>
    </div>
    <div class="busca">
      <input type="text" v-model="pokemon" @keyup.enter="buscar()" />

      <div class="btn-area">
        <div class="luzes">
          <span class="bolinha bg-blue"></span>
          <span class="bolinha bg-yellow"></span>
          <span class="bolinha bg-green"></span>
        </div>

        <button class="btn-busca" @click="buscar()"></button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      resultado: "aguardando...",
      pokemon: "",
    };
  },
  methods: {
    buscar() {
      // Faz uma requisição a um usuarío com um ID expecifico
      axios
        .get("https://pokeapi.co/api/v2/pokemon/" + this.pokemon, {
          headers: {
            Accept: "application/json",
            "Content-Type": "application/json",
          },
        })
        .then((response) => {
          this.resultado = response.data;
        });
    },
  },
};
</script>

<style scoped>
#pokedex {
  background-color: rgb(255, 75, 75);
  width: 20rem;
  height: 30rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  border-radius: 10px;
}
.display {
  background-color: #383232;
  width: 80%;
  height: 50%;
  margin-top: 2rem;
  border: 10px solid steelblue;
  border-radius: 10px;
}

.btn-busca {
  display: flex;
  border: 10px solid #ccc;
  border-radius: 60%;
  background-color: steelblue;
  width: 80px;
  height: 80px;

  
}

.busca input {
  width: 80%;
  background-color: #fff;
  outline: none;
  border-radius: 5px;
}

.busca {
  width: 100%;
  margin-top: 1rem;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.resultado {
  width: 100%;
  height: 100%;
  color: #fff;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.bolinha {
  width: 10px;
  padding:9px 9px;
  height: 10px;
  border-radius: 50%;
  margin: 0.2em;
  border: 1px solid #fff;
}

.bg-green {
  background-color: rgb(62, 237, 62);
}
.bg-yellow {
  background-color: yellow;
}
.bg-red {
  background-color: red;
}

.btn-area {
  width: 90%;
  height: 150px;
  display: flex;
  flex-direction: row;
  align-items: center;
}

.luzes{
display: flex;
height: 100%;
flex-direction: column;
justify-content: end;
width:65%;
}
</style>


<script lang="ts" setup>
import { onMounted, ref, toRefs } from "vue";
import axios from "axios";

interface dataTypes {
  name: string;
  url: string;
}

const data = ref<object>();

onMounted(() => {
  axios("https://pokeapi.co/api/v2/pokemon").then((res) => {
    data.value = res.data.results;
    console.log(res.data);
  });
});
</script>

<template>
  <div class="container">
    <div class="card">
      <div class="pokemon" v-for="(pokemon, index) in data" :key="index">
        <router-link :to="{ name: 'about', params: { id: pokemon.url } }">
          {{ pokemon.name.toUpperCase() }}
        </router-link>
      </div>
    </div>
  </div>
</template>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.card {
  display: flex;
  flex-wrap: wrap;
  gap: 15px;
  height: 600px;
  margin: 0;

  .pokemon {
    display: flex;
    justify-content: center;
    align-items: center;
    flex: 1;
    margin: 0;
    height: 100px;
    border: 5px solid black;
    border-radius: 4px;
    padding: 0px 20px;
    a {
      color: black;
      font-weight: bold;
    }
  }
  .pokemon_img {
    width: 200px;
    height: 200px;
  }
}
</style>

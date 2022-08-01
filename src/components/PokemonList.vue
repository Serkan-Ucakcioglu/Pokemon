<script lang="ts" setup>
import { onMounted, ref } from "vue";
import axios from "axios";

interface dataTypes {
  name: string;
  url: string;
}

const data = ref<object>();

onMounted(() => {
  axios("https://pokeapi.co/api/v2/pokemon").then((res) => {
    data.value = res.data.results;
  });
});
</script>

<template>
  <div class="container">
    <!--head title-->
    <h1>Which pokemon would you like to go to?</h1>
    <!--card -->
    <div class="card">
      <!--Pokemon data-->
      <div class="pokemon" v-for="(pokemon, index) in data" :key="index">
        <!--dynamic router-->
        <router-link :to="{ name: 'about', params: { url: pokemon.url } }">
          {{ index + 1 }}. {{ pokemon.name.toUpperCase() }}
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
  margin-top: 20px;

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
      display: flex;
    }
  }
  .pokemon_img {
    width: 200px;
    height: 200px;
  }
}
</style>

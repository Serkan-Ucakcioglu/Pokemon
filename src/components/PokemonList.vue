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
      <router-link to="/" class="pokemon">
        <div class="list"  v-for="(pokemon, index) in data" :key="index">
        <h1>{{pokemon.name}}</h1>
        </div>
      </router-link>
    </div>
  </div>

</template>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.pokemon {
  display: flex;
  flex-wrap: wrap;
  gap: 15px;
  height: 600px;

  .list {
    display: flex;
    justify-content: center;
    align-items: center;
    flex: 1;
    height: 100px;
    border: 5px solid black;
    border-radius: 4px;
    padding: 0px 20px;
  }
  .pokemon_img {
    width: 200px;
    height: 200px;
  }
}
</style>

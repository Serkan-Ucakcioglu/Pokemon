<script setup lang="ts">
import { onMounted, defineProps, reactive } from "vue";
import axios from "axios";

interface dataTypes {
  name: string;
  id: number;
  back: string;
  backshiny: string;
  default: string;
  url: string;
}

const data: dataTypes = reactive({
  name: "",
  url: "",
  back: "",
  default: "",
  backshiny: "",
  id: 0,
});
const props = defineProps<{
  url: string;
}>();

onMounted(() => {
  axios(`${props.url}`).then((res) => {
    data.name = res.data.name;
    data.back = res.data.sprites.back_default;
    data.backshiny = res.data.sprites.back_shiny;
    data.default = res.data.sprites.front_default;
    data.url = res.data.sprites.front_shiny;
    data.id = res.data.id;
    console.log(res.data);
  });
});
</script>

<template>
  <div class="container">
    <!--card -->
    <div class="card-detail">
      <h1>{{ data.name.toUpperCase() }}</h1>
      <h3>Id : {{ data.id }}</h3>
      <!--Pokemon Img-->
      <div class="pokemon">
        <img :src="data.url" alt="" />
        <img :src="data.back" alt="" />
        <img :src="data.backshiny" alt="" />
        <img :src="data.default" alt="" />
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.container {
  display: flex;
  justify-content: center;
  .card-detail {
    width: 800px;
    color: black;
    border-radius: 4px;
    background-color: white;

    .pokemon {
      display: flex;
      justify-content: space-around;
      img {
        border: 3px solid #5c5a5a;
        border-radius: 4px;
        margin-bottom: 10px;
        padding: 5px;
      }
    }
  }
}
@media only screen and (max-width: 600px) {
  .pokemon {
    flex-direction: column !important;
    align-items: center;

    width: 100%;
  }
}
</style>

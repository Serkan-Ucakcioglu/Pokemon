<script setup lang="ts">
import { onMounted, defineProps, reactive } from "vue";
import axios from "axios";

interface dataTypes {
  name: string;
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
  });
});
</script>

<template>
  <div class="container">
    <!--card -->
    <div class="card-detail">
      <h1>{{ data.name.toUpperCase() }}</h1>
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
    width: 300px;
    border: 4px solid black;
    border-radius: 4px;
    box-shadow: 0 0 6px 8px rgba(0, 0, 0, 0.2);
  }
}
</style>

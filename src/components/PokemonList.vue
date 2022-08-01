<script lang="ts" setup>
import { onMounted, reactive } from 'vue';
import axios from "axios"

interface dataTypes {
    name: string,
    url: string,
}

 const data: dataTypes = reactive({
    name: '',
    url: ''
})

onMounted(() => {
    axios('https://pokeapi.co/api/v2/pokemon')
    .then(res => {
        console.log(res.data.results);
    })
})

</script>

<template>
 <h1>helloworld</h1>
</template>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>

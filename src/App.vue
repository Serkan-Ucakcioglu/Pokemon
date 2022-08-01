<template>
  <router-view />
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #f1f1f1;
  margin-top: 120px;
}
.container {
  max-width: 1200px;
  margin: 0px auto;
}
a {
  text-decoration: none;
}
@media only screen and (max-width: 600px) {
  .continer {
    width: 90% !important;
  }
}
</style>

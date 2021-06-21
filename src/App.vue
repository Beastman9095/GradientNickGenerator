<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.header {
  display: grid;
}
.header h1{
  color: #C2DACB;
  position: relative;
}
.header img{
  position: absolute;
  padding-left: 20%;
  padding-top: 0.3%;
}
</style>

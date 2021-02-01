<template>
  <div id="app">
    <Home/>
  </div>
</template>

<script>
import Home from "@/components/Home";

export default {
  name: 'App',
  components: {
    Home,
  }
}
</script>

<style>
*{
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
#app {
  height: 100vh;
  width: 100vw;
  background: #F2F2F2;
  padding: 100px 0;
  font-family: 'Roboto', sans-serif;
  font-weight: 300;
  text-align: center;
  color: black;
}
</style>

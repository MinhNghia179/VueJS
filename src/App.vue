<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Welcome to Your Vue.js App" />
  <TotalNumber />
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import TotalNumber from './components/TotalNumber.vue';

export default {
  name: 'App',
  components: {
    HelloWorld,
    TotalNumber,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

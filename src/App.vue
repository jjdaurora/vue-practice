<template>
  <div id="app">
    <test msg="Merry Christmas!"></test>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import Test from "./components/Test.vue";

export default {
  name: "app",
  components: {
    HelloWorld,
    Test
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

<template>
  <div id="app">
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <game/>
  </div>
</template> 

<script>
import HelloWorld from "./components/HelloWorld.vue";
import game from './components/game.vue'

export default {
  name: "App",
  components: {
    HelloWorld,
    game,

  },

  data: function () {
    return {
      total: 0, //ผลรวมทั้งหมด ---> เอาไปแสดงผล{{}}
      name: "",
      code: "",
      gpa: "",
    };
  },

  methods: {
    sum(counterValue) {
      this.total += counterValue;
    },
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

<template>
  <!-- <CreatePoll msg="Welcome to Your Vue.js App"/> -->
  <polls msg="Welcome to Your Vue.js App" />
</template>

<script>
import Polls from "./components/Polls.vue";
//import CreatePoll from './components/CreatePoll.vue'

export default {
  name: "App",
  components: {
    Polls,
    //CreatePoll
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
}
</style>

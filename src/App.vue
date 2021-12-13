<template>
  <div id="app">
    <section>
      <h3>Rover Types</h3>
      <br />
      <input type="radio" v-model="rover" value="0" />Curiosity
      <input type="radio" v-model="rover" value="1" />Opportunity
      <input type="radio" v-model="rover" value="2" />Spirit
      <br />
    </section>
    <HelloWorld msg="The Mars Files" :rover="rover" />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
  data() {
    return {
      rover: "0",
    };
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

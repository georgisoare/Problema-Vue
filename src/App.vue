<template>
  <h1>{{ title }}</h1>
  <Content />
</template>

<script>
import Content from "./components/Content.vue";

export default {
  name: "App",
  components: {
    Content,
  },

  data() {
    return {
      title: "Problemă Vue",
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

h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>

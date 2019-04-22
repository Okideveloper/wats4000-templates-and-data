<template>
  <div id="app">
    <results></results>
  </div>
</template>

<script>
import Results from "@/components/Results";
export default {
  name: "app",
  components: {
    Results
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
}
p {
  padding-bottom: 20px;
}
h1 {
  text-align: center;
  font-family: Verdana;
}
h2 {
  text-align: center;
}
.results {
  font-family: Arial, sans-serif;
  font-weight: 500;
  font-size: 18px;
  width: 75%;
  margin: 0 auto;
  text-align: left;
  background: #fff;
  padding: 2rem;
}
.ratings {
  text-align: left;
}
.total-pages,
.total-results {
  font-size: 15px;
}

a {
  cursor: pointer;
}
html,
body {
  margin: 0;
  padding: 0;
  background: #4c40be;
}
</style>

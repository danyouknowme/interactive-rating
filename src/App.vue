<template>
  <div id="app">
    <Card />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Card from "@/components/Card.vue";

@Component({
  components: {
    Card,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Overpass:wght@400;700&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  width: 100vw;
  height: 100vh;
  background-color: hsl(216, 12%, 8%);
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: "Overpass", sans-serif;
}
</style>

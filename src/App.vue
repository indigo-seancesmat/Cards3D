<template>
  <div id="app">
    <Card3D :bg-image="mountain" :depth-map="mountainDepth" :sensitivity="25">
      <h1 slot="header">Mountains</h1>
      <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing elit.</p>
    </Card3D>
    <TippyCard :bg-image="subway" :depth-map="subwayDepth" :sensitivity="25">
      <h1 slot="header">Subway</h1>
      <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing elit.</p>
    </TippyCard>
  </div>
</template>

<script>
import TippyCard from "./components/TippyCard";
import Card3D from "./components/Card3D";
import subway from "@/assets/subway.jpg";
import subwayDepth from "@/assets/subway-depth.jpg";
import mountain from "@/assets/mountain.jpg";
import mountainDepth from "@/assets/mountain-depth.jpg";

export default {
  name: "App",
  components: {
    TippyCard,
    Card3D
  },
  data() {
    return {
      subway,
      subwayDepth,
      mountain,
      mountainDepth
    };
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

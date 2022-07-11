<template>
  <div v-if="nodeCards.length"  class="container">
    <NodeCards 
    init
    v-for="(elem, index) in nodeCards" :key="index"
    :node="nodeCards[index]" />
  </div>
</template>

<script>
import NodeCards from "./components/NodeCards.vue";

export default {
  name: "App",
  components: { NodeCards },
  data() {
    return {
      nodeCards: [],
    };
  },
  created() {
    fetch("https://functions.yandexcloud.net/d4e7argpi2fe7epuh65b")
      .then((data) => {
        return data.json();
      })
      .then((data) => {
        this.nodeCards = data;

        console.log(this.nodeCards)
      });
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;500&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-color: #f5f5f5;
}

#app {
  font-family: "Roboto", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #000;
  font-weight: 400;
  height: 100vh;
}

.container {
  width: 100%;
  height: 100%;
  padding: 90px;
}

.node-card {
  background: #ffffff;
  box-shadow: 0px 4px 15px rgba(0, 0, 0, 0.25);
  border-radius: 5px;
  display: flex;
  flex-direction: column;
  max-width: 250px;
  margin-bottom: 15px;
  width: 100%;
}

.node-card__header {
  width: 100%;
  background: #7555f6;
  border-radius: 5px 5px 0 0;
}

.node-card__header p {
  color: #fff;
  font-size: 16px;
  font-weight: 500;
  padding: 20px 14px;
}

.node-card__body {
  width: 100%;
  padding: 24px 40px;
  display: flex;
  justify-content: space-between;
}
</style>

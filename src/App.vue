<script>
import AppMain from "./components/AppMain.vue";

export default {
  data() {
    return {
      img: "https://upload.wikimedia.org/wikipedia/commons/1/11/Yu-Gi-Oh%21_%28Logo%29.jpg",
      title: "Yu-Gi-Oh Api",
    };
  },

  components: { AppMain },
};
</script>

<template>
  <img :src="img" alt="" />
  <h1>{{ title }}</h1>

  <AppMain />
</template>

<style lang="scss">
body {
  h1 {
    display: inline;
    vertical-align: middle;
  }
  img {
    width: 80px;
    margin: 20px 30px;
  }
}
</style>

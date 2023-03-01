<script>
import axios from "axios";
export default {
  data() {
    return {
      cards: [],
    };
  },

  created() {
    axios
      .get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=10&offset=0")
      .then((response) => {
        console.log(response);
        this.cards = response.data.data;
      });
  },
};
</script>

<template>
  <div class="row row-cols-2">
    <div v-for="card in cards" class="col">
      <h3>{{ card.name }}</h3>
    </div>
  </div>
</template>

<style lang="scss"></style>

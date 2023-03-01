<script>
import axios from "axios";
export default {
  data() {
    return {
      cards: [],
    };
  },

  created() {
    const firstRequest = axios.get(
      "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=4&offset=0"
    );
    const secondRequest = axios.get(
      "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=11&offset=191"
    );

    axios.all([firstRequest, secondRequest]).then(
      axios.spread((...responses) => {
        const firstResponse = responses[0];
        const secondResponse = responses[1];
        this.cards = [...firstResponse.data.data, ...secondResponse.data.data];
      })
    );
  },
};
</script>

<template>
  <div class="row row-cols-5 bg-white">
    <div v-for="(card, index) in cards" v-bind:key="index" class="col">
      <img :src="card.card_images[0].image_url" class="img-fluid" alt="" />
      <h3>{{ card.name }}</h3>
      <p>{{ card.archetype }}</p>
    </div>
  </div>
</template>

<style lang="scss">
.bg-white {
  background-color: white;
}
</style>

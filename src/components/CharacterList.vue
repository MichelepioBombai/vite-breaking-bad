<script>
import axios from "axios";
import CharacterCardVue from "./CharacterCard.vue";
export default {
  data() {
    return {
      cards: [],
    };
  },

  components: { CharacterCardVue },

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
    <CharacterCardVue
      v-for="card in cards"
      :key="card.id"
      :pic="card.card_images[0].image_url"
      :name="card.name"
      :type="card.archetype"
    />
  </div>
</template>

<style lang="scss"></style>

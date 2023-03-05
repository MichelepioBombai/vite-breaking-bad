<script>
import axios from "axios";
import CharacterCardVue from "./CharacterCard.vue";
export default {
  data() {
    return {
      cards: [],
      cardTypes: [],
      selectedType: "",
    };
  },

  components: { CharacterCardVue },

  created() {
    this.getCards();
  },
  methods: {
    getCards() {
      axios
        .get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=500&offset=0")
        .then((response) => {
          this.cards = response.data.data;
          this.cardTypes = this.getCardTypes(response.data.data);
        });
    },
    getCardsByType() {
      let url = "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=15&offset=0";
      if (this.selectedType !== "") {
        url += `&type=${this.selectedType}`;
      }
      axios.get(url).then((response) => {
        this.cards = response.data.data;
      });
    },
    getCardTypes(cards) {
      let types = [];
      cards.forEach((card) => {
        if (!types.includes(card.type)) {
          types.push(card.type);
        }
      });
      return types;
    },
  },
};
</script>

<template>
  <label class="text-white fs-4 pe-3" for="card-type-select"
    >Seleziona un tipo di carta:</label
  >
  <select id="card-type-select" v-model="selectedType" @change="getCardsByType">
    <option value="">Tutti</option>
    <option v-for="(type, index) in cardTypes" :key="index" :value="type">
      {{ type }}
    </option>
  </select>
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

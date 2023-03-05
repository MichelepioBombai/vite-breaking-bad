<script>
import CharacterList from "./CharacterList.vue";

export default {
  components: { CharacterList },
};
</script>

<template>
  <main class="bg-orange">
    <div class="container">
      <CharacterList />
    </div>
  </main>
</template>

<style lang="scss">
.bg-orange {
  background-color: #d48f38;
  padding-top: 50px;
}

.select {
  width: 130px;
  border-radius: 5px;
  border: none;
  height: 30px;
}
</style>

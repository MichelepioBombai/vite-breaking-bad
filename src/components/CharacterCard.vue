<script>
export default {
  props: {
    pic: String,
    name: String,
    type: String,
  },
};
</script>
!
<template>
  <div class="col">
    <img :src="pic" class="img-fluid mt-4" alt="" />
    <div class="info-card">
      <h3>{{ name }}</h3>
      <p>{{ type }}</p>
    </div>
  </div>
</template>

<style lang="scss">
.bg-white {
  background-color: white;
  padding: 10px 40px;
}

.info-card {
  background-color: #d48f38;
  height: 200px;
  padding-top: 30px;
}

h3 {
  text-align: center;
  color: white;
  padding-bottom: 20px;
}

p {
  text-align: center;
  font-size: 24px;
}
</style>

<template>
  <div class="wrap-blue">
    <h1>ν!</h1>
    <div class="boom-boom-emoji1">π₯</div>
    <div class="boom-boom-emoji2">π£</div>
    <h4> κ±Έλ¦°μ¬λ: {{ boomedSocket }} </h4>
    <img
      class="btn-img"
      @click="moveSelectGame"
      src="./../../../assets/back_btn.png"
      alt="back-btn"
    />
  </div>
</template>

<script>
export default {
  name: "BoomEndView",
  data() {
    return {
      boomedSocket: this.$route.params.boomedSocket,
    };
  },
  methods: {
    moveSelectGame() {
      this.$socket.emit("exitRoom")
      this.$router.push({
        name: "Home",
      });
    },
  },
};
</script>

<style scoped>
.boom-boom-emoji1 {
  text-align: center;
  width: 60%;
  margin: 0 auto;
  font-size: 100px;
}
.boom-boom-emoji2 {
  text-align: center;
  width: 60%;
  margin: 0 60% 40px 15%;
  font-size: 100px;
}
</style>

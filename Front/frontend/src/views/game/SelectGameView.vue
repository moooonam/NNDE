<template>
  <div class="wrap-blue">
    <h3>게임 목록</h3>
    <div>
      <div class="game-btn" @click="goBalanceGame">밸런스</div>
      <div class="game-btn" @click="goBoomGame">폭탄돌리기</div>
      <div class="game-btn" @click="goLiarGame">라이어</div>
    </div>
  </div>
</template>

<script>
import router from "@/router";
import { onMounted, ref } from "vue";
export default {
  setup() {
    const modal = ref(null);
    const body = ref(null);
    onMounted(() => {
      modal.value = document.querySelector(".modal");
      body.value = document.querySelector("body");
    });
    const goBoomGame = () => {
      router.push({ name: "MakeRoom", params: { modeName: "BoomSetup" } });
    };
    const goLiarGame = () => {
      router.push({
        name: "MakeRoom",
        params: { modeName: "LiarThemeList" },
      });
    };
    const goBalanceGame = () => {
      router.push({ name: "MakeRoom", params: { modeName: "Balance" } });
    };
    const toggleGameInfo = () => {
      modal.value.classList.toggle("show");
      if (modal.value.classList.contains("show")) {
        body.value.style.overflow = "hidden";
      } else {
        body.value.style.overflow = "auto";
      }
    };
    return {
      goBoomGame,
      toggleGameInfo,
      goLiarGame,
      goBalanceGame,
    };
  },
};
</script>

<style scoped>
.game-info {
  cursor: pointer;
  position: absolute;
  top: 10px;
  left: calc(100% - 60px);
  width: 50px;
  height: 50px;
  background-color: white;
  border-radius: 20%;
}
.game-btn {
  margin: 50px auto;
  font-size: 48px;
  text-align: center;
  width: 60%;
}
.modal {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: none;
  background-color: rgba(0, 0, 0, 0.4);
}
.show {
  display: block;
}
.modal-body {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 200px;
  height: 300px;
  padding: 40px;
  text-align: center;
  background-color: rgb(255, 255, 255);
  border-radius: 10px;
  box-shadow: 0 2px 3px 0 rgba(34, 36, 38, 0.15);
  transform: translateX(-50%) translateY(-50%);
}
</style>

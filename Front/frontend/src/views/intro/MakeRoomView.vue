<template>
  <div class="wrap-blue">
    <h2>인원수 설정</h2>
    <div class="wrap-count-num">
      <img src="../../assets/left_btn.png" @click="minusNum" />
      <p v-bind:limitMember="limitMember">{{ limitMember }}</p>
      <img src="../../assets/right_btn.png" @click="plusNum" />
    </div>
    <img
      src="../../assets/makeroom_btn.png"
      class="btn-img"
      @click="makeRoom"
    />
  </div>
</template>

<script>
import router from "@/router";
import { ref, getCurrentInstance } from "vue";
import { useRoute } from "vue-router";
export default {
  setup() {
    const app = getCurrentInstance();
    const $socket = app.appContext.config.globalProperties.$socket;
    const route = useRoute();
    const limitMember = ref(5);
    const modeName = ref(route.params.modeName);
    const minusNum = () => {
      if (limitMember.value > 1) {
        limitMember.value -= 1;
      }
    };
    const plusNum = () => {
      if (limitMember.value < 6) {
        limitMember.value += 1;
      }
    };
    const makeRoom = () => {
      $socket.emit("makeRoom", {
        limitMember: limitMember.value,
        modeName: modeName.value,
      });
      router.push({
        name: "RoomWaiting",
        params: { modeName: modeName.value },
      });
    };
    return {
      limitMember,
      minusNum,
      plusNum,
      makeRoom,
    };
  },
  methods: {},
};
</script>

<style></style>

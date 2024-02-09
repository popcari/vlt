<script setup>
  import { ref } from "vue";

  // Initialize position with default values
  const positionX = ref(null);
  const positionY = ref(null);
  const isAccepted = ref(false);

  const onOKBtnClick = () => {
    isAccepted.value = true;
  };

  const onMouseoverNO = () => {
    positionX.value = Math.floor(Math.random() * 80);
    positionY.value = Math.floor(Math.random() * 80);
  };
</script>

<template>
  <div class="container relative max-w-full h-screen flex flex-col p-5">
    <div class="h-4/5" :class="{ accepted: isAccepted }">
      <img
        :src="isAccepted ? '/public/vlt_card.png' : '/public/vlt_ask.png'"
        class="h-full w-auto mx-auto custom-transition"
      />

      <button
        class="bg-blue-400 hover:bg-blue-700 hover:scale-125 w-[80px] mt-10 text-white font-bold py-2 drop-shadow-lg px-4 rounded absolute left-[50%] mr-10 transition-color duration-300 translate-x-[-150%]"
        @click="onOKBtnClick"
        :style="{ display: isAccepted ? 'none' : 'block' }"
      >
        YES
      </button>
      <button
        @mouseover="onMouseoverNO"
        class="bg-red-400 w-[80px] hover:bg-red-700 text-white font-bold mt-10 py-2 px-4 rounded absolute right-[50%] ml-10 transition-color duration-500 translate-x-[150%]"
        :style="{
          top: `${positionY}%`,
          left: `${positionX}%`,
          display: isAccepted ? 'none' : 'block',
        }"
      >
        NO
      </button>
    </div>
  </div>
</template>

<style scoped>
  .accepted {
    height: 100%;
    transition: all 0.5s ease-in-out;
  }
</style>

<script setup>
// import { ref } from "vue";
const emit = defineEmits(["openNavContent"]);

const openNavContent = () => {
  emit("openNavContent");
};
</script>

<template>
  <button class="toggleSideBtn" @click="openNavContent">
    <div class="line line1"></div>
    <div class="line line2"></div>
    <div class="line line3"></div>
  </button>
</template>

<style lang="scss" scoped>
.toggleSideBtn {
  width: 40px;
  height: 30px;
  position: relative;
  background: #d6d6d6;
  border-radius: 5px;
}

.line {
  width: 15px;
  height: 1px;
  background: #000000;
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  z-index: 2;
}

.line1 {
  top: 10px;
}
.line2 {
  top: 15px;
}
.line3 {
  top: 20px;
}
</style>

<script setup>
// import { ref } from "vue";
// const emit = defineEmits(["onToggleClick"]);
</script>

<template>
  <div>
    <div class="mask"></div>

    <div class="content">123</div>
  </div>
</template>

<style lang="scss" scoped>
.mask {
  width: 100%;
  height: 100vh;
  position: fixed;
  top: 0;
  left: 0;
  background: rgba(0, 0, 0, 0.1);
  z-index: 9000;
}

.content {
  width: 180px;
  height: 100vh;
  background: rgba(0, 0, 0, 0.7);
  position: fixed;
  top: 0;
  right: 0;
  z-index: 9001;
  color: #ffffff;
  padding: 10px 5px;
}
</style>

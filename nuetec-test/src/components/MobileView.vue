<script setup>
import { ref } from "vue";

// ^ Components
import ToggleBtn from "./ToggleBtn.vue";
import NavContent from "./NavContent.vue";

const count = ref(0);

const onToggleClick = () => {
  console.log("onToggleClick");
};
</script>

<template>
  <div class="mobile-view">
    <section class="nav">
      <ToggleBtn @onToggleClick="onToggleClick" />

      <NavContent />
    </section>
  </div>
</template>

<style lang="scss" scoped>
.mobile-view {
  width: 390px;
  height: 844px;
  background: #d6d6d6;
  position: relative;
}

.nav {
  width: 100%;
  height: 40px;
  padding: 5px;
  background: #ffffff;
  display: flex;
  justify-content: flex-end;
}
</style>

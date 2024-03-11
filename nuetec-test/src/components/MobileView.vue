<script setup>
import { ref } from "vue";

// ^ Components
import ToggleBtn from "./ToggleBtn.vue";
import NavContent from "./NavContent.vue";

const count = ref(0);

const isShowNavContent = ref(true);

const openNavContent = () => {
  console.log("onToggleClick");
  isShowNavContent.value = true;
};

const closeNavContent = () => {
  console.log("closeNavContent");
  isShowNavContent.value = false;
};
</script>

<template>
  <div class="mobile-view">
    <section class="nav">
      <ToggleBtn @openNavContent="openNavContent" />

      <NavContent
        :isShow="isShowNavContent"
        @closeNavContent="closeNavContent"
      />
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

<script setup>
import { ref } from "vue";

// ^ Components
import ToggleBtn from "./ToggleBtn.vue";
import NavContent from "./NavContent.vue";

const blocksArr = ref([
  {
    key: "b1",
    isShimmer: false,
  },
  {
    key: "b2",
    isShimmer: false,
  },
  {
    key: "b3",
    isShimmer: true,
  },
  {
    key: "b4",
    isShimmer: false,
  },
  {
    key: "b5",
    isShimmer: true,
  },
  {
    key: "b6",
    isShimmer: false,
  },
  {
    key: "b7",
    isShimmer: false,
  },
  {
    key: "b8",
    isShimmer: false,
  },
  {
    key: "b9",
    isShimmer: true,
  },
]);

const isShowNavContent = ref(false);

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

    <div class="blocks-cotainer">
      <div class="blocks">
        <div
          class="block"
          v-for="item in blocksArr"
          :key="item.key"
          :class="{ shimmer: item.isShimmer }"
        ></div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@keyframes fadeInOut {
  0%,
  100% {
    opacity: 1;
  }

  50% {
    opacity: 0.6;
  }
}

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

.blocks-cotainer {
  width: 100%;
  height: calc(100vh - 40px);
  display: flex;
  flex-direction: column;
  justify-content: center;

  .blocks {
    width: 100%;
    height: 310px;
    background: #fff;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 5px;
    padding: 5px;
  }

  .block {
    height: 100px;
    border: black solid 2px;
    background: radial-gradient(
      circle,
      rgba(113, 81, 95, 1) 81%,
      rgba(0, 0, 0, 1) 100%
    );

    &.shimmer {
      animation: fadeInOut 0.5s infinite;
    }
  }
}
</style>

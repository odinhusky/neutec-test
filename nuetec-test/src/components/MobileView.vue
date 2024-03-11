<script setup>
import { ref } from "vue";

// ^ Components
import ToggleBtn from "./ToggleBtn.vue";
import NavContent from "./NavContent.vue";

const blocksArr = ref([
  {
    key: "b1",
    isShimmer: false,
    ball: "1",
  },
  {
    key: "b2",
    isShimmer: false,
  },
  {
    key: "b3",
    isShimmer: true,
    ball: "2",
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
    ball: "3",
  },
  {
    key: "b8",
    isShimmer: false,
  },
  {
    key: "b9",
    isShimmer: true,
    ball: "4",
  },
]);

const isShowNavContent = ref(false);

const openNavContent = () => {
  isShowNavContent.value = true;
};

const closeNavContent = () => {
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
        <div class="block" v-for="item in blocksArr" :key="item.key">
          <div class="block-inside" :class="{ shimmer: item.isShimmer }"></div>
          <div v-if="item.ball" class="ball" :class="[`ball${item.ball}`]">
            0
          </div>
        </div>
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

@keyframes moveRight {
  0% {
    transform: translate(-50%, -50%);
  }

  100% {
    transform: translate(900%, -50%);
  }
}

.mobile-view {
  width: 390px;
  height: 844px;
  background: #d6d6d6;
  position: relative;
  overflow: hidden;
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

    position: relative;

    .block-inside {
      width: 100%;
      height: 100%;
      background: radial-gradient(
        circle,
        rgba(113, 81, 95, 1) 81%,
        rgba(0, 0, 0, 1) 100%
      );
      position: relative;
      z-index: 3;

      &.shimmer {
        animation: fadeInOut 0.5s infinite;
      }
    }

    & .ball {
      width: 30px;
      height: 30px;
      background-color: #a5f12b;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 16px;
      border-radius: 50%;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      z-index: 4;

      animation: moveRight 2s infinite ease-in-out;
    }
  }
}
</style>

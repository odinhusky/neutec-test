<script setup>
import { ref, provide } from "vue";
import data from "../assets/data";

// ^ Components
import TreeMenu from "./TreeMenu.vue";

defineProps({
  isShow: Boolean,
});

const treeData = ref(data);
const selectedPath = ref([]);
provide("selectedPath", selectedPath);

const emit = defineEmits(["closeNavContent"]);

const closeNavContent = () => {
  emit("closeNavContent");
};

const selectThis = (text, depth) => {
  const length = selectedPath.value.length;

  if (length - depth === 0) {
    selectedPath.value.push(text);
  } else {
    selectedPath.value.splice(depth, length - depth, text);
  }
};
provide("selectThis", selectThis);
</script>

<template>
  <div>
    <div class="mask" @click.self="closeNavContent" v-if="isShow"></div>

    <transition name="content">
      <div class="content" v-if="isShow">
        <!-- path: {{ selectedPath.join(" / ") }} -->
        <TreeMenu
          v-for="item in treeData"
          :key="item.key"
          :children="item.children"
          :depth="0"
          :text="item.text"
        />
      </div>
    </transition>
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

.content-leave-active,
.content-enter-active {
  transition: all 0.9s ease;
}

.content-enter-from {
  right: -180px;
}

.content-enter-to {
  right: 0px;
}

.content-leave-from {
  right: 0px;
}

.content-leave-to {
  right: -180px;
}
</style>

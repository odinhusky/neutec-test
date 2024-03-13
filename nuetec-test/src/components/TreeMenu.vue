<script setup name="tree-menu">
import { inject, computed } from "vue";

const { text, depth } = defineProps({
  text: String,
  children: Array,
  depth: Number,
});

const selectedPath = inject("selectedPath");
const selectThis = inject("selectThis");

const selectedBg = computed(() => {
  if (depth === 0 && selectedPath.value.includes(text))
    return { backgroundColor: "gray" };
  else return {};
});

const selectedTextStyle = computed(() =>
  selectedPath.value.includes(text) ? { color: "yellow" } : {}
);
</script>

<template>
  <div class="tree-menu" :style="selectedBg">
    <div
      class="text"
      :style="selectedTextStyle"
      @click="selectThis(text, depth)"
    >
      {{ text }}
    </div>

    <template v-if="selectedPath.includes(text)">
      <tree-menu
        v-for="item in children"
        :children="item.children"
        :text="item.text"
        :depth="depth + 1"
        :key="item.key"
      />
    </template>
  </div>
</template>

<style lang="scss" scoped>
.tree-menu {
  width: 100%;
  padding: 10px 0 10px 16px;
}

.text {
  color: #ffffff;
  font-size: 16px;
}
</style>

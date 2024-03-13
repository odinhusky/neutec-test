<script setup>
import MobileView from "./components/MobileView.vue";

// 額外需求 - 文字描述 start

// # 主頁面九宮格動畫
// 1. 請使用兩種以上的動畫執行方式，來繪製動畫
// Ans: 除了使用 css 的動畫以外，也可以透過 Vue 提供的 <transition> 實踐，以及透過 Web Animation API 實踐。另外，也可以透過三方套件，例如 Velocity 或是 GSAP 等套件實踐。

// 2. 四顆球同時朝同一個座標點移動
// Ans: 同一個座標點如果是在九宮格的範圍內，可能球對齊的Dom對象就要修改成共同的父元素，抑或者是計算出對應的位置，設定相對應的 CSS 語法。

// # 側邊選單
// 1. 另提供一個下拉選單，需包含所有種類。從下拉選單中選取任一項目時，等同點擊該項目
// Ans: 這個功能透過類似 tree-menu 的 Component，使用 Recursive 的方式便可以動態的產生對應的下拉選單以及選項，之後再將每一個下拉選單選擇到的選項文字填入 <NavContent> 中的 ref: selectedPath，即可以同點擊該項目。

// 2. 請實作記憶功能，關閉分頁後再開啟，可以顯示上次選取的項目
// Ans: 透過 localStorage 記憶選擇的 selectedPath ，等再次進入後先確認是否有暫存資料，有的話就在初始化的階段填入，即可達成記憶的需求。

// 3. 請在效能考量下，設計可收合、展開最多一百層的選單
// Ans: 在實作上需要調整的主要是虛擬滾動的部分，透過限制特定區域的顯示部分的列表內容，提升效能。可以透過第三方的套件實現，例如 vue-virtual-scroller。

// 額外需求 - 文字描述 end
</script>

<template>
  <div class="body">
    <MobileView />
  </div>
</template>

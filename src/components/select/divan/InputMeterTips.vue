<script setup>
// import { ref } from 'vue'
import { useCarcStore } from '@/stores/dataForCalculation'
const carcStore = useCarcStore()
const props = defineProps(['parentValue'])
const emit = defineEmits(['update:modelValue'])

const pick = function (data) {
  emit('update:modelValue', data)
}
</script>

<script></script>

<template>
  <!-- <ul>  {{ carcStore.sortTips() }}</ul> -->
  <ul>
    <li
      v-on:mousedown="pick(item[0])"
      class="item"
      :key="item[2]"
      v-for="item in carcStore.sortTips()"
    >
      <span :class="[props.parentValue == item[0] ? 'picked' : '']">{{ item[0] }}</span>
    </li>
  </ul>
</template>

<style scoped>
ul::-webkit-scrollbar {
  width: 4px;
  height: 4px;
}
@media (hover: none) and (pointer: coarse) {
  ul::-webkit-scrollbar {
    width: 2px;
    height: 2px;
  }
}
ul::-webkit-scrollbar-track {
  border-radius: 10px;
  background: rgba(0, 0, 0, 0.042);
}
ul::-webkit-scrollbar-thumb {
  border-radius: 10px;
  background: rgba(0, 0, 0, 0.2);
}
ul::-webkit-scrollbar-thumb:hover {
  background: rgba(0, 0, 0, 0.4);
}
ul::-webkit-scrollbar-thumb:active {
  background: rgba(0, 0, 0, 0.9);
}
ul {
  scrollbar-width: thin; /* "auto" or "thin" */
  scrollbar-color: blue orange; /* scroll thumb and track */
  scrollbar-color: red orange;
  /* overflow: overlay;  */
  overflow: auto;
  /* Скрываем вертикальный scrollbar */
  overflow-y: hidden;
  /* overflow: hidden; */
  background: rgb(255, 255, 255);
  /* position: fixed; */
  /* position: absolute; */
  bottom: 0;
  left: 0;
  z-index: 9;
  width: 100%;
  height: 55px;
  font-size: 20px;
  padding: 0px;
  display: flex;
  margin: 13px 0;
  
  width:calc(100% - 6px);
  margin-left: 3px;
  border-radius: 5px;
  /* margin-right: 23px; */
  margin-top:3px;
  margin-bottom: 3px;


}

.item {
  display: flex;
  align-items: center;
  user-select: none;
  /* height: 100%; */
  /* margin: 3px; */

  list-style-type: none;
}
.item:nth-last-child(1) {
  margin-right: 70px;
}
.item > span {
  text-align: center;
  color: white;
  background: rgb(64, 64, 64);
  margin: 0px 2px;
  padding: 2px 10px;
  border-radius: 30px;
  cursor: pointer;
  min-width: 37px;
  display: block;
  align-content: center;
}

.item .picked {
  background: tomato;
}
</style>

<script setup>
import { ref, reactive } from 'vue';

defineProps({});

const list = ref([]);
const obj = reactive({});
const addToList = () => {
  if (list.value.length < 5) {
    list.value.push(Math.random().toString(36).slice(-6));
  }
};
</script>

<template>
  <button @click="addToList">添加</button>
  <button @click="list.pop()">删除</button>
  <p v-for="item in list">
    {{ item }}
  </p>
</template>

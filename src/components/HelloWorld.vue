<script setup>
import { ref, reactive, toRef } from 'vue';

defineProps({});
const emit = defineEmits(['click-emit']);
const list = ref([]);

const obj = reactive({});
let num = 0;
const addProp = () => {
  switch (num) {
    case 0:
      obj['name'] = 'weizhuofei';
      break;
    case 1:
      obj['age'] = 18;
      break;
    case 2:
      obj['home'] = 'shenyang';
      break;
    case 3:
      obj['job'] = 'android';
      break;
  }
  if (num < 4) {
    num++;
  }
};
const testString = { str1: 'origin' };
const toRefTest = toRef(testString, 'str1');
const deleteProp = () => {
  switch (num) {
    case 1:
      delete obj['name'];
      break;
    case 2:
      delete obj['age'];
      break;
    case 3:
      delete obj['home'];
      break;
    case 4:
      delete obj['job'];
      break;
  }
  if (num > 0) {
    num--;
  }
  console.log(obj);
};
const refTest = ref('origin');
const changeToRef = () => {
  toRefTest.value = 'modified';
};
const changeRef = () => {
  refTest.value = 'modified';
};
const addToList = () => {
  if (list.value.length < 5) {
    list.value.push(Math.random().toString(36).slice(-6));
  }
};
const emitEvent = (num) => {
  emit('click-emit', num);
};
</script>

<template>
  <button @click="addToList">添加</button>
  <button @click="list.pop()">删除</button>
  <button @click="list[0] = 'modified'">更改</button>
  <p v-for="item in list">
    {{ item }}
  </p>
  <br />
  <button @click="addProp">添加属性</button>
  <button @click="deleteProp">删除属性</button>
  <p v-for="key in Object.keys(obj)">{{ key }}:{{ obj[key] }}</p>
  <br />
  <button @click="changeToRef">更改toref</button>
  <button @click="changeRef">更改ref</button>
  <p>{{ toRefTest }} || {{ refTest }}</p>
  <br />
  <button @click="emitEvent(1)">emit1</button>
  <button @click="emitEvent(2)">emit2</button>
</template>

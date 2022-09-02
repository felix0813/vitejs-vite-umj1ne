<template>
  <div>
    <p>{{ counter }}</p>
    <button @click="onClick">点击+1</button>
  </div>
</template>
<script lang="ts">
import { defineComponent, ref, computed, reactive, onMounted } from 'vue';

export default defineComponent({
  name: 'Counter',
  setup() {
    const counter = ref(0);
    const onClick = () => {
      counter.value++;
    };
    return { counter, onClick };
  },
});
</script>

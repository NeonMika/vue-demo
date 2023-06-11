<script setup lang="ts">
import { ref } from 'vue';

  const rects = ref([{x: 10, y: 10, width: 10, height: 10}])

  function removeFirst() : void {
    rects.value = rects.value.slice(1)
  }
</script>

<template>
  <button @click="rects.push({x: Math.random() * 400, y: Math.random() * 400, width: Math.random() * 50, height: Math.random() * 50})">
  Add random rectangle
  </button>

  <button @click="removeFirst">
    Remove first
  </button>
  <br>
  <svg width="400" height="400">
    <rect width="100%" height="100%" style="fill: lightgray"></rect>
    <rect v-for="r in rects" :x="r.x" :y="r.y" :width="r.width" :height="r.height" style="fill: white; stroke: black; fill-opacity: 0;"/>
    <text v-for="r in rects" :x="r.x" :y="r.y"> {{ r.x.toFixed(2) }} / {{ r.y.toFixed(2) }} </text>
  </svg>
  <pre>
  {{ rects }}
  </pre>
</template>
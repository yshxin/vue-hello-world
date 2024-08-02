<template>
  <div class="main" @click="clickChange">
    <Child ref="childRef" @ok="childOk"></Child>
  </div>
</template>

<script setup lang="ts">
import Child from "@/components/test/Child.vue";
import {ref} from "vue";

const childRef = ref()

function clickChange() {
  childRef.value.parentCall('add')
}

function childOk() {
  console.log(childRef.value.childCount)
}

</script>

<style scoped>
.main {
  width: 50px;
  height: 50px;
  background: red;
  text-align: center;
  line-height: 50px;
}
</style>
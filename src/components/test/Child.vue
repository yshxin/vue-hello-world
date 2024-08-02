<template>
  <div ref="childRef">{{ childCount }}</div>
</template>

<script lang="ts" setup>
import {ref} from "vue";

const childCount = ref(0)
const childRef = ref()

function parentCall(opt: string) {
  if (opt === 'add') {
    childCount.value++
    emit('ok')
  } else if (opt === 'sub') {
    childCount.value--
  }
}

// 对外暴露方法
defineExpose({
  parentCall,
  childCount
})

const emit = defineEmits([
    'ok'
])
</script>


<style scoped>

</style>
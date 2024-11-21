<script setup>
import { useData } from 'vitepress';
import { ref, watch, onMounted } from 'vue';

onMounted(() => {
  import('rapidoc')
})

const data = useData();
const theme = ref(data.isDark.value ? 'dark' : 'light')

watch(data.isDark, (isDark) => {
  theme.value = isDark ? 'dark' : 'light';
})
</script>

<template>
<div>
  <rapi-doc
      spec-url = "https://petstore.swagger.io/v2/swagger.json"
      render-style = "read"
      :theme="theme"
      style = "height:100vh; width:100%"
  > </rapi-doc>
</div>
</template>

<style scoped>

</style>

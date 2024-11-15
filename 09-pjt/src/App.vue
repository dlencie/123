<template>
  <div id="app">
    <AppNav />
    <div class="page">
      <router-view />
    </div>
  </div>
</template>


<script setup>
import AppNav from '@/components/Common/AppNav.vue'
</script>


<style scoped>
#app {
  font-family: "Noto Sans KR", sans-serif;
}

ul {
  padding-left: 0;
  list-style: none;
}

.page {
  padding-top: 3.5rem;
}
</style>

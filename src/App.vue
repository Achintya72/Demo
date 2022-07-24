<script setup>
import HeaderBar from './components/HeaderBar.vue';
import OpenOrder from './components/OpenOrder.vue';
import CustomerSearch from "./components/CustomerSearch.vue"
</script>

<template>
  <HeaderBar v-model="searchType" />
  <OpenOrder v-if="searchType == 'Open Order'" />
  <CustomerSearch v-else />
</template>
<script>
export default {
  data() {
    return {
      searchType: "Purchase",
    }
  }
}
</script>
<style >
#app {
  font-family: 'Open-Sans', sans-serif;
  margin: 0;
  padding: 0;
  height: 100%;
}

html,
body {
  height: 100%;
  min-height: 100%;
}
</style>

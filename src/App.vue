<template>
  <div id="app">
    <Gifts/>
  </div>
</template>

<script>
  // Pages
  import Gifts from "./components/Gifts.vue";
  // App component
  export default {
    name: 'App',
    components: {
      Gifts
    }
  }
</script>
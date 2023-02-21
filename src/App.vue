<template>
  <TheHeader />
</template>

<script>
  import TheHeader from './layout/TheHeader.vue';

  export default {
    components: {
      TheHeader
    },
    data() {
      return {
      };
    },
  };
</script>

<style>
  html {
    font-family: sans-serif;
  }

  body {
    margin: 0;
    min-height: 100vh;
  }
</style>
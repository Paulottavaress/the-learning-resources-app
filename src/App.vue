<template>
  <TheHeader />
  <main>
    <TheResources />
  </main>
</template>

<script>
  import TheHeader from './components/layout/TheHeader.vue';
  import TheResources from './components/learning-resources/TheResources.vue';

  export default {
    components: {
      TheHeader,
      TheResources
    }
  };
</script>

<style>
  * {
    box-sizing: border-box;
  }

  html {
    font-family: sans-serif;
  }

  body {
    margin: 0;
    min-height: 100vh;
  }
</style>

<style scoped>
  main {
    max-width: 1440px;
    margin: 40px 80px;
    display: flex;
    flex-direction: column;
    gap: 40px;
  }
</style>
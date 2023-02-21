<template>
  <header>
    <slot>
      <h1>RememberMe</h1>
    </slot>
  </header>
</template>

<script>
  export default {};
</script>

<style scoped>
  header {
    background-color: rgba(96, 10, 43, 1);
    height: 10vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  h1 {
    color: rgba(255, 255, 255, 1);
  }
</style>
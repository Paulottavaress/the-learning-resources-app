<template>
  <div>
    <slot></slot>
  </div>
</template>

<script>
  export default {};
</script>

<style scoped>
  div {
    border-radius: 12px;
    border: 1px solid rgba(0, 0, 0, 1);
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    padding: 20px;
  }
</style>
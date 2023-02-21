<template>
  <dialog open>
    <slot></slot>
  </dialog>
</template>

<script>
  export default {};
</script>

<style scoped>
  dialog {
    position: fixed;
    z-index: 1000;
    left: 50%;
    transform: translateX(50%);
    background: white;
  }
</style>
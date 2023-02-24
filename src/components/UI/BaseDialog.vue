<template>
  <teleport to="body">
    <div
      v-if="isDialogOpen"
      class="overlay"
      @click="this.$emit('close-dialog')"
    ></div>
    <dialog :open="isDialogOpen">
      <header>
        <slot name="header"></slot>
      </header>
      <div>
        <slot></slot>
        <BaseButton
          @click="this.$emit('close-dialog')"
          :isAlwaysActive="true"
          class="confirm-btn"
        >Okay</BaseButton>
      </div>
    </dialog>
  </teleport>
</template>

<script>
  import BaseButton from './BaseButton.vue';

  export default {
    components: {
      BaseButton
    },
    emits: ['close-dialog'],
    props: {
      isDialogOpen: {
        type: Boolean,
        required: true
      }
    }
  };
</script>

<style scoped>
  dialog {
    position: fixed;
    z-index: 1000;
    left: 50%;
    transform: translateX(-50%);
    background: white;
    border: 0px;
    border-radius: 15px;
    padding: 0px;
  }

  header {
    border-radius: 15px 15px 0 0;
    background-color: rgba(53, 11, 80, 1);
    width: 100%;
    padding: 15px;
    color: rgba(255, 255, 255, 1);
  }

  div {
    padding: 15px;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: flex-end;
  }

  .confirm-btn {
    min-width: 86px;
  }

  .overlay {
    position: absolute;
    left: 0;
    top: 0;
    z-index: 100;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.75);
  }
</style>
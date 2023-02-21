<template>
  <button :type='btnType' ref="baseButton">
    <slot></slot>
  </button>
</template>

<script>
  export default {
    methods: {
      triggerActive() {
        const btn = this.$refs.baseButton;

        (this.btnName === this.selectedComponent)
        ? btn.classList.add('active')
        : btn.classList.remove('active');
      }
    },
    mounted() {
      this.triggerActive();

      if (this.isAlwaysActive) this.$refs.baseButton.classList.add('active');
    },
    props: {
      btnName: {
        type: String,
        required: true
      },
      selectedComponent: {
        type: String,
        required: false,
        default: ''
      },
      isAlwaysActive: {
        type: Boolean,
        required: false,
        default: false
      },
      btnType: {
        type: String,
        required: false,
        default: 'button'
      }
    },
    watch: {
      selectedComponent() {
        this.triggerActive();
      }
    }
  };
</script>

<style scoped>
  button {
    height: 50px;
    width: 150px;
    cursor: pointer;
    color: rgba(53, 11, 80, 1);
    border: none;
    background-color: rgba(255, 255, 255, 1);
    white-space: nowrap;
    padding: 20px;
    font-weight: bold;
  }

  button:hover {
    background-color: rgba(235, 210, 255, 1);
    color: rgba(53, 11, 80, 1);
  }

  .active {
    background-color: rgba(53, 11, 80, 1);
    color: rgb(255, 255, 255, 1)
  }
</style>
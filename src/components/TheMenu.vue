<template>
  <BaseCard>
    <BaseButton
      btn-name='stored-resources'
      @click="activeComponent('stored-resources')"
      :selectedComponent="selectedComponent"
    >Stored Resources</BaseButton>
    <BaseButton
      btn-name='add-resource'
      @click="activeComponent('add-resource')"
      :selectedComponent="selectedComponent"
    >Add Resource</BaseButton>
  </BaseCard>
</template>

<script>
  import BaseButton from './UI/BaseButton.vue';
  import BaseCard from './UI/BaseCard.vue';

  export default { 
    components: { 
      BaseCard,
      BaseButton
    },
    emits: ['active-component'],
    methods: {
      activeComponent(cmp) {
        this.$emit('active-component', cmp);
      }
    },
    props: {
      selectedComponent: {
        type: String,
        required: true
      }
    }
  };
</script>

<style scoped>

</style>
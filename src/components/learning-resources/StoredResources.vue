<template>
  <BaseCard v-for="resource in resources" :key="resource.id">
    <header>
      <h2>{{ resource.title }}</h2>
      <button @click="deleteResource(resource.id)">Delete</button>
    </header>
    <h3>{{resource.description }}</h3>
    <a :href="resource.url"><h3>View Resource</h3></a>
  </BaseCard>
</template>

<script>
  import BaseCard from '../UI/BaseCard.vue';

  export default {
    components: {
      BaseCard
    },
    inject: {
      resources: {
        type: Object,
        required: true
      },
      deleteResource: {
        type: Function,
        required: true
      }
    }
  };
</script>

<style scoped>
  header {
    display: flex;
    align-items: center;
  }
  
  header h2 {
    flex-grow: 1;
  }

  header button {
    color: rgba(37, 7, 57, 1);
    padding: 0 20px;
    background-color: rgba(255, 255, 255, 1);
    border: none;
    font-weight: bold;
    cursor: pointer;
    font-size: 1.17em;
  }

  header button:hover {
    color: rgba(235, 210, 255, 1);
  }

  a {
    color: rgba(196, 127, 82, 1);
    text-decoration: none;
    font-weight: bold;
  }

  a:hover {
    color: rgba(196, 127, 82, 0.5);
  }
</style>
<template>
    <ResourcesMenu
      @active-component="toggleComponent"
      :selectedComponent="selectedComponent"
    ></ResourcesMenu>
    <KeepAlive>
      <component :is="selectedComponent" />
    </KeepAlive>
</template>

<script>
  import { computed } from '@vue/reactivity';
  import AddResource from './AddResource.vue';
  import ResourcesMenu from './ResourcesMenu.vue';
  import StoredResources from './StoredResources.vue';

  export default {
    components: {
      AddResource,
      ResourcesMenu,
      StoredResources
    },
    data() {
      return {
        resources: [
          {
            id: 0,
            title: 'Official Guide',
            description: 'The official Vue.js documentation',
            url: 'https://vuejs.org/guide/introduction.html'
          },
          {
            id: 1,
            title: 'Google',
            description: 'Learn to google...',
            url: 'http://google.com/'
          }
        ],
        selectedComponent: 'stored-resources'
      };
    },
    methods: {
      addResource(enteredData) {
        this.resources.unshift({
          id: this.resources.length + 1,
          ...enteredData
        })
      },
      deleteResource(id) {
        this.resources = this.resources.filter(resource => resource.id !== id);
      },
      toggleComponent(cmp) {
        this.selectedComponent = cmp;
      }
    },
    provide() {
      return {
        resources: computed(() => this.resources),
        deleteResource: this.deleteResource,
        addResource: this.addResource,
        toggleComponent: this.toggleComponent
      }
    }
  };
</script>

<style scoped>

</style>
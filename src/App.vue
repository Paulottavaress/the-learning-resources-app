<template>
  <TheHeader />
  <main>
    <TheMenu
      @active-component="toggleComponent"
      :selectedComponent="selectedComponent"
    ></TheMenu>
    <KeepAlive>
      <component
        :is="selectedComponent"
        :resources="resources"
        @delete-resource="deleteResource"
        @add-resource="addResource"
        @active-component="toggleComponent"
      />
    </KeepAlive>
  </main>
</template>

<script>
  import AddResource from './components/AddResource.vue';
  import StoredResources from './components/StoredResources.vue';
  import TheHeader from './components/layout/TheHeader.vue';
  import TheMenu from './components/TheMenu.vue';

  export default {
    components: {
      AddResource,
      StoredResources,
      TheHeader,
      TheMenu
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

  main {
    max-width: 1440px;
    margin: 40px 80px;
    display: flex;
    flex-direction: column;
    gap: 40px;
  }
</style>
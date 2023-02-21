<template>
  <BaseCard>
      <form @submit.prevent="addResource">
        <div>
          <label>Title</label>
          <input ref="titleField">
        </div>
        <div>
          <label>Description</label>
          <textarea ref="descriptionField"></textarea>
        </div>
        <div>
          <label>Link</label>
          <input ref="urlField">
        </div>
        <BaseButton :isAlwaysActive="true" :btnType="'submit'">Add Resource</BaseButton>
      </form>
  </BaseCard>
</template>

<script>
  import BaseButton from './UI/BaseButton.vue';
  import BaseCard from './UI/BaseCard.vue';
  import BaseDialog from './UI/BaseDialog.vue';

  export default {
    components: {
      BaseButton,
      BaseCard,
      BaseDialog
    },
    emits: ['add-resource'],
    methods: {
      addResource() {
        const enteredTitle = this.$refs.titleField.value;
        const enteredDescription= this.$refs.descriptionField.value;
        const enteredUrl = this.$refs.urlField.value;

        this.$emit('add-resource', {
          title: enteredTitle,
          description: enteredDescription,
          url: enteredUrl
        });
      }
    }
  };
</script>

<style scoped>
  form {
    display: flex;
    flex-direction: column;
    gap: 15px;
  }

  form div {
    display: flex;
    flex-direction: column;
    gap: 5px;
  }

  form label {
    font-weight: bold;
  }

  form input {
    height: 25px;
  }

  form textarea {
    resize: none;
    height: 75px;
  }
</style>
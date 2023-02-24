<template>
  <BaseCard>
      <form @submit.prevent="submitForm">
        <div>
          <label for="title-field">Title</label>
          <input id="title-field" name="title-field" ref="titleField">
        </div>
        <div>
          <label for="description-field">Description</label>
          <textarea id="description-field" name="description-field" ref="descriptionField"></textarea>
        </div>
        <div>
          <label for="url-field">Link</label>
          <input id="url-field" name="url-field" ref="urlField">
        </div>
        <BaseButton :isAlwaysActive="true" type="submit">Add Resource</BaseButton>
      </form>
  </BaseCard>
  <BaseDialog :isDialogOpen="isDialogOpen" @close-dialog="closeDialog">
    <template #header>
      <h2>Invalid Input</h2>
    </template>
    <template #default>
      <p>Unfortunately, at least one input values is invalid.</p>
      <p>Please check all inputs and make sure you enter at least a few characters into each input field.</p>
    </template>
  </BaseDialog>
</template>

<script>
  import BaseButton from '../UI/BaseButton.vue';
  import BaseCard from '../UI/BaseCard.vue';
  import BaseDialog from '../UI/BaseDialog.vue';

  export default {
    components: {
      BaseButton,
      BaseCard,
      BaseDialog
    },
    data() {
      return {
        isDialogOpen: false
      }
    },
    inject: {
      addResource: {
        type: Object,
        required: true
      },
      toggleComponent: {
        type: Function,
        required: true
      }
    },
    methods: {
      submitForm() {
        const enteredTitle = this.$refs.titleField.value;
        const enteredDescription= this.$refs.descriptionField.value;
        const enteredUrl = this.$refs.urlField.value;

        if (
          enteredTitle.trim() === '' || 
          enteredDescription === '' || 
          enteredUrl === ''
        ) {
          this.isDialogOpen = true;
          return;
        }

        this.addResource({
          title: enteredTitle,
          description: enteredDescription,
          url: enteredUrl
        });

        this.toggleComponent('stored-resources');
      },
      closeDialog() {
        this.isDialogOpen = false;
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

  h2 {
    margin: 0px;
  }

  p {
    width: 100%;
  }
</style>
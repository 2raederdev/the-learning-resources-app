<template>
  <BaseDialog v-if="inputIsInvalid" title="Invalid Input" @close="confirmError">
    <template #default>
      <p>Unfortunately, at least one input value is invalid.</p>
      <p>Please, make sure you enter at least a few characters in each input.</p>
    </template>
    <template #actions>
      <BaseButton @click="confirmError">OK</BaseButton>
    </template>
  </BaseDialog>
  <BaseCard>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input id="title" name="title" type="text" v-model="title">
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea id="description" name="description" rows="3" v-model="description"></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input id="link" name="link" type="url" v-model="link">
      </div>
      <div>
        <BaseButton type="submit">Add Resource</BaseButton>
      </div>
    </form>
  </BaseCard>
</template>

<script>
export default {
  data () {
    return {
      title: '',
      description: '',
      link: '',
      inputIsInvalid: false
    }
  },
  inject: ['addResource'],
  methods: {
    validateForm () {
      return !this.title.trim().length || !this.title.trim().length || !this.title.trim().length
    },
    submitData () {
      if (this.validateForm()) {
        this.inputIsInvalid = true
        return
      }
      const data = {
        title: this.title,
        description: this.description,
        link: this.link,
      }
      this.addResource(data)
    },
    confirmError () {
      this.inputIsInvalid = false
    }
  }
}
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
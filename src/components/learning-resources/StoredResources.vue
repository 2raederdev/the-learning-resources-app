<template>
  <ul>
    <LearningResource
      v-for="resource in resources"
      :key="resource.id" 
      :resource="resource"/>
  </ul>
</template>

<script>
import LearningResource from './LearningResource'

export default {
  components: {
    LearningResource
  },
  inject: ['resources']
}
</script>

<style scoped>

ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
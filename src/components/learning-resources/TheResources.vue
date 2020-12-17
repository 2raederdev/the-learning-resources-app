<template>
  <BaseCard>
    <BaseButton
      @click="setSelectedTab('StoredResources')"
      :mode="storedResButtonMode">
      Stored Resources
    </BaseButton>
    <BaseButton
      @click="setSelectedTab('AddResource')"
      :mode="addResButtonMode">
      Add Resource
    </BaseButton>
  </BaseCard>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import StoredResources from './StoredResources'
import AddResource from './AddResource'

export default {
  components: { 
    StoredResources,
    AddResource
  },
  computed: {
    storedResButtonMode () {
      return this.selectedTab === 'StoredResources' ? null : 'flat'
    },
    addResButtonMode () {
      return this.selectedTab === 'AddResource' ? null : 'flat'
    }
  },
  data () {
    return {
      selectedTab: 'StoredResources',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The official Vue.js documentation',
          link : 'https://vuejs.org'
        },
        {
          id: 'goole',
          title: 'Google',
          description: 'Learn tu google',
          link : 'https://www.google.com'
        }
      ]
    }
  },
  provide () {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
      deleteResource: this.deleteResource
    }
  },
  methods: {
    setSelectedTab (tab) {
      this.selectedTab = tab
    },
    addResource (data) {
      const { title, description, link} = data
      const newResource = {
        id: new Date().toISOString(),
        title,
        description,
        link
      }
      this.storedResources.unshift(newResource)
      this.selectedTab = 'StoredResources'
    },
    deleteResource (id) {
      const index = this.storedResources.findIndex(res => res.id === id)
      this.storedResources.splice(index, 1)
    }
  }
}
</script>

<style>

</style>
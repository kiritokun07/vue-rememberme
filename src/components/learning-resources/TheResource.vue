<template>
  <base-card>
    <base-button @click="setSelectedTab('stored-resource')"
                 :mode="storedResButtonMode">Stored Resources
    </base-button>
    <base-button @click="setSelectedTab('add-resource')"
                 :mode="addResButtonMode">Add Resource
    </base-button>
  </base-card>
  <component :is="selectedTab"></component>
</template>

<script>
import StoredResource from "./StoredResource.vue";
import AddResource from "./AddResource.vue";

export default {
  components: {
    StoredResource,
    AddResource
  },
  data() {
    return {
      selectedTab: 'stored-resource',
      storedResources: [
        {
          id: 'baidu',
          title: 'Baidu',
          description: '百度',
          link: 'https://www.baidu.com'
        },
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The official Vue.js ducumentation.',
          link: 'https://vuejs.org'
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to google',
          link: 'https://google.com'
        }
      ]
    };
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
    };
  },
  computed: {
    storedResButtonMode() {
      return this.selectedTab === 'stored-resource' ? null : 'flat';
    },
    addResButtonMode() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    }
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, description, url) {
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: url,
      };
      //在数组的开头加入
      this.storedResources.unshift(newResource);
      this.selectedTab = 'stored-resource';
    },
  }
}
</script>

<style scoped>

</style>
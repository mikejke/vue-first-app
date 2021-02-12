<template>
  <base-card>
    <base-button @click="changeTab('stored-resources')" :mode="storedResBtnMode"
      >Ресурсы</base-button
    >
    <base-button @click="changeTab('add-resource')" :mode="addResBtnMode"
      >Добавить</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import StoredResources from "./StoredResouces";
import AddResource from "./AddResource";

export default {
  components: {
    StoredResources,
    AddResource,
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
      removeResource: this.removeResource,
    };
  },
  data() {
    return {
      storedResources: [
        {
          id: "official-guide",
          title: "Официальная документация",
          desc: "Официальная документация Vue.JS.",
          link: "https://vuejs.org",
        },
        {
          id: "google",
          title: "Google",
          desc: "Научись искать...",
          link: "https://google.com",
        },
      ],
      selectedTab: "stored-resources",
    };
  },
  methods: {
    changeTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, desc, url) {
      const newResource = {
        id: new Date().toISOString(),
        title,
        desc,
        link: url,
      };

      this.storedResources.unshift(newResource);
      this.selectedTab = "stored-resources";
    },
    removeResource(resourceID) {
      const resIndex = this.storedResources.findIndex(
        (res) => res.id === resourceID
      );

      this.storedResources.splice(resIndex, 1);
    },
  },
  computed: {
    addResBtnMode() {
      return this.selectedTab === "add-resource" ? null : "flat";
    },
    storedResBtnMode() {
      return this.selectedTab === "stored-resources" ? null : "flat";
    },
  },
};
</script>

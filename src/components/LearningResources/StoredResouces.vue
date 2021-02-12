<template>
  <ul>
    <learning-resource
      v-for="res in resources"
      :key="res.id"
      :id="res.id"
      :title="res.title"
      :description="res.desc"
      :link="res.link"
    />
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
        padding: 0;
    }
</style>
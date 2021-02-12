<template>
  <li>
    <base-card>
      <header>
        <h3>{{ title }}</h3>
        <base-button type="button" @click="removeResource(id)" >Убрать</base-button>
      </header>
      <p>{{ description }}</p>
      <nav>
        <a target="_blank" :href="link">Перейти..</a>
      </nav>
    </base-card>
  </li>
</template>

<script>
export default {
  inject: ['removeResource'],
  props: ['id', 'title', 'description', 'link']
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

a {
  text-decoration: none;
  color: rgb(192, 80, 19);
}
a:hover {
  text-decoration: 1px dashed rgb(192, 80, 19);
}
</style>

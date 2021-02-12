<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<script>
export default {
  props: ['title']
}
</script>

<style scoped>
header {
  width: 100%;
  height: 5rem;
  background: linear-gradient(rgb(80, 15, 150), rgba(110, 25, 150));
  display: flex;
  justify-content: center;
  align-items: center;
}
header h1 {
  color: white;
  margin: 0;
}
</style>
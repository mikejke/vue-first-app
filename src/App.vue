<template>
  <the-header title="Запомни" />
  <the-resources></the-resources>
</template>

<script>
// Layout
import TheHeader from "./components/Layout/TheHeader";
// the resources
import TheResources from "./components/LearningResources/TheResources"

export default {
  components: {
    TheHeader,
    TheResources,
  }
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
}
* {
  font-family: Arial, Helvetica, sans-serif;
}
</style>

<template>
  <button :class="mode">
    <slot>Button</slot>
  </button>
</template>

<script>
export default {
  props: ["mode"],
};
</script>

<style scoped>
button {
  font-weight: 700;
  cursor: pointer;
  padding: 0.5rem 1rem;
  color: white;
  background: rgb(110, 25, 150);
  border: none;
  box-shadow: none;
  outline: none;
}

button:hover {
  background: rgb(80, 15, 150);
}

.flat {
  background: transparent;
  color: rgb(110, 25, 150);
}

.flat:hover {
  color: rgb(80, 15, 150);
  background: rgb(196, 196, 196);
}
</style>

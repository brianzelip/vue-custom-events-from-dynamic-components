<template>
  <section id="B">
    <h1>Component B</h1>
    <p>Color prop sent from parent: "{{ color }}"</p>
    <button @click="click">Click me to swap components from within the dynamic component</button>
  </section>
</template>

<script>
export default {
  props: ["color"],
  methods: {
    click() {
      this.$emit("swap-components");
    }
  }
};
</script>

<style scoped>
#B {
  padding: 1rem;
  background: turquoise;
}
</style>

<template>
  <section id="A">
    <h1>Component A</h1>
    <p>Data prop sent from parent: "{{ data }}"</p>
    <button @click="click">I'm from the dynamic component - click me to swap components</button>
  </section>
</template>

<script>
export default {
  props: ["data"],
  methods: {
    click() {
      this.$emit("swap-components");
    }
  }
};
</script>

<style scoped>
#A {
  padding: 1rem;
  background: tomato;
}
</style>

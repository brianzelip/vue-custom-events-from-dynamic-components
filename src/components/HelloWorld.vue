<template>
  <div>
    <h1>The dynamic components ⤵️</h1>
    <component
      :is="current"
      v-bind="dynamicProps"
    ></component>
    <button
      @click="click"
    >I'm from the parent of the dynamic component - click me to swap components</button>
  </div>
</template>

<script>
import A from "./A.vue";
import B from "./B.vue";

export default {
  data() {
    return {
      current: "A"
    };
  },
  computed: {
    dynamicProps() {
      return this.current === "A" ? { data: 11 } : { color: "black" };
    }
  },
  methods: {
    click() {
      this.$emit("swap-components");
    },
    swapComponents() {
      this.current = this.current === "A" ? "B" : "A";
    }
  },
  mounted() {
    this.$nextTick(function() {
      // Code that will run only after the
      // entire view has been rendered
      this.$on("swap-components", this.swapComponents);
    });
  },
  components: {
    A,
    B
  },
  props: {
    msg: String
  }
};
</script>

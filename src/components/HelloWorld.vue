<template>
  <div>
    <h1>The dynamic components ⤵️</h1>
    <component
      :is="current"
      v-bind="dynamicProps"
      v-on:swap-components="swapComponents"
    ></component>
    <button
      @click="click"
    >Click me to swap components from within the parent of the dynamic component</button>
  </div>
</template>

<script>
import A from "./A.vue";
import B from "./B.vue";

export default {
  data() {
    return {
      current: "A",
      passedData: ""
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
    swapComponents(str) {
      this.current = this.current === "A" ? "B" : "A";
      this.passedData = str;
    }
  },
  mounted() {
    this.$nextTick(() => {
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

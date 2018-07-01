<template>
    <parameters />
</template>

<script>
import Parameters from "@/components/Parameters.vue";

export default {
  name: "layout",
  data() {
    return {
      xmlString: ""
    };
  },
  components: {
    Parameters
  },
  methods: {
    onParametersString: function(input) {
      this.xmlString = input;
    }
  }
};
</script>

<style scoped>
</style>

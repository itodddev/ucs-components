<template>
  <div class="home">
    
    <RackItem />
    <RackItem />
    <RackItem />
    <RackItem />
    <RackItem />
    <RackItem />
    <RackItem />
    <RackItem />
    
    <Parameters />

  </div>
</template>

<script>
// @ is an alias to /src
import Parameters from "@/components/Parameters.vue";
import RackItem from "@/components/RackItem.vue";

export default {
  name: "home",
  components: {
    Parameters,
    RackItem
  }
};
</script>

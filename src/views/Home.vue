<template>
  <div class="home">
    
    <RackItem row="1" />
    <RackItem row="2" />
    <RackItem row="3" />
    <RackItem row="4" />
    <RackItem row="5" />
    <RackItem row="6" />
    <RackItem row="7" />
    <RackItem row="8" />
    <RackItem row="9" />
    <RackItem row="10" />
    <RackItem row="11" />
    <RackItem row="12" />
    <RackItem row="13" />
    <RackItem row="14" />
    <RackItem row="15" />

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

<template>
<div class="home">
  <div class="columns">
      <div class="column has-text-centered">
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
      <img id="blankimg" src="../../public/img/blank-layout.jpg" alt="" style="display:none;">
      <div class="column hast-text-centered">
        <canvas id="imageCanvas" width="800" height="800" style="border: 1px solid #000000"></canvas>
      </div>
  </div>
</div>
</template>

<script>
window.onload = function() {
  var c = document.getElementById("imageCanvas");
  var ctx = c.getContext("2d");
  var img = document.getElementById("blankimg");
  ctx.drawImage(img, 10, 10);
};

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

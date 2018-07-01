<template>
<div class="home">
  <div class="columns">
      <div class="column has-text-centered">
        
        <rack-item row="1" />
        <rack-item row="2" />
        <rack-item row="3" />
        <rack-item row="4" />
        <rack-item row="5" />
        <rack-item row="6" />
        <rack-item row="7" />
        <rack-item row="8" />
        <rack-item row="9" />
        <rack-item row="10" />
        <rack-item row="11" />
        <rack-item row="12" />
        <rack-item row="13" />
        <rack-item row="14" />
        <rack-item row="15" />

        <parameters />    
        {{ onParametersString }}
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
import { EventBus } from "../EventBus.js";

export default {
  name: "home",
  data() {
    return {
      parametersString: ""
    };
  },
  components: {
    Parameters,
    RackItem
  },
  computed: {
    onParametersString() {
      EventBus.$on("parametersString", parametersString => {
        this.parametersString = parametersString;
      });
    }
  }
};
</script>

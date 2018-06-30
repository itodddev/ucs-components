<template>

    <div class="columns">
        <div class="column has-text-centered">
            
            <!-- Rack RUs Parameter -->

            <div class="field is-horizontal">

                <div class="field-label">
                    <label class="label">Rack RUs:</label>
                </div>

                <div class="field-body">
                    <div class="field is-narrow">
                        <div class="control">
                            <div class="select">
                            <select v-model="ruSelection">
                                <option> 18 </option>
                                <option> 24 </option>
                                <option> 30 </option>
                                <option> 36 </option>
                                <option> 42 </option>
                                <option> 48 </option>
                                <option> 54 </option>
                                <option> 60 </option>
                            </select>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Rack Face Parameter -->

            <div class="field is-horizontal">

                <div class="field-label">
                    <label class="label">Rack Face:</label>
                </div>

                <div class="field-body">
                    <div class="field is-narrow">
                        <div class="control has-text-centered">
                            <label class="radio">
                                <input type="radio" name="face" value="FRONT" v-model="rackFace"> &nbsp;Front
                            </label>
                            <label class="radio">
                                <input type="radio" name="face" value="REAR" v-model="rackFace"> &nbsp;Rear
                            </label>
                            <label class="radio">
                                <input type="radio" name="face" value="PERSPECTIVE" v-model="rackFace"> &nbsp;Perspective
                            </label>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Front Bezel Parameter -->

            <div class="field is-horizontal">

                <div class="field-label">
                    <label class="label">Front Bezel:</label>
                </div>

                <div class="field-body">
                    <div class="field is-narrow">
                        <div class="control has-text-centered">
                            <label class="radio">
                                <input type="radio" name="bezl" value="YES" v-model="frontBezel"> &nbsp;Yes
                            </label>
                            <label class="radio">
                                <input type="radio" name="bezl" value="NO" v-model="frontBezel"> &nbsp;No
                            </label>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Rack Load Parameter -->

            <div class="field is-horizontal">

                <div class="field-label">
                    <label class="label">Rack Load:</label>
                </div>

                <div class="field-body">
                    <div class="field is-narrow">
                        <div class="control has-text-centered">
                            <label class="radio">
                                <input type="radio" name="load" value="HIGH" v-model="rackLoad"> &nbsp;High
                            </label>
                            <label class="radio">
                                <input type="radio" name="load" value="LOW" v-model="rackLoad"> &nbsp;Low
                            </label>
                            <label class="radio">
                                <input type="radio" name="load" value="NO" v-model="rackLoad"> &nbsp;No Rack
                            </label>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Panels Parameter -->

            <div class="field is-horizontal">

                <div class="field-label">
                    <label class="label">Panels:</label>
                </div>
                
                <div class="field-body">
                    <div class="field is-narrow">
                        <div class="control has-text-centered">
                            <label class="radio">
                                <input type="radio" name="pnls" value="YES" v-model="panels"> &nbsp;Yes
                            </label>
                            <label class="radio">
                                <input type="radio" name="pnls" value="NO" v-model="panels"> &nbsp;No
                            </label>              
                        </div>
                    </div>
                </div>
            </div>

            <!-- Format Parameter -->

            <div class="field is-horizontal">

                <div class="field-label">
                    <label class="label">Format:</label>
                </div>
                
                <div class="field-body">
                    <div class="field is-narrow">
                        <div class="control has-text-centered">
                            <label class="radio">
                                <input type="radio" name="format" value="PHOTO" v-model="format"> &nbsp;Photo
                            </label>
                            <label class="radio">
                                <input type="radio" name="format" value="DRAWING" v-model="format"> &nbsp;Drawing
                            </label>
                            <label class="radio">
                                <input type="radio" name="format" value="OVERLAY" v-model="format"> &nbsp;Overlay
                            </label>               
                        </div>
                    </div>
                </div>
            </div>

            <div class="field is-horizontal">

                <div class="field-label">
                    <label class="label">Image Size:</label>
                </div>
                
                <div class="field-body">
                    <div class="field is-narrow">
                        <div class="control has-text-centered">
                            <label class="radio">
                                <input type="radio" name="image-size" value="SMALL" v-model="imageSize"> &nbsp;Small
                            </label>
                            <label class="radio">
                                <input type="radio" name="image-size" value="MEDIUM" v-model="imageSize"> &nbsp;Medium
                            </label>
                            <label class="radio">
                                <input type="radio" name="image-size" value="LARGE" v-model="imageSize"> &nbsp;Large
                            </label>               
                        </div>
                    </div>
                </div>
            </div>
            <br>
            {{ buildParameterString }}
        </div> <!-- End Column -->
    </div> <!-- End Columns -->

</template>

<script>
export default {
  name: "Parameters",
  data() {
    return {
      ruSelection: 42,
      rackFace: "FRONT",
      frontBezel: "YES",
      rackLoad: "HIGH",
      panels: "YES",
      format: "PHOTO",
      imageSize: "MEDIUM",
      paramsStart: "<params ",
      paramsEnd: " />"
    };
  },
  computed: {
    buildRackUnits() {
      return `ru="${this.ruSelection}" extra="0" `;
    },
    buildRackFace() {
      if (this.rackFace === "FRONT") {
        return `face="FRONT" `;
      } else if (this.rackFace === "REAR") {
        return `face="REAR" `;
      } else {
        return `face="PERSPECTIVE" `;
      }
    },
    buildFrontBezel() {
      if (this.frontBezel === "YES") {
        return `bezel="YES" `;
      } else {
        return `bezel="NO" `;
      }
    },
    buildRackLoad() {
      if (this.rackLoad === "HIGH") {
        return `load="HIGH" `;
      } else if (this.rackLoad === "LOW") {
        return `load="LOW" `;
      } else {
        return `load="NO" `;
      }
    },
    buildRackPanels() {
      if (this.panels === "YES") {
        return `panels="YES" `;
      } else {
        return `panels="NO" `;
      }
    },
    buildImageFormat() {
      if (this.format === "PHOTO") {
        return `format="PHOTO" `;
      } else if (this.format === "DRAWING") {
        return `format="DRAWING" `;
      } else {
        return `format="OVERLAY" `;
      }
    },
    buildImageSize() {
      if (this.imageSize === "SMALL") {
        return `size="SMALL" `;
      } else if (this.imageSize === "MEDIUM") {
        return `size="MEDIUM" `;
      } else {
        return `size="LARGE" `;
      }
    },
    buildParameterString() {
      return `${this.paramsStart}${this.buildRackUnits}${this.buildRackFace}${
        this.buildFrontBezel
      }${this.buildRackLoad}${this.buildRackPanels}${this.buildImageFormat}${
        this.buildImageSize
      }${this.paramsEnd}`;
    }
  }
};
</script>

<style scoped>
</style>

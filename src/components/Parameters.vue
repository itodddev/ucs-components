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
                                <input type="radio" name="face" value="FRONT" v-model="rackFace" /><span class="choicePadding">Front</span>
                            </label>
                            <label class="radio">
                                <input type="radio" name="face" value="REAR" v-model="rackFace"/><span class="choicePadding">Rear</span>
                            </label>
                            <label class="radio">
                                <input type="radio" name="face" value="PERSPECTIVE" v-model="rackFace" /><span class="choicePadding">Perspective</span>
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
                                <input type="radio" name="bezl" value="YES" v-model="frontBezel" /><span class="choicePadding">Yes</span>
                            </label>
                            <label class="radio">
                                <input type="radio" name="bezl" value="NO" v-model="frontBezel" /><span class="choicePadding">No</span>
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
                                <input type="radio" name="load" value="HIGH" v-model="rackLoad" /><span class="choicePadding">High</span>
                            </label>
                            <label class="radio">
                                <input type="radio" name="load" value="LOW" v-model="rackLoad" /><span class="choicePadding">Low</span>
                            </label>
                            <label class="radio">
                                <input type="radio" name="load" value="NO" v-model="rackLoad" /><span class="choicePadding">No Rack</span>
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
                                <input type="radio" name="pnls" value="YES" v-model="panels" /><span class="choicePadding">Yes</span>
                            </label>
                            <label class="radio">
                                <input type="radio" name="pnls" value="NO" v-model="panels" /><span class="choicePadding">No</span>
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
                                <input type="radio" name="format" value="PHOTO" v-model="format" /><span class="choicePadding">Photo</span>
                            </label>
                            <label class="radio">
                                <input type="radio" name="format" value="DRAWING" v-model="format" /><span class="choicePadding">Drawing</span>
                            </label>
                            <label class="radio">
                                <input type="radio" name="format" value="OVERLAY" v-model="format" /><span class="choicePadding">Overlay</span>
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
                                <input type="radio" name="image-size" value="SMALL" v-model="imageSize"/><span class="choicePadding">Small</span>
                            </label>
                            <label class="radio">
                                <input type="radio" name="image-size" value="MEDIUM" v-model="imageSize" /><span class="choicePadding">Medium</span>
                            </label>
                            <label class="radio">
                                <input type="radio" name="image-size" value="LARGE" v-model="imageSize" /><span class="choicePadding">Large</span>
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
      if (this.rackFace === "FRONT") return `face="FRONT" `;
      else if (this.rackFace === "REAR") return `face="REAR" `;

      return `face="PERSPECTIVE" `;
    },
    buildFrontBezel() {
      if (this.frontBezel === "YES") return `bezel="YES" `;

      return `bezel="NO" `;
    },
    buildRackLoad() {
      if (this.rackLoad === "HIGH") return `load="HIGH" `;
      else if (this.rackLoad === "LOW") return `load="LOW" `;

      return `load="NO" `;
    },
    buildRackPanels() {
      if (this.panels === "YES") return `panels="YES" `;

      return `panels="NO" `;
    },
    buildImageFormat() {
      if (this.format === "PHOTO") return `format="PHOTO" `;
      else if (this.format === "DRAWING") return `format="DRAWING" `;

      return `format="OVERLAY" `;
    },
    buildImageSize() {
      if (this.imageSize === "SMALL") return `size="SMALL" `;
      else if (this.imageSize === "MEDIUM") return `size="MEDIUM" `;

      return `size="LARGE" `;
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
.choicePadding {
  padding-left: 1em;
  padding-right: 1em;
}
</style>

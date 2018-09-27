<template>
    <div class="quadrilateral" v-bind:style="{ 'border-width': quadrilateralSize, left: quadrilateralLeft }" ></div>
</template>

<script>
export default {
  name: "quadrilateral",
  data() {
    return {
      quadrilateralSize: "0 0",
      quadrilateralLeft: "0"
    }
  },
  mounted() {
    this.defineQuadrilateralSize(window.innerHeight, window.innerWidth)
    //console.log("first width: " + window.innerWidth + " height: " + window.innerHeight)
    this.$nextTick(() => {
      window.addEventListener('resize', () => {
       //console.log("width: " + window.innerWidth + " height: " + window.innerHeight)
       this.defineQuadrilateralSize(window.innerHeight, window.innerWidth)
      });
    })
  },
  methods: {
    defineQuadrilateralSize : function(height, width) {
      this.quadrilateralSize = (height * .5) + "px 0 0 " + width * 1.5 + "px"
      this.quadrilateralLeft = "-" + (width * .5) + "px"
    }
  }
};
</script>

<style scoped>
.quadrilateral {
  width: 0%;
  height: 100%;
  border-style: solid;
  border-color: #006064 transparent;
  position: absolute;
  top: 0;
  z-index: -1;
}
</style>

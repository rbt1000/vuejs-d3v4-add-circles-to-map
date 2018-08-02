<template>
  <div id="holder">
    <div class="mapHolder">
      <mapone
      />
    </div>
  </div>
</template>



<script>
import * as Datamap from "datamaps";
import * as d3 from "d3";

var _ = require('lodash');

//const map = require('d3-components/basic-map-bubble/mapone');


// lets load with vue-resource, but parse with d3
// just because we can
////import * as d3 from 'd3-dsv';


const mapone = require('d3-components/basic-map-bubble/mapone');


export default {
  components: {
    mapone: mapone
  },
  props: {
    projects: Array,
    name: String
  },

  data: function() {
    return {
      width: 0,
      height: 0
    };
  },

};
</script>

<style lang="scss">

.hoverinfo {
  cursor: pointer !important;
}

.project-info {
  position: fixed;
  display: block;
  width: calc(100% - 300px);
  z-index: 999;
  height: 400px;
  bottom: -400px;
  border: none;
  transition: all 0.3s ease;
  background-color: white;
}

.map-container {
  position: absolute;
  left: 0;
  top: 0;
}

.mapone {
  display: inline-flex;
  flex-wrap: nowrap;
  flex-direction: row;
  justify-content: center;
  justify-items: center;
  align-content: center;
  align-items: center;
  overflow: hidden;
}

.project-info.show {
  bottom: 0;
}
</style>

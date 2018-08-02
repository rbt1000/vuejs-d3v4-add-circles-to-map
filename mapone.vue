<template>
  <svg width="1000" height="600"></svg>
</template>



<script>

const d3 = require('d3');
const topojson = require('topojson')

export default {
  mounted: function() {
console.log('mounting-bubble');
    var v = this;
    var svg = d3.select(this.$el);
    var width = +svg.attr('width');
    var height = +svg.attr('height');


//    var projection = d3.geoAlbers();
//    var path = d3.geoPath().projection(projection);

var color = d3.scaleThreshold()
    .domain([10000,100000,500000,1000000,5000000,10000000,50000000,100000000,500000000,1500000000])
    .range(["rgb(247,251,255)", "rgb(222,235,247)", "rgb(198,219,239)", "rgb(158,202,225)", "rgb(107,174,214)", "rgb(66,146,198)","rgb(33,113,181)","rgb(8,81,156)","rgb(8,48,107)","rgb(3,19,43)"]);


  var path = d3.geoPath();

    var projection = d3.geoMercator()
                       .scale(270)
                      .translate( [width , height ]);

    var path = d3.geoPath().projection(projection);



//   d3.json("static/data/world_countries.json", function(error, us) {
  d3.json("static/data/us.json", function(error, us) {
    var g = svg.append('g');
        g
          .selectAll('.state')
          .data(topojson.feature(us, us.objects.usStates).features)
          .enter()
          .append("path")
          .attr("class", "state")
          .attr("d", path)

          .on('mouseover', function(d) {
            v.$emit('stateSelected', d.properties.STATE_ABBR)
      		})
          .on('mouseout', function(d) {
            v.$emit('stateDeselected', d.properties.STATE_ABBR)
          })
      g.attr('transform', 'scale(1.2)')


//      -71 longitude, 42 latitude
            var coordinates = projection([ -71.109734,42.373616]);

       g.append("circle")
               .attr("r", 5)
               .attr("cx", coordinates[0])
               .attr("cy", coordinates[1])
               .style("fill", "red");
    });



  }
  // TODO: fire events
}
</script>

<style>
.state {
  fill: #ccc;
  stroke: #fff;
}
.state:hover {
  fill: steelblue;
}
.mapHolder {
  float:center
}
</style>

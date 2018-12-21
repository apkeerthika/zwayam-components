<template lang="pug">
section.circle-chart(ref="circleChart")
</template>

<script>
export default {
  mounted () {
    d3.json('seed/meetup_history.json').then((history) => {
      d3.select(this.$refs.circleChart)
        .append("svg")
        .attr("viewBox", "0 0 1000 1000")
        .selectAll("circle")
        .data(history)
        .enter()
        .append("circle")
        .attr("cx", function(history){
          return (history.time-1238713200000)/100000000
        })
        .attr("cy", function(history){
          return (history.yes_rsvp_count)
        })
        .attr("r", 6)
        .style("fill", "MediumSeaGreen")
        .style("stroke", "black")
      }
    )
  }
}
</script>


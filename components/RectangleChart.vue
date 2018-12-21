<template lang="pug">
section.my-chart(ref="chart")
</template>


<script>
import * as d3 from 'd3'
import topics from 'static/seed/num_topics.json'

export default {
  data () {
    return {
      topics: topics
    }
  },
  mounted () {
    d3.json('seed/num_topics.json').then((topics) => {
      d3.select(this.$refs.chart)
        .append("ul")
        .selectAll("li")
        .data(topics)
        .enter()
        .append("li")
        .text(
          function (d) {
            var msg = d.count
            msg += " People Specify"
            msg += d.num_topics;
            msg += " topics "
            return msg
          }
        )
      }
    )
    d3.json('seed/num_topics.json').then((data) => {
      d3.select(this.$refs.chart)
        .append("svg")
        .selectAll("rect")
        .data(data)
        .enter()
        .append("rect")
        .attr("y", (d, i) =>{
          return i*24
        })
        .attr("width", (d, i) =>{
          return 11*d.count
        })
        .attr("height", 20)
      }
    )

  }

}
</script>
<style lang="sass" scoped>
section
  .new
    h1
     font-size: 40px
  .data
    .content
      margin: 32px

section.my-chart
  display: flex
  margin-top: 2rem


</style>


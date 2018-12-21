<template lang="pug">
.page
  no-ssr
    rectangle-chart
    circle-chart
</template>


<script>
import * as d3 from 'd3'
import topics from 'static/seed/num_topics.json'

import RectangleChart from '~/components/RectangleChart'
import CircleChart from '~/components/CircleChart'

export default {
  components: {
    RectangleChart,
    CircleChart
  }
}
</script>


<style>

</style>

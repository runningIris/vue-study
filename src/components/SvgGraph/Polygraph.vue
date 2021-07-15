<template>
  <g>
    <polygon :points="points"></polygon>
    <circle cx="100" cy="100"></circle>
    <axis-label
      v-for="(stat, index) in stats"
      :stat="stat"
      :index="index"
      :total="stats.length"
      :key="index"
    ></axis-label>
  </g>
</template>

<script>
import { computed, reactive } from 'vue'
import AxisLabel from './AxisLabel.vue'
import {valueToPoint} from './util'

export default {
  name: 'polygraph',
  components: {AxisLabel},
  props: {
    stats: Array
  },
  setup(props) {
    const points = computed(() => {
      return props.stats.map((stat, i) => {
        const point = valueToPoint(stat.value, i, props.stats.length)
        return point.x + ', ' + point.y
      }).join(' ')
    })

    return {points}
  },
}
</script>

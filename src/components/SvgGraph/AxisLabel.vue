<template>
   <text :x="point.x" :y="point.y">{{stat.label}}</text>
</template>

<script>
import { computed, reactive } from 'vue'
import {valueToPoint} from './util'
export default {
  props: {
    stat: Object,
    index: Number,
    total: Number,
  },
  setup(props) {
    const point = computed(() => {
      return valueToPoint(
        props.stat.value + 10,
        props.index,
        props.total,
      )
    })
    return {point}
  },
}
</script>

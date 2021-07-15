<template>
<div>
  <svg width="200" height="200">
    <polygraph :stats="state.stats"></polygraph>
  </svg>
  <div v-for="stat in state.stats" :key="stat">
    <label>{{ stat.label }}</label>
    <input v-model="stat.value" type="range" min="0" max="100"/>
    <span>{{stat.value}}</span>
    <button @click="remove(stat)">X</button>
  </div>
  <form id="add">
    <input name="newLabel" v-model="state.newLabel"/>
    <button @click="add">Add a Stat</button>
  </form>
  <pre id="raw">{{state.stats}}</pre>
</div>
</template>

<script>
import { computed, reactive, watch } from 'vue'
import Polygraph from './Polygraph.vue'

export default {
  name: 'svg-graph',
  setup() {
    const state = reactive({
      newLabel: '',
      stats:  [
        { label: "A", value: 100 },
        { label: "B", value: 100 },
        { label: "C", value: 100 },
        { label: "D", value: 100 },
        { label: "E", value: 100 },
        { label: "F", value: 100 }
      ]
    })

    const add = (e) => {
      e.preventDefault()
      if (!state.newLabel) return
      state.stats.push({
        label: state.newLabel,
        value: 100
      })
      state.newLabel = ''
    }

    const remove = stat => {
      if (state.stats.length > 3) {
        state.stats.splice(state.stats.indexOf(stat), 1)
      } else {
        alert('Can\'t delete more!')
      }
    }

    return {state, add, remove}
  },
}
</script>

<style>
body {
  font-family: Helvetica Neue, Arial, sans-serif;
}

polygon {
  fill: #42b983;
  opacity: 0.75;
}

circle {
  fill: transparent;
  stroke: #999;
}

text {
  font-family: Helvetica Neue, Arial, sans-serif;
  font-size: 10px;
  fill: #666;
}

label {
  display: inline-block;
  margin-left: 10px;
  width: 20px;
}

#raw {
  position: absolute;
  top: 0;
  left: 300px;
}

</style>
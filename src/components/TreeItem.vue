<template>
  <li style="text-align: left;">
    <div :class="{bold: isFolder}" @click="toggle" @dblclick="makeFolder">
      {{ item.name }}
      <span v-if="isFolder">[{{ state.isOpen ? '-' : '+'}}]</span>
    </div>
    <ul v-show="state.isOpen" v-if="isFolder">
      <tree-item
        class="item"
        v-for="(child, index) in item.children"
        :key="index"
        :item="child"
        @make-folder="$emit('make-folder', $event)"
        @add-item="$emit('add-item', $event)"
      ></tree-item>
      <li class="add" @click="$emit('add-item', item)">+</li>
    </ul>
  </li>
</template>

<script>
import { computed, reactive } from 'vue'

export default {
  name: 'tree-item',
  props: {
    item: Object
  },
  setup(props, context) {
    const state = reactive({isOpen: false})
    const isFolder = computed(() => {
      return !!props.item.children?.length
    })

    const toggle = () => {
      if (isFolder.value) {
        state.isOpen = !state.isOpen
      }
    }

    const makeFolder = () => {
      console.log({isFolder: isFolder.value})
      if (!isFolder.value) {
        context.emit('make-folder', props.item)
        state.isOpen = true
      }
    }

    return {state, isFolder, toggle, makeFolder}
  },
}
</script>

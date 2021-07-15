<template>
<ul>
  <div>(You can double click on an item to turn it into a folder.)</div>
  <tree-item
    class="item"
    :item="state.treeData"
    @make-folder="makeFolder"
    @add-item="addItem"
  ></tree-item>
</ul>
</template>

<script>
import { reactive } from 'vue'
import TreeItem from './TreeItem.vue'

export default {
  name: 'my-tree',
  components: { TreeItem },
  setup(props) {
    const state = reactive({ 
      treeData: {
        name: 'My Tree',
        children: [
          { name: 'hello' },
          { name: 'wat' },
          {
            name: 'child folder',
            children: [
              {
                name: 'child folder',
                children: [{ name: 'hello' }, { name: 'wat' }]
              },
              { name: 'hello' },
              { name: 'wat' },
              {
                name: 'child folder',
                children: [
                  { name: 'hello' },
                  { name: 'wat' }
                ]
              }
            ]
          }
        ]
      }
    })

    const addItem = (item) => {
      item.children.push({
        name: 'new stuff'
      })
    }

    const makeFolder = (item) => {
      console.log('making folders')
      item.children = []
      addItem(item)
    }

    return {
      state,
      makeFolder,
      addItem
    }
  },
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  font-family: Menlo, Consolas, monospace;
  color: #444;
}
.item {
  cursor: pointer;
}
.bold {
  font-weight: bold;
}
ul {
  padding-left: 1em;
  line-height: 1.5em;
  list-style-type: dot;
}
</style>

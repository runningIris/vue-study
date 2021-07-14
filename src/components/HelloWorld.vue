<template>
  <h1>{{ msg }}</h1>
  <div class="h-20"/>
  <div>count is: {{ state.count }}</div>
  <div class="h-20"/>
  <div class="content">
    <div class="btn" @click="subtract">-</div>
    <div class="gap"/>
    <div class="btn" @click="add">+</div>
  </div>
</template>

<script setup>
import { defineProps, reactive } from 'vue'

defineProps({
  msg: String
})

const state = reactive({ count: 0 })

const add = () => state.count++
const subtract = () => state.count--

</script>

<style scoped>
a {
  color: #42b983;
}
.gap {
  width: 20px;
}
.content {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}
.btn {
  width: 60px;
  height: 30px;
  border-radius: 15px;
  background: #42b983;
  color: aliceblue;
  border-color: aliceblue;
  display: flex;
  align-items: center;
  justify-content: center;
  user-select: none;
}
.btn:active {
  opacity: 0.8;
}
.h-20 {
  height: 20px;
}
.h-40 {
  height: 40px;
}
.h-60 {
  height: 60px;
}
</style>

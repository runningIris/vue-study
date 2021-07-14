<template>
  <h1>{{ msg }}</h1>
</template>

<script setup>
import { defineProps, reactive } from 'vue'

defineProps({
  msg: String
})

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

<script setup>
import { reactive,ref } from 'vue';
const counter = reactive({
  count: 0
})
const message = ref("hello world")

const titleClass = ref('title')

const count = ref(0)

function increment(){
  count.value++
}

function increment2(){
  counter.count++
}

</script>

<template>
  <div>
    <h1 :class="titleClass">TEST</h1>
    <h1>{{ message }}</h1>
    <button @click="increment2">change</button>
    <h1>count is : {{ counter.count }}</h1>
    <button @click="increment">change</button>
    <h1>count = {{ count }}</h1>
  </div>

</template>

<style scoped>
.title{
  color:red
}
</style>

<script setup>
import { reactive,ref } from 'vue';
import cats from './components/cats.vue';

const message = ref("hello world")

const titleClass = ref('title')

const counter = reactive({
  count: 0
})

const x = ref(0)

const text = ref('kucing imut')

function increase(){
  counter.count++
}

function increment(){
  x.value++
}

function incrementBy(number) {
  x.value += number; // Update count.value directly
}

const awesome = ref(true)

function toggleAwesome(){
  awesome.value = !awesome.value
}

</script>

<template>
  <div>
    <h1 :class="titleClass">TEST</h1>
    <h1>{{ message }}</h1>
    <button @click="increase">change</button>
    <h1>count is : {{ counter.count }}</h1>
    <button @click="increment">add</button>
    <button @click="incrementBy(2)">add by 2</button>
    <h1>count = {{ x }}</h1>

    <!-- <input :value="text" @input="onInput">
    function onInput(e) {
      // a v-on handler receives the native DOM event
      // as the argument.
      text.value = e.target.value
    } -->

    <!-- v-model is shorthand for above function -->
    <!-- v-model automatically syncs the <input>'s value with the bound state, so we no longer need to use an event handler for that. -->
    <input type="text" v-model="text" placeholder="type here">
    <p>result : {{ text }}</p>

    <button @click="toggleAwesome">toggle</button>
    <h1 v-if="awesome">awesome dude</h1>
    <h1 v-else>not awesome</h1>
    <cats/>
  </div>

</template>

<style scoped>
.title{
  color:red
}
</style>

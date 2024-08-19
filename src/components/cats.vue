<script setup>
import { ref } from 'vue';

let id = 0

const newCat = ref('')
const cats = ref([
    { id: id++, name: 'Bob' },
    { id: id++, name: 'Brown' },
    { id: id++, name: 'White' },
])

function addCat() {
    cats.value.push({ id: id++, name: newCat.value })
    newCat.value = ''
}

function removeCat(id) {
    cats.value = cats.value.filter((t) => t.id !== id)
}

</script>
<template>
    <div>
        <form @submit.prevent="addCat">
            <input v-model="newCat" />
            <button>add cat</button>
        </form>
        <ul>
            <li v-for="cat in cats" :key="cat.id">
                {{ cat.name }}
                <button @click="removeCat(cat.id)">remove</button>
            </li>
        </ul>

    </div>
</template>

<style lang="">

</style>
<script setup>
import { computed, ref } from 'vue';

let id = 0

const newCat = ref('')
const cats = ref([
    { id: id++, name: 'Bob', gone: false },
    { id: id++, name: 'Brown', gone: true },
    { id: id++, name: 'White', gone: false },
])

const hideGoneCats = ref(false)

function addCat() {
    cats.value.push({ id: id++, name: newCat.value })
    newCat.value = ''
}

function removeCat(id) {
    cats.value = cats.value.filter((t) => t.id !== id)
}

const filteredCats = computed(() => {
    return hideGoneCats.value ? cats.value.filter((t) => !t.gone) : cats.value
})

</script>
<template>
    <div>
        <form @submit.prevent="addCat">
            <input v-model="newCat" placeholder="add a new cat" />
            <button>add cat</button>
        </form>
        <ul>
            <!-- <li v-for="cat in cats" :key="cat.id"> -->
            <li v-for="cat in filteredCats" :key="cat.id">
                {{ cat.name }}
                <button @click="removeCat(cat.id)">remove</button>

                {{ cat.gone ? "cat is gone" : "still alive" }}
                <input type="checkbox" v-model="cat.gone"> is cat gone?
            </li>
        </ul>

        <button @click="hideGoneCats = !hideGoneCats">{{ hideGoneCats ? "Show all" : "Hide Gone cats" }}</button>

    </div>
</template>

<style lang="">

</style>
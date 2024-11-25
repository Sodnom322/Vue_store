<script setup>
import Header from './components/Header.vue'
import Drawer from './components/Drawer.vue'
import CartList from './components/CartList.vue'
import { onMounted, ref, watch, reactive } from 'vue'
import axios from 'axios'

const items = ref([])

const filters = reactive({
  sortBy: '',
  searchQuery: '',
})

const onChangeSelect = (event) => {
  filters.sortBy = event.target.value
}

onMounted(async () => {
  try {
    const { data } = await axios.get('https://144d4d58d53fbf73.mokky.dev/items')
    items.value = data
  } catch (error) {
    console.log(error)
  }
})

watch(filters, async () => {
  try {
    const { data } = await axios.get(
      'https://144d4d58d53fbf73.mokky.dev/items?sortBy=' + filters.sortBy,
    )
    items.value = data
  } catch (error) {
    console.log(error)
  }
})
</script>

<template>
  <!--  <Drawer /> -->
  <div class="w-4/5 m-auto bg-white rounded-xl shadow-xl mt-14">
    <Header />
    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-8">Все кроссвоки</h2>
        <div class="flex gap-4">
          <select @change="onChangeSelect" class="py-2 px-3 border rounded-md outline-none">
            <option value="name">По названию</option>
            <option value="price">По цене(дешевые)</option>
            <option value="-price">По цене(дорогие)</option>
          </select>

          <div class="relative">
            <img class="absolute left-3 top-3" src="/search.svg" alt="" />
            <input
              class="border rounded-md py-2 pl-12 pr-4 outline-none focus:border-gray-400"
              placeholder="Поиск..."
            />
          </div>
        </div>
      </div>
      <div class="mt-10">
        <CartList :items="items" />
      </div>
    </div>
  </div>
</template>
